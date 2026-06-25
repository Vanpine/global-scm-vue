<template>
  <div class="bg-[#F5F5F7] min-h-screen text-slate-900 selection:bg-blue-200">

    <!-- ===== Hero ===== -->
    <section class="relative h-screen min-h-[700px] flex items-center justify-center overflow-hidden bg-black">
      <video
        :src="heroVideo"
        autoplay
        muted
        loop
        playsinline
        class="absolute inset-0 w-full h-full object-cover z-0 opacity-70"
      />
      <div class="absolute inset-0 bg-gradient-to-b from-black/40 via-black/20 to-black/80 z-10" />

      <div class="relative z-20 text-center px-6 max-w-4xl mx-auto mt-20">
        <h1
          v-motion
          :initial="{ opacity: 0, y: 30 }"
          :enter="{ opacity: 1, y: 0, transition: { duration: 800, ease: [0.16, 1, 0.3, 1] } }"
          class="text-6xl md:text-8xl font-semibold tracking-tight text-white mb-6"
        >
          全球供应链<span class="text-transparent bg-clip-text bg-gradient-to-r from-blue-400 to-emerald-300">大平台</span>
        </h1>
        <p
          v-motion
          :initial="{ opacity: 0, y: 30 }"
          :enter="{ opacity: 1, y: 0, transition: { duration: 800, delay: 100, ease: [0.16, 1, 0.3, 1] } }"
          class="text-xl md:text-3xl text-white/90 font-light mb-10 tracking-wide"
        >
          赋能地方资源 · 连接全球市场
        </p>

        <div
          v-motion
          :initial="{ opacity: 0, y: 30 }"
          :enter="{ opacity: 1, y: 0, transition: { duration: 800, delay: 200, ease: [0.16, 1, 0.3, 1] } }"
          class="flex flex-wrap items-center justify-center gap-6 text-white/80 font-medium mb-12"
        >
          <span class="flex items-center gap-2"><TrendingDown class="w-5 h-5" /> 降本增效</span>
          <span class="hidden md:inline-block w-1.5 h-1.5 rounded-full bg-white/30" />
          <span class="flex items-center gap-2"><ShieldCheck class="w-5 h-5" /> 抗风险</span>
          <span class="hidden md:inline-block w-1.5 h-1.5 rounded-full bg-white/30" />
          <span class="flex items-center gap-2"><Cpu class="w-5 h-5" /> AI 赋能</span>
        </div>

        <div
          v-motion
          :initial="{ opacity: 0, y: 30 }"
          :enter="{ opacity: 1, y: 0, transition: { duration: 800, delay: 300, ease: [0.16, 1, 0.3, 1] } }"
          class="flex flex-col sm:flex-row items-center justify-center gap-4"
        >
          <RouterLink to="/join" class="w-full sm:w-auto px-8 py-4 rounded-full bg-white text-slate-950 font-medium hover:scale-105 transition-all duration-300 shadow-[0_0_40px_rgba(255,255,255,0.2)]">
            申请加入 &rarr;
          </RouterLink>
          <RouterLink to="/smart-procurement" class="w-full sm:w-auto px-8 py-4 rounded-full bg-white/10 border border-white/20 text-white font-medium hover:bg-white/20 backdrop-blur-md transition-all duration-300">
            了解产品 &rarr;
          </RouterLink>
        </div>
      </div>
    </section>

    <!-- ===== Polycrisis ===== -->
    <section class="py-32 px-6 lg:px-8 max-w-7xl mx-auto">
      <div class="text-center mb-20">
        <div class="text-4xl md:text-6xl font-bold tracking-widest text-slate-200 mb-4 uppercase">POLYCRISIS</div>
        <h2 class="text-2xl md:text-3xl font-medium text-slate-500">供应链的多重危机</h2>
      </div>

      <TransitionGroup name="crisis" tag="div" class="grid grid-cols-1 lg:grid-cols-3 gap-8">
        <article
          v-for="(crisis, idx) in visibleCrises"
          :key="crisis.title"
          v-motion
          :initial="{ opacity: 0, scale: 0.95 }"
          :enter="{ opacity: 1, scale: 1, transition: { duration: 500, delay: idx * 50 } }"
          class="bg-white rounded-[2rem] overflow-hidden shadow-[0_8px_30px_rgb(0,0,0,0.04)] hover:shadow-xl transition-shadow group flex flex-col"
        >
          <div class="h-64 overflow-hidden relative">
            <ImageWithFallback
              :src="crisis.img"
              :alt="crisis.title"
              class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-700"
            />
          </div>
          <div class="p-8 flex-1 flex flex-col">
            <h3 class="text-xl font-semibold text-slate-900 mb-2">{{ crisis.title }}</h3>
            <p class="text-slate-500 font-medium text-sm mb-6 pb-6 border-b border-slate-100">{{ crisis.sub }}</p>
            <ul class="space-y-3 mt-auto">
              <li v-for="(bullet, i) in crisis.bullets" :key="i" class="flex items-start text-sm text-slate-600 leading-relaxed">
                <span class="text-blue-500 mr-2 mt-1">&bull;</span>
                {{ bullet }}
              </li>
            </ul>
          </div>
        </article>
      </TransitionGroup>

      <div v-if="!showAllCrises" class="mt-16 text-center">
        <button
          @click="showAllCrises = true"
          class="inline-flex items-center gap-2 px-6 py-3 rounded-full bg-white border border-slate-200 text-slate-600 hover:bg-slate-50 transition-colors shadow-sm"
        >
          查看全部危机 <ChevronDown class="w-4 h-4" />
        </button>
      </div>
    </section>

    <!-- ===== AI Banner ===== -->
    <section class="relative h-screen min-h-[600px] flex flex-col justify-center overflow-hidden bg-slate-900">
      <div class="absolute inset-0 z-0">
        <ImageWithFallback
          src="https://images.unsplash.com/photo-1451187580459-43490279c0fa?auto=format&fit=crop&w=2000&q=80"
          alt="AI Supply Chain"
          class="w-full h-full object-cover opacity-30 mix-blend-luminosity scale-105 animate-[pulse_20s_ease-in-out_infinite_alternate]"
        />
        <div class="absolute inset-0 bg-gradient-to-t from-slate-950 via-slate-900/60 to-transparent"></div>
      </div>
      <div class="relative z-10 px-6 max-w-4xl mx-auto text-center">
        <h2 class="text-5xl md:text-7xl font-semibold text-white mb-8 tracking-tight">AI 重塑全球供应链</h2>
        <p class="text-xl md:text-2xl text-slate-300 font-light leading-relaxed mb-12">
          将全球供应链从被动、割裂、脆弱的系统，<br class="hidden md:block"/>转变为可预测、可重构、具备韧性的智能网络。
        </p>
        <RouterLink to="/smart-procurement" class="inline-flex items-center gap-2 px-10 py-5 rounded-full bg-blue-600 text-white font-medium hover:bg-blue-500 transition-colors shadow-lg shadow-blue-500/30 text-lg hover:scale-105 duration-300">
          探索解决方案 <ArrowRight class="w-5 h-5" />
        </RouterLink>
      </div>
    </section>

    <!-- ===== Pillars ===== -->
    <section class="py-20 px-6 max-w-7xl mx-auto mb-16">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-12 divide-y md:divide-y-0 md:divide-x divide-slate-200">
        <div
          v-for="(pillar, idx) in PILLARS"
          :key="idx"
          v-motion
          :initial="{ opacity: 0, y: 30 }"
          :visible="{ opacity: 1, y: 0, transition: { duration: 600, delay: idx * 100 } }"
          :visible-once="true"
          class="pt-12 md:pt-0 md:px-12 flex flex-col items-center text-center group"
        >
          <div class="w-16 h-16 rounded-2xl bg-white shadow-sm border border-slate-100 flex items-center justify-center mb-6 text-slate-900 group-hover:scale-110 group-hover:bg-blue-50 group-hover:text-blue-600 transition-all duration-300">
            <component :is="pillar.icon" class="w-8 h-8" />
          </div>
          <h3 class="text-2xl font-semibold mb-4 text-slate-900">{{ pillar.title }}</h3>
          <p class="text-slate-500 leading-relaxed font-light">{{ pillar.desc }}</p>
        </div>
      </div>
    </section>

    <!-- ===== Capabilities Carousel ===== -->
    <section class="py-32 bg-slate-50 overflow-hidden">
      <div class="max-w-[90rem] mx-auto px-6 lg:px-8">
        <div class="text-center mb-20">
          <div class="text-4xl md:text-5xl font-bold tracking-widest text-slate-200 mb-4 uppercase">CAPABILITIES</div>
          <h2 class="text-2xl md:text-3xl font-medium text-slate-500">五大核心能力</h2>
        </div>

        <div class="relative">
          <div
            ref="carouselRef"
            class="flex gap-6 overflow-x-auto snap-x snap-mandatory hide-scrollbar pb-12 pt-4 px-4 -mx-4"
            style="scrollbar-width: none; ms-overflow-style: none;"
          >
            <div
              v-for="(cap, idx) in CAPABILITIES"
              :key="idx"
              class="snap-center shrink-0 w-[85vw] md:w-[400px] h-[500px] relative rounded-[2rem] overflow-hidden group cursor-pointer"
            >
              <RouterLink :to="cap.link" class="block w-full h-full">
                <ImageWithFallback
                  :src="cap.img"
                  :alt="cap.title"
                  class="absolute inset-0 w-full h-full object-cover group-hover:scale-105 transition-transform duration-700 ease-out"
                />
                <div class="absolute inset-0 bg-gradient-to-t from-slate-900/90 via-slate-900/40 to-transparent transition-opacity group-hover:from-slate-900"></div>
                <div class="absolute bottom-0 left-0 p-8 w-full text-white transform translate-y-4 group-hover:translate-y-0 transition-transform duration-300">
                  <h3 class="text-3xl font-semibold mb-4">{{ cap.title }}</h3>
                  <ul class="space-y-3 opacity-80 group-hover:opacity-100 transition-opacity">
                    <li v-for="(bullet, i) in cap.bullets" :key="i" class="flex items-start text-sm font-light">
                      <span class="text-blue-400 mr-2 mt-1">&bull;</span>
                      {{ bullet }}
                    </li>
                  </ul>
                </div>
              </RouterLink>
            </div>
          </div>

          <div class="flex items-center justify-center gap-4 mt-8">
            <button
              @click="scrollLeft"
              class="w-12 h-12 rounded-full bg-white border border-slate-200 flex items-center justify-center text-slate-600 hover:bg-slate-50 transition-colors shadow-sm"
            >
              <ChevronLeft class="w-5 h-5" />
            </button>
            <button
              @click="scrollRight"
              class="w-12 h-12 rounded-full bg-white border border-slate-200 flex items-center justify-center text-slate-600 hover:bg-slate-50 transition-colors shadow-sm"
            >
              <ChevronRight class="w-5 h-5" />
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== Stats ===== -->
    <section class="py-20 px-6 max-w-7xl mx-auto">
      <div class="grid grid-cols-2 md:grid-cols-4 gap-12 md:gap-6 text-center divide-x divide-slate-200/50">
        <div
          v-for="(stat, idx) in STATS"
          :key="idx"
          v-motion
          :initial="{ opacity: 0, scale: 0.9 }"
          :visible="{ opacity: 1, scale: 1, transition: { duration: 500, delay: idx * 100 } }"
          :visible-once="true"
        >
          <div class="text-4xl md:text-5xl font-semibold text-slate-900 mb-2">{{ stat.num }}</div>
          <div class="text-sm font-medium text-slate-500 uppercase tracking-wider">{{ stat.label }}</div>
        </div>
      </div>
    </section>

    <!-- ===== Risk Map ===== -->
    <RiskDashboard />

    <!-- ===== CTA ===== -->
    <section class="py-32 px-6 text-center">
      <div
        v-motion
        :initial="{ opacity: 0, y: 30 }"
        :visible="{ opacity: 1, y: 0, transition: { duration: 600 } }"
        :visible-once="true"
        class="max-w-3xl mx-auto"
      >
        <h2 class="text-4xl md:text-5xl font-semibold text-slate-900 mb-6 tracking-tight">加入全球供应链大平台</h2>
        <p class="text-xl text-slate-500 font-light mb-10">赋能地方资源 · 连接全球市场</p>
        <RouterLink to="/join" class="inline-flex items-center gap-2 px-10 py-5 rounded-full bg-slate-900 text-white font-medium text-lg hover:bg-slate-800 hover:scale-105 active:scale-95 transition-all duration-300 shadow-xl shadow-slate-900/20">
          申请加入 <ArrowRight class="w-5 h-5" />
        </RouterLink>
      </div>
    </section>

  </div>
