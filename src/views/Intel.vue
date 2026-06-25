<template>
  <div class="bg-[#F5F5F7] min-h-screen text-slate-900 selection:bg-blue-200">

    <!-- ===== Hero ===== -->
    <section class="relative h-screen min-h-[700px] flex items-center justify-center overflow-hidden bg-black">
      <ImageWithFallback
        src="https://images.unsplash.com/photo-1450101499163-c8848c66ca85?auto=format&fit=crop&w=1920&q=85"
        alt="Intel Hero" class="absolute inset-0 w-full h-full object-cover opacity-70" />
      <div class="absolute inset-0 bg-gradient-to-b from-black/40 via-black/20 to-black/80 z-10" />

      <div class="relative z-20 text-center px-6 max-w-4xl mx-auto mt-20">
        <h1 v-motion :initial="{ opacity: 0, y: 30 }"
          :enter="{ opacity: 1, y: 0, transition: { duration: 800, ease: [0.16, 1, 0.3, 1] } }"
          class="text-6xl md:text-8xl font-semibold tracking-tight text-white mb-6">
          全球情报<span class="text-transparent bg-clip-text bg-gradient-to-r from-blue-400 to-emerald-300">要闻</span>
        </h1>
        <p v-motion :initial="{ opacity: 0, y: 30 }"
          :enter="{ opacity: 1, y: 0, transition: { duration: 800, delay: 100, ease: [0.16, 1, 0.3, 1] } }"
          class="text-xl md:text-3xl text-white/90 font-light mb-10 tracking-wide">
          实时追踪政策、关税、地缘与物流动态
        </p>

        <div v-motion :initial="{ opacity: 0, y: 30 }"
          :enter="{ opacity: 1, y: 0, transition: { duration: 800, delay: 200, ease: [0.16, 1, 0.3, 1] } }"
          class="flex flex-wrap items-center justify-center gap-6 text-white/80 font-medium mb-12">
          <span class="flex items-center gap-2">
            <FileText class="w-5 h-5" /> 政策速递
          </span>
          <span class="hidden md:inline-block w-1.5 h-1.5 rounded-full bg-white/30" />
          <span class="flex items-center gap-2">
            <Globe class="w-5 h-5" /> 地缘观察
          </span>
          <span class="hidden md:inline-block w-1.5 h-1.5 rounded-full bg-white/30" />
          <span class="flex items-center gap-2">
            <Truck class="w-5 h-5" /> 物流快报
          </span>
        </div>
      </div>
    </section>

    <!-- ===== News Groups ===== -->
    <section class="py-24 px-6 lg:px-8 max-w-7xl mx-auto">
      <div v-for="group in NEWS_GROUPS" :key="group.category" v-motion :initial="{ opacity: 0, y: 40 }"
        :visible="{ opacity: 1, y: 0, transition: { duration: 600, ease: [0.16, 1, 0.3, 1] } }" :visible-once="true"
        class="mb-20 last:mb-0">
        <h3 class="flex items-center gap-3 text-2xl font-semibold text-slate-900 mb-8 pb-4 border-b border-slate-200">
          <component :is="group.icon" class="w-6 h-6 text-blue-600" />
          {{ group.category }}
        </h3>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          <article v-for="(item, idx) in group.items" :key="idx"
            class="group bg-white rounded-[2rem] overflow-hidden shadow-[0_8px_30px_rgba(0,0,0,0.04)] hover:shadow-xl transition-all duration-300 cursor-pointer flex flex-col"
            @click="item.href ? $router.push(item.href) : null">
            <div class="h-52 overflow-hidden relative">
              <ImageWithFallback :src="item.img" :alt="item.title"
                class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-700" />
              <span
                :class="['absolute top-4 left-4 px-3 py-1.5 rounded-full text-xs font-semibold backdrop-blur-md', item.catStyle]">
                {{ item.catLabel }}
              </span>
            </div>

            <div class="p-6 flex-1 flex flex-col">
              <h4
                class="text-lg font-semibold text-slate-900 mb-3 group-hover:text-blue-600 transition-colors leading-snug">
                {{ item.title }}
              </h4>
              <p class="text-sm text-slate-500 leading-relaxed mb-5 flex-1">
                {{ item.summary }}
              </p>
              <div class="flex items-center justify-between text-xs text-slate-400 pt-4 border-t border-slate-100">
                <span>{{ item.meta }}</span>
                <span class="text-blue-600 font-medium group-hover:translate-x-1 transition-transform duration-300">阅读详情
                  &rarr;</span>
              </div>
            </div>
          </article>
        </div>
      </div>

      <p class="text-center text-sm text-slate-400 mt-8">
        * 全球情报要闻基于 2026 年公开报道整理，用于展示版式与解读视角；点击任意卡片查看完整内容。
      </p>
    </section>

    <!-- ===== Leaflet Map ===== -->
    <section class="py-16 px-6 lg:px-8 max-w-7xl mx-auto">
      <div class="text-center mb-12">
        <div class="text-sm font-bold tracking-widest text-slate-400 mb-4 uppercase">INTERACTIVE MAP · 区域态势</div>
        <h2 class="text-3xl md:text-4xl font-semibold text-slate-900 mb-4">可缩放的全球风险地图</h2>
        <p class="text-lg text-slate-500 font-light max-w-2xl mx-auto">
          放大任意区域，查看港口、航线与高危事件的分布细节。滚轮缩放、拖动平移、点击标记查看详情。
        </p>
      </div>

      <div
        class="leaflet-wrap relative rounded-[2.5rem] overflow-hidden shadow-[0_20px_60px_rgba(0,0,0,0.1)] border border-slate-200">
        <div id="riskLeaflet" class="w-full h-[500px] md:h-[600px]" />
        <button class="map-theme-btn" @click="toggleMapTheme" :title="darkMode ? '切换日间模式' : '切换夜间模式'">{{ darkMode ? '☀️'
          : '🌙' }}</button>
        <div
          class="absolute bottom-6 left-6 flex gap-4 text-xs font-medium bg-white/90 backdrop-blur-md px-4 py-2 rounded-full border border-slate-200 shadow-sm z-[1000]">
          <span class="flex items-center gap-2"><span class="w-2 h-2 rounded-full bg-red-500"></span> 高危</span>
          <span class="flex items-center gap-2"><span class="w-2 h-2 rounded-full bg-amber-500"></span> 关注</span>
          <span class="flex items-center gap-2"><span class="w-2 h-2 rounded-full bg-emerald-500"></span> 正常</span>
        </div>
      </div>
      <p class="text-center text-sm text-slate-400 mt-6">
        * 供应链风险点为演示数据；全球地震为 USGS 实时数据（纯前端直连，每 60 秒自动刷新）。
      </p>
    </section>

  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted, markRaw } from 'vue'
