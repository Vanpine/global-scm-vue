<script setup>
/**
 * RiskDashboard.vue — 全球风险地图控制塔（数据中枢）
 *
 * 职责：
 *   1. 从 GDACS 拉取实时灾害数据（洪水/气旋/野火/干旱/火山）
 *   2. 从 USGS 拉取实时地震数据（纯前端直连）
 *   3. 通过 provide() 将数据下发给子组件 Globe3D 和 RiskFeed
 *
 * 子组件关系：
 *   RiskDashboard (provide 数据)
 *     ├── Globe3D   — 3D 地球可视化
 *     └── RiskFeed  — 右侧地震快讯面板
 */

import { ref, computed, onMounted, onUnmounted, provide } from 'vue'
import Globe3D from './Globe3D.vue'
import RiskFeed from './RiskFeed.vue'

// ═══════════════════════════════════════════════════════
// 一、GDACS 全球灾害数据
// ═══════════════════════════════════════════════════════

const GDACS_TYPE_ZH = {
  EQ: '地震', FL: '洪水', TC: '热带气旋',
  VO: '火山喷发', DR: '干旱', WF: '野火', TS: '海啸',
}

function gdacsLevel(alertLevel) {
  if (alertLevel === 'Red')    return 'high'
  if (alertLevel === 'Orange') return 'watch'
  return 'normal'
}

const disasterPoints = ref([])

// ═══════════════════════════════════════════════════════
// 二、全球主要贸易航线
// ═══════════════════════════════════════════════════════

const ARCS = [
  { startLat: 31.23, startLng: 121.47, endLat: 33.75, endLng: -118.19, name: '上海→洛杉矶' },
  { startLat: 31.23, startLng: 121.47, endLat: 53.55, endLng: 9.99,    name: '上海→汉堡' },
  { startLat: 1.29,  startLng: 103.85, endLat: 51.95, endLng: 4.4,     name: '新加坡→鹿特丹' },
  { startLat: 31.23, startLng: 121.47, endLat: 1.29,  endLng: 103.85,  name: '上海→新加坡' },
  { startLat: 25.27, startLng: 55.30,  endLat: 53.55, endLng: 9.99,    name: '迪拜→汉堡' },
  { startLat: 35.10, startLng: 129.03, endLat: 33.75, endLng: -118.19, name: '釜山→洛杉矶' },
  { startLat: 29.75, startLng: -95.35, endLat: 51.95, endLng: 4.4,     name: '休斯顿→鹿特丹' },
]

const HUB_PORTS = [
  { lat: 31.23, lng: 121.47, zh: '上海港', en: 'Shanghai' },
  { lat: 33.75, lng: -118.19, zh: '洛杉矶港', en: 'Los Angeles' },
  { lat: 53.55, lng: 9.99, zh: '汉堡港', en: 'Hamburg' },
  { lat: 1.29, lng: 103.85, zh: '新加坡港', en: 'Singapore' },
  { lat: 51.95, lng: 4.4, zh: '鹿特丹港', en: 'Rotterdam' },
  { lat: 25.27, lng: 55.30, zh: '迪拜港', en: 'Dubai' },
  { lat: 35.10, lng: 129.03, zh: '釜山港', en: 'Busan' },
  { lat: 29.75, lng: -95.35, zh: '休斯顿港', en: 'Houston' },
]

function haversineKm(lat1, lng1, lat2, lng2) {
  const R = 6371
  const dLat = (lat2 - lat1) * Math.PI / 180
  const dLng = (lng2 - lng1) * Math.PI / 180
  const a = Math.sin(dLat / 2) ** 2 +
    Math.cos(lat1 * Math.PI / 180) * Math.cos(lat2 * Math.PI / 180) *
    Math.sin(dLng / 2) ** 2
  return R * 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1 - a))
}