</template>

<script setup>
import { ref, computed, markRaw } from 'vue'
import { RouterLink } from 'vue-router'
import {
  ArrowRight, TrendingDown, ShieldCheck, ChevronDown,
  ChevronLeft, ChevronRight, Cpu, Zap
} from 'lucide-vue-next'
import heroVideo from '@/assets/vedio.mp4'
import ImageWithFallback from '@/components/ImageWithFallback.vue'
import RiskDashboard from '@/components/home/RiskDashboard.vue'

const CRISIS_DATA = [
  {
    title: "地缘冲突与航运中断",
    sub: "战争与对峙，切断全球关键航道",
    bullets: [
      "红海危机：胡塞武装袭击商船，主力班轮绕行好望角，每航次增加 10-14 天",
      "霍尔木兹海峡：全球 20% 石油运输咽喉，美伊对峙持续升级",
      "俄乌冲突：黑海航运保险费用飙升，全球谷物出口通道受阻"
    ],
    img: "https://images.unsplash.com/photo-1605745341112-85968b19335b?auto=format&fit=crop&w=1400&q=85"
  },
  {
    title: "极端天气与自然灾害",
    sub: "一场洪水、一次飓风，就能掐断全球关键节点",
    bullets: [
      "泰国洪水（2011）：淹没全球 25% 硬盘产能，价格暴涨 180%，持续两年才恢复",
      "美国德州暴雪（2021）：三星/恩智浦/英飞凌三大芯片厂停产，汽车产业再遭重击",
      "全球极端天气频率较 1980 年代增加超 3 倍，每年造成供应链损失超 2,000 亿美元"
    ],
    img: "https://images.unsplash.com/photo-1470071459604-3b5ec3a7fe05?auto=format&fit=crop&w=1400&q=85"
  },
  {
    title: "供应中断与单点依赖",
    sub: "一根钉子折了，整条产线就得停",
    bullets: [
      "日本 311 地震（2011）：全球汽车 MCU 芯片断供，丰田/本田停产数月，波及全球",
      "美国东海岸港口罢工（2024）：3 天损失超 15 亿美元，36 个港口同时瘫痪",
      "台积电一家占全球先进芯片产能 90%，地震、缺水随时可能触发全球断供"
    ],
    img: "https://images.unsplash.com/photo-1586528116311-ad8dd3c8310d?auto=format&fit=crop&w=1400&q=85"
  },
  {
    title: "关税与贸易壁垒",
    sub: "关税一日三变，到岸成本随时失控",
    bullets: [
      "美国对华 301 关税覆盖约 3,700 亿美元商品，平均税率达 19.3%",
      "欧盟 CBAM 碳边境机制 2026 年正式征收，钢铁铝制品首当其冲",
      "芯片出口管制持续扩大：从光刻机延伸至半导体设备与 EDA 软件"
    ],
    img: "https://images.unsplash.com/photo-1681505531034-8d67054e07f6?auto=format&fit=crop&w=1400&q=85"
  },
  {
    title: "港口拥堵与物流瘫痪",
    sub: "一个堵点，全球货物在海面漂着回不了家",
    bullets: [
      "苏伊士运河\"长赐号\"搁浅（2021）：全球贸易每日损失 96 亿美元，422 艘船滞留",
      "美国西海岸港口罢工：洛杉矶/长滩港积压超 100 艘，货值超 240 亿美元",
      "巴拿马运河因干旱限行：日通行量从 36 艘骤降至 22 艘，运价应声暴涨"
    ],
    img: "https://images.unsplash.com/photo-1494412651409-8963ce7935a7?auto=format&fit=crop&w=1400&q=85"
  },
  {
    title: "需求剧烈波动",
    sub: "终端一点微动，上游就是一场海啸",
    bullets: [
      "全球芯片短缺（2020-2022）：汽车产业损失超 2,100 亿美元，交货周期长达 52 周",
      "疫情期间\"牛鞭效应\"：零售商恐慌囤货→制造商过度扩产→全链路库存崩盘",
      "集装箱运价单周暴涨 300%（2024）：需求预测完全失准，现货舱位一票难求"
    ],
    img: "https://images.unsplash.com/photo-1460925895917-afdab827c52f?auto=format&fit=crop&w=1400&q=85"
  }
]