import { Globe, FileText, Truck, Zap, Ship } from 'lucide-vue-next'
import ImageWithFallback from '@/components/ImageWithFallback.vue'
import L from 'leaflet'
import 'leaflet/dist/leaflet.css'

// ── News Data ──────────────────────────────────────────

const NEWS_GROUPS = [
  {
    category: '地缘冲突',
    icon: markRaw(Globe),
    items: [
      {
        title: '黑海出口走廊再遇袭，俄无人机击中三艘外籍商船',
        summary: '乌克兰粮食与金属外运走廊安全告急，袭击或推高全球粮价，非洲、中东、亚洲进口国首当其冲。',
        meta: 'Modern Diplomacy · 5 小时前',
        img: 'https://images.unsplash.com/photo-1494412651409-8963ce7935a7?auto=format&fit=crop&w=900&q=75',
        catLabel: '地缘冲突',
        catStyle: 'bg-red-500/90 text-white',
      },
      {
        title: '乌克兰"物流封锁"战：年内击中 15 座俄炼油厂',
        summary: '1–5 月乌方打击 15 座炼油厂，约四成俄炼油产能离线，克里米亚燃油配给，俄已限制成品油出口。',
        meta: 'Kyiv Independent · 8 小时前',
        img: 'https://images.unsplash.com/photo-1586528116311-ad8dd3c8310d?auto=format&fit=crop&w=900&q=75',
        catLabel: '地缘冲突',
        catStyle: 'bg-red-500/90 text-white',
      },
      {
        title: '战争险重定价：中东冲突推高海运保险，承保人撤出海湾',
        summary: '多家 P&I 俱乐部 72 小时内取消海湾战争险承保，西方船舶保费升至船价数个百分点，成本沿全链路传导。',
        meta: 'Insurance Business · 今日',
        img: 'https://images.unsplash.com/photo-1454165804606-c3d57bc86b40?auto=format&fit=crop&w=900&q=75',
        catLabel: '地缘冲突',
        catStyle: 'bg-red-500/90 text-white',
      },
    ],
  },
  {
    category: '交通物流',
    icon: markRaw(Truck),
    items: [
      {
        title: '红海危机延续：主力班轮默认绕行好望角',
        summary: 'CMA CGM、马士基等已把好望角作为亚欧默认航线，单程增加 10–14 天、燃油上升约 30%，每箱附加费 500–1,500 美元。',
        meta: 'Reuters · 海运 · 今日',
        img: 'https://images.unsplash.com/photo-1605745341112-85968b19335b?auto=format&fit=crop&w=900&q=75',
        catLabel: '交通物流',
        catStyle: 'bg-blue-500/90 text-white',
      },
      {
        title: '东欧陆运口岸受阻，中欧班列绕行加价',
        summary: '过境俄罗斯—白俄罗斯—波兰的主通道持续受地缘冲突影响，陆运时效与成本上升，企业转向多枢纽与备选路由。',
        meta: 'GMK Center · 1 天前',
        img: 'https://images.unsplash.com/photo-1566576721346-d4a3b4eaeb55?auto=format&fit=crop&w=900&q=75',
        catLabel: '交通物流',
        catStyle: 'bg-blue-500/90 text-white',
      },
      {
        title: '巴拿马运河暂不限航，2027 干旱风险笼罩',
        summary: '运河管理局称年内维持 38 班/日、不限航；但 El Niño 强度上升，2027 旱季或重演 2023 减班至 22 班/日的局面。',
        meta: 'Tico Times · 1 天前',
        img: 'https://images.unsplash.com/photo-1605745341112-85968b19335b?auto=format&fit=crop&w=900&q=75',
        catLabel: '交通物流',
        catStyle: 'bg-blue-500/90 text-white',
      },
    ],
  },
  {
    category: '能源与环境',
    icon: markRaw(Zap),
    items: [
      {
        title: '霍尔木兹海峡近乎关闭，全球两成石油咽喉中断',
        summary: '自 2 月底美以空袭伊朗以来，海峡日通行量从约 95 艘骤降至个位数，布伦特原油逼近 95 美元，战争险一度暴涨逾十倍。',
        meta: 'Bloomberg · 能源 · 2 小时前',
        img: 'https://images.unsplash.com/photo-1578575437130-527eed3abbec?auto=format&fit=crop&w=900&q=75',
        catLabel: '能源与环境',
        catStyle: 'bg-amber-500/90 text-white',
      },
      {
        title: '欧盟 CBAM 碳边境机制进入正式期，进口商须清缴碳证',
        summary: '自 1 月 1 日起，钢铁、水泥、铝、化肥、电力、氢进口需具备授权申报人资格并清缴碳证；Q1 碳价 75.36 欧元/吨。',
        meta: 'European Commission · 2 天前',
        img: 'https://images.unsplash.com/photo-1494412651409-8963ce7935a7?auto=format&fit=crop&w=900&q=75',
        catLabel: '能源与环境',
        catStyle: 'bg-amber-500/90 text-white',
      },
    ],
  },
  {
    category: '贸易政策',
    icon: markRaw(FileText),
    items: [
      {
        title: '美国 Section 232 金属关税扩围至铜，最高 50%',
        summary: '4 月 6 日起钢、铝、铜及衍生品按全额征税：主金属 50%、衍生品 25%、部分工业设备 15%，重塑采购成本与产地选择。',
        meta: 'Baker Tilly · 今日',
        img: 'https://images.unsplash.com/photo-1450101499163-c8848c66ca85?auto=format&fit=crop&w=900&q=75',
        catLabel: '贸易政策',
        catStyle: 'bg-purple-500/90 text-white',
      },
      {
        title: '美国 10% 普遍关税陷法律拉锯，7 月 24 日到期前仍在征收',
        summary: '国际贸易法院裁定 Section 122 关税违法，但联邦巡回法院发出临时中止令，CBP 继续照常征收，退税并不自动。',
        meta: 'Flexport · 今日',
        img: 'https://images.unsplash.com/photo-1517048676732-d65bc937f952?auto=format&fit=crop&w=900&q=75',
        catLabel: '贸易政策',
        catStyle: 'bg-purple-500/90 text-white',
      },
      {
        title: '中国稀土管制悬顶：11 月 10 日大限将至',
        summary: '2025 年 4 月七类中重稀土许可制仍生效；10 月扩大管制暂停至 11 月 10 日，若重启，域外条款将波及含中国稀土的海外制成品。',
        meta: 'TechTimes · IEA · 3 小时前',
        img: 'https://images.unsplash.com/photo-1586528116311-ad8dd3c8310d?auto=format&fit=crop&w=900&q=75',
        catLabel: '贸易政策',
        catStyle: 'bg-purple-500/90 text-white',
      },
      {
        title: '美对华 AI 芯片管制收紧，明确适用海外子公司',
        summary: '商务部澄清：对总部在华企业，其海外子公司同样受 AI 芯片出口限制约束；H200 按个案审查，Blackwell 仍禁运。',
        meta: 'Al Jazeera · BIS · 1 天前',
        img: 'https://images.unsplash.com/photo-1518770660439-4636190af475?auto=format&fit=crop&w=900&q=75',
        catLabel: '贸易政策',
        catStyle: 'bg-purple-500/90 text-white',
      },
      {
        title: '美国对进口药品加征关税，最高 100%',
        summary: '对专利药品及原料药按 20%–100% 分档征税，7 月 31 日 / 9 月 29 日分批生效，英国药品按 10%，重塑医药供应链布局。',
        meta: 'Baker Tilly · 1 天前',
        img: 'https://images.unsplash.com/photo-1584308666744-24d5c474f2ae?auto=format&fit=crop&w=900&q=75',
        catLabel: '贸易政策',
        catStyle: 'bg-purple-500/90 text-white',
      },
      {
        title: 'USMCA 联合复审临近，7 月 1 日成关键节点',
        summary: '依第 34.7 条，协定生效六年后启动联合复审；若三国未共同确认，将进入十年"日落"机制，牵动北美供应链与近岸布局。',
        meta: 'Deluair · 2 天前',
        img: 'https://images.unsplash.com/photo-1605902711622-cfb43c4437b5?auto=format&fit=crop&w=900&q=75',
        catLabel: '贸易政策',
        catStyle: 'bg-purple-500/90 text-white',
      },
    ],
  },
]