function sampleGreatCircle(lat1, lng1, lat2, lng2, n = 5) {
  const points = []
  for (let i = 0; i <= n; i++) {
    const t = i / n
    const φ1 = lat1 * Math.PI / 180, λ1 = lng1 * Math.PI / 180
    const φ2 = lat2 * Math.PI / 180, λ2 = lng2 * Math.PI / 180
    const x1 = Math.cos(φ1) * Math.cos(λ1), y1 = Math.cos(φ1) * Math.sin(λ1), z1 = Math.sin(φ1)
    const x2 = Math.cos(φ2) * Math.cos(λ2), y2 = Math.cos(φ2) * Math.sin(λ2), z2 = Math.sin(φ2)
    const dot = x1 * x2 + y1 * y2 + z1 * z2
    const omega = Math.acos(Math.min(1, Math.max(-1, dot)))
    if (Math.abs(omega) < 1e-10) { points.push({ lat: lat1, lng: lng1 }); continue }
    const sinO = Math.sin(omega)
    const a = Math.sin((1 - t) * omega) / sinO
    const b = Math.sin(t * omega) / sinO
    const x = a * x1 + b * x2, y = a * y1 + b * y2, z = a * z1 + b * z2
    points.push({
      lat: Math.atan2(z, Math.sqrt(x * x + y * y)) * 180 / Math.PI,
      lng: Math.atan2(y, x) * 180 / Math.PI,
    })
  }
  return points
}

const AFFECT_KM = 1200

function arcAffectedLevel(arc, disasters) {
  const samples = sampleGreatCircle(arc.startLat, arc.startLng, arc.endLat, arc.endLng, 5)
  let worst = 'normal'
  for (const d of disasters) {
    for (const s of samples) {
      if (haversineKm(s.lat, s.lng, d.lat, d.lng) < AFFECT_KM) {
        if (d.level === 'high') return 'high'
        if (d.level === 'watch') worst = 'watch'
      }
    }
  }
  return worst
}

const dynamicArcs = computed(() => {
  const disasters = disasterPoints.value
  return ARCS.map(arc => {
    const level = disasters.length ? arcAffectedLevel(arc, disasters) : 'normal'
    if (level === 'high')   return { ...arc, color: ['#ff3b30', '#ff3b30'] }
    if (level === 'watch')  return { ...arc, color: ['#ff9500', '#ff9500'] }
    return { ...arc, color: ['#2997ff', '#5e5ce6'] }
  })
})

// ═══════════════════════════════════════════════════════
// 三、USGS 实时地震数据
// ═══════════════════════════════════════════════════════

const USGS_URL = 'https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/2.5_day.geojson'

const quakePoints = ref([])
const lastUpdated = ref(null)
const liveOK      = ref(false)

let refreshTimer = null

function magLevel(m) {
  return m >= 6 ? 'high' : (m >= 4.5 ? 'watch' : 'normal')
}

async function fetchQuakes() {
  try {
    const res = await fetch(USGS_URL)
    const geo = await res.json()
    const feats = (geo.features || [])
      .sort((a, b) => b.properties.time - a.properties.time)

    quakePoints.value = feats.slice(0, 80).map(f => {
      const c   = f.geometry.coordinates
      const mag = f.properties.mag || 0
      return {
        lat: c[1],
        lng: c[0],
        level: magLevel(mag),
        type: 'quake',
        mag,
        time: f.properties.time,
        place: f.properties.place || 'Unknown',
        url: f.properties.url || '',
        zh: 'M' + mag.toFixed(1) + ' 地震 · ' + (f.properties.place || ''),
        en: 'M' + mag.toFixed(1) + ' quake · ' + (f.properties.place || '')
      }
    })

    liveOK.value = true
    lastUpdated.value = Date.now()
  } catch {
    liveOK.value = false
  }
}