const PILLARS = [
  { title: "降本", desc: "基于 AI 的预测与优化，减少库存积压与物流成本，提高资源配置效率。", icon: markRaw(TrendingDown) },
  { title: "增效", desc: "自动化流程与统一协作机制，加快决策与执行速度，降低运营误差。", icon: markRaw(Zap) },
  { title: "抗风险", desc: "前瞻性风险识别与情景模拟，支持在冲击发生前进行结构性调整，保障供应连续性。", icon: markRaw(ShieldCheck) }
]

const CAPABILITIES = [
  {
    title: "智能撮合",
    bullets: ["AI 多维度解析采购需求与供应商产能", "双向匹配并附评分依据，告别盲目撒网", "供需双方在同一平台互相发现、直接对接"],
    img: "https://images.unsplash.com/photo-1553877522-43269d4ea984?auto=format&fit=crop&w=800&q=80",
    link: "/smart-procurement"
  },
  {
    title: "安全合规",
    bullets: ["制裁名单实时比对，一键筛查交易对手风险", "多层股权穿透，追溯实际控制人与关联方", "诉讼与合规记录自动汇总，分钟级生成尽调报告"],
    img: "https://images.unsplash.com/photo-1450101499163-c8848c66ca85?auto=format&fit=crop&w=800&q=80",
    link: "/smart-procurement"
  },
  {
    title: "可信交付",
    bullets: ["合同、物流、结算全链路透明化追踪", "关键节点自动存证，纠纷有据可查", "智能履约监控，降低交付延期与违约风险"],
    img: "https://images.unsplash.com/photo-1586528116311-ad8dd3c8310d?auto=format&fit=crop&w=800&q=80",
    link: "/trusted-delivery"
  },
  {
    title: "全局风控",
    bullets: ["地缘冲突、关税政策、极端天气 24h 全球扫描", "风险事件自动关联到你的供应商与航线", "在冲击到来前预警，同步推送替代方案"],
    img: "https://images.unsplash.com/photo-1551288049-bebda4e38f71?auto=format&fit=crop&w=800&q=80",
    link: "/smart-procurement"
  },
  {
    title: "数据智脑",
    bullets: ["全平台交易与风控数据实时汇聚、量化分析", "每一次决策都有数据支撑，告别拍脑袋", "知识沉淀在平台而非个人脑中，经验可复用"],
    img: "https://images.unsplash.com/photo-1460925895917-afdab827c52f?auto=format&fit=crop&w=800&q=80",
    link: "/smart-procurement"
  }
]

const STATS = [
  { num: "1,300+", label: "全球专业合伙人" },
  { num: "50+", label: "服务国家和地区" },
  { num: "17", label: "专业服务年限" },
  { num: "10,000+", label: "成功案例" }
]

const showAllCrises = ref(false)
const carouselRef = ref(null)

const visibleCrises = computed(() => showAllCrises.value ? CRISIS_DATA : CRISIS_DATA.slice(0, 3))

function scrollLeft() {
  carouselRef.value?.scrollBy({ left: -400, behavior: 'smooth' })
}

function scrollRight() {
  carouselRef.value?.scrollBy({ left: 400, behavior: 'smooth' })
}
</script>

<style scoped>
.crisis-enter-active,
.crisis-leave-active {
  transition: all 0.5s ease;
}
.crisis-enter-from,
.crisis-leave-to {
  opacity: 0;
  transform: scale(0.95);
}
.crisis-move {
  transition: transform 0.5s ease;
}
</style>