// ═══════════════════════════════════════════════════════
// 2D Leaflet 地图 — GDACS 灾害 + USGS 地震（实时）
// ═══════════════════════════════════════════════════════

const GDACS_TYPE_ZH = { EQ: '地震', FL: '洪水', TC: '热带气旋', VO: '火山喷发', DR: '干旱', WF: '野火', TS: '海啸' }
const USGS_URL = 'https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/2.5_day.geojson'
const TILE_DARK = 'https://{s}.basemaps.cartocdn.com/dark_all/{z}/{x}/{y}{r}.png'
const TILE_LIGHT = 'https://{s}.basemaps.cartocdn.com/light_all/{z}/{x}/{y}{r}.png'
const LEVEL_COLOR = { high: '#ff3b30', watch: '#ff9500', normal: '#34c759' }
const LEVEL_RADIUS = { high: 9, watch: 7, normal: 5 }

const mapContainer = ref(null)
const darkMode = ref(false)

let mapInstance = null
let disasterLayer = null
let quakeLayer = null
let tileLayer = null
let mapTimer = null

function gdacsLevel(alertLevel) {
  if (alertLevel === 'Red') return 'high'
  if (alertLevel === 'Orange') return 'watch'
  return 'normal'
}

function magLevel(m) {
  return m >= 6 ? 'high' : (m >= 4.5 ? 'watch' : 'normal')
}