async function fetchGDACS() {
  try {
    const res = await fetch('/gdacs/xml/rss.xml')
    const xmlText = await res.text()
    const parser = new DOMParser()
    const doc = parser.parseFromString(xmlText, 'text/xml')

    const geoNS   = 'http://www.w3.org/2003/01/geo/wgs84_pos#'
    const gdacsNS = 'http://www.gdacs.org'

    const disasters = []
    doc.querySelectorAll('item').forEach(item => {
      const eventType = item.getElementsByTagNameNS(gdacsNS, 'eventtype')[0]?.textContent
      if (!eventType || eventType === 'EQ') return

      let lat, lng
      const georssEl = item.getElementsByTagNameNS('http://www.georss.org/georss', 'point')[0]
      if (georssEl?.textContent) {
        const parts = georssEl.textContent.trim().split(/\s+/)
        lat = parseFloat(parts[0])
        lng = parseFloat(parts[1])
      }
      if (isNaN(lat) || isNaN(lng)) {
        lat = parseFloat(item.getElementsByTagNameNS(geoNS, 'lat')[0]?.textContent)
        lng = parseFloat(item.getElementsByTagNameNS(geoNS, 'long')[0]?.textContent)
      }

      if (isNaN(lat) || isNaN(lng) || lat < -90 || lat > 90 || lng < -180 || lng > 180) return

      const alertLevel = item.getElementsByTagNameNS(gdacsNS, 'alertlevel')[0]?.textContent || 'Green'
      const title = item.querySelector('title')?.textContent || ''
      const link  = item.querySelector('link')?.textContent || ''
      const country  = item.getElementsByTagNameNS(gdacsNS, 'country')[0]?.textContent || ''
      const fromDate = item.getElementsByTagNameNS(gdacsNS, 'fromdate')[0]?.textContent || ''
      const severityEl = item.getElementsByTagNameNS(gdacsNS, 'severity')[0]
      const severity   = severityEl?.textContent || ''

      const typeZh = GDACS_TYPE_ZH[eventType] || eventType
      const time   = new Date(fromDate).getTime()

      disasters.push({
        lat, lng,
        level: gdacsLevel(alertLevel),
        type: eventType,
        typeZh,
        zh: typeZh + ' · ' + country + (severity ? ' · ' + severity : ''),
        en: eventType + ' · ' + country + ' · ' + title,
        url: link,
        time: isNaN(time) ? 0 : time,
        severity,
      })
    })

    disasters.sort((a, b) => b.time - a.time)
    disasterPoints.value = disasters.slice(0, 50)
  } catch (e) {
    console.warn('GDACS 灾害数据获取失败', e)
  }
}

// ═══════════════════════════════════════════════════════
// 四、依赖注入
// ═══════════════════════════════════════════════════════
provide('riskPoints', disasterPoints)
provide('riskArcs', dynamicArcs)
provide('hubPorts', HUB_PORTS)
provide('quakePoints', quakePoints)
provide('liveOK', liveOK)
provide('lastUpdated', lastUpdated)

// ═══════════════════════════════════════════════════════
// 五、生命周期
// ═══════════════════════════════════════════════════════
onMounted(async () => {
  await Promise.all([fetchQuakes(), fetchGDACS()])
  refreshTimer = setInterval(() => {
    fetchQuakes()
    fetchGDACS()
  }, 60000)
})

onUnmounted(() => {
  clearInterval(refreshTimer)
})
</script>

<template>
  <section class="py-32 bg-slate-950 text-white relative" id="risk">
    <div class="w-[85%] mx-auto px-6 lg:px-8">
      <div class="text-center mb-16">
        <div class="text-sm font-bold tracking-widest text-slate-500 mb-4 uppercase">CONTROL TOWER</div>
        <h2 class="text-3xl md:text-4xl font-semibold mb-4 text-white">全球风险地图 · 实时控制塔</h2>
        <p class="text-slate-400 max-w-2xl mx-auto font-light">影响你供应商的外部事件，一个屏幕看清。实时监测地缘冲突、政策变化、港口状态与极端天气。</p>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-start">
        <div class="lg:col-span-8 bg-slate-900 rounded-[2.5rem] border border-slate-800 h-[500px] md:h-[600px] relative overflow-hidden">
          <div id="globeViz" class="w-full h-full"></div>
          <Globe3D />
          <div class="absolute bottom-6 left-6 flex gap-4 text-xs font-medium bg-slate-950/80 backdrop-blur-md px-4 py-2 rounded-full border border-slate-800 z-10">
            <span class="flex items-center gap-2"><span class="w-2 h-2 rounded-full bg-red-500"></span> 高危</span>
            <span class="flex items-center gap-2"><span class="w-2 h-2 rounded-full bg-amber-500"></span> 关注</span>
            <span class="flex items-center gap-2"><span class="w-2 h-2 rounded-full bg-emerald-500"></span> 正常</span>
          </div>
          <div class="absolute bottom-6 right-6 text-xs text-slate-500 z-10">拖动旋转 · 滚轮缩放 · 悬停查看详情</div>
        </div>

        <div class="lg:col-span-4 h-[500px] md:h-[600px]">
          <RiskFeed />
        </div>
      </div>

      <p class="text-center text-sm text-slate-500 mt-6">
        * 供应链风险点为演示数据；全球地震为 USGS 实时数据（纯前端直连，每 60 秒自动刷新）。正式版接入 GDELT、气象、港口与制裁等更多实时源。
      </p>
    </div>
  </section>
</template>