function makeCircleMarker(lat, lng, level, popupHtml) {
  const color = LEVEL_COLOR[level] || LEVEL_COLOR.normal
  const classes = level !== 'normal' ? 'pulse-marker pulse-' + level : ''
  return L.circleMarker([lat, lng], {
    radius: LEVEL_RADIUS[level] || 5,
    fillColor: color,
    color: '#fff',
    weight: 1.5,
    fillOpacity: 0.85,
    className: classes,
  }).bindTooltip(popupHtml, { direction: 'top', offset: [0, -8], opacity: 0.92, sticky: true })
}

async function fetchGDACS() {
  try {
    const res = await fetch('/gdacs/xml/rss.xml')
    const xmlText = await res.text()
    const parser = new DOMParser()
    const doc = parser.parseFromString(xmlText, 'text/xml')
    const geoNS = 'http://www.w3.org/2003/01/geo/wgs84_pos#'
    const gdacsNS = 'http://www.gdacs.org'

    const markers = []
    doc.querySelectorAll('item').forEach(item => {
      const eventType = item.getElementsByTagNameNS(gdacsNS, 'eventtype')[0]?.textContent
      if (!eventType || eventType === 'EQ') return

      const pointEl = item.getElementsByTagNameNS(geoNS, 'Point')[0]
      const latEl = pointEl?.getElementsByTagNameNS(geoNS, 'lat')[0]
      const lngEl = pointEl?.getElementsByTagNameNS(geoNS, 'long')[0]
      const lat = parseFloat(latEl?.textContent)
      const lng = parseFloat(lngEl?.textContent)
      if (isNaN(lat) || isNaN(lng) || lat < -90 || lat > 90 || lng < -180 || lng > 180) return

      const alertLevel = item.getElementsByTagNameNS(gdacsNS, 'alertlevel')[0]?.textContent || 'Green'
      const title = item.querySelector('title')?.textContent || ''
      const country = item.getElementsByTagNameNS(gdacsNS, 'country')[0]?.textContent || ''
      const typeZh = GDACS_TYPE_ZH[eventType] || eventType
      const level = gdacsLevel(alertLevel)
      const popup = `<b>${typeZh}</b><br>${title}<br><small>${country} · ${alertLevel}</small>`

      markers.push(makeCircleMarker(lat, lng, level, popup))
    })
    return markers
  } catch (e) {
    console.warn('GDACS 灾害数据获取失败', e)
    return []
  }
}

async function fetchUSGS() {
  try {
    const res = await fetch(USGS_URL)
    const geo = await res.json()
    return (geo.features || []).slice(0, 60).map(f => {
      const [lng, lat] = f.geometry.coordinates
      const mag = f.properties.mag || 0
      const place = f.properties.place || ''
      const level = magLevel(mag)
      const popup = `<b>M${mag.toFixed(1)} 地震</b><br>${place}`
      return makeCircleMarker(lat, lng, level, popup)
    })
  } catch (e) {
    console.warn('USGS 地震数据获取失败', e)
    return []
  }
}

async function refreshMap() {
  if (!mapInstance) return
  const [disasters, quakes] = await Promise.all([fetchGDACS(), fetchUSGS()])
  if (disasterLayer) mapInstance.removeLayer(disasterLayer)
  if (quakeLayer) mapInstance.removeLayer(quakeLayer)
  disasterLayer = L.layerGroup(disasters).addTo(mapInstance)
  quakeLayer = L.layerGroup(quakes).addTo(mapInstance)
}

function toggleMapTheme() {
  if (!tileLayer || !mapInstance) return
  darkMode.value = !darkMode.value
  mapInstance.removeLayer(tileLayer)
  tileLayer = L.tileLayer(darkMode.value ? TILE_DARK : TILE_LIGHT, { maxZoom: 18, noWrap: false }).addTo(mapInstance)
}

function initMap() {
  const el = document.getElementById('riskLeaflet')
  if (!el) return
  mapInstance = L.map(el, {
    center: [20, 0], zoom: 2, minZoom: 2, maxZoom: 12,
    maxBounds: [[-85, -180], [85, 180]],
    maxBoundsViscosity: 0.8,
    zoomControl: true, attributionControl: false,
    scrollWheelZoom: true, worldCopyJump: true,
  })
  tileLayer = L.tileLayer(darkMode.value ? TILE_DARK : TILE_LIGHT, { maxZoom: 18, noWrap: false }).addTo(mapInstance)
  refreshMap()
  mapTimer = setInterval(refreshMap, 60000)
}

function destroyMap() {
  clearInterval(mapTimer)
  if (mapInstance) { mapInstance.remove(); mapInstance = null }
}

onMounted(() => {
  initMap()
})

onUnmounted(() => {
  destroyMap()
})
</script>

<style scoped>
.map-theme-btn {
  position: absolute;
  top: 16px;
  right: 16px;
  z-index: 1000;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: 1px solid rgba(0, 0, 0, 0.1);
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(8px);
  font-size: 18px;
  cursor: pointer;
  display: grid;
  place-items: center;
  transition: all 0.2s;
}

.map-theme-btn:hover {
  background: #fff;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

/* Pulse markers for high/watch risk on 2D map */
:deep(.pulse-marker) {
  animation: pulse-ring 2s ease-out infinite;
}

:deep(.pulse-high) {
  animation-duration: 1.4s;
}

:deep(.pulse-watch) {
  animation-duration: 2.2s;
}

@keyframes pulse-ring {
  0% {
    r: 5;
    opacity: 0.9;
  }

  100% {
    r: 18;
    opacity: 0;
  }
}
</style>
