<template>
  <div class="bg-white">
    <!-- Hero -->
    <section class="relative h-screen min-h-[800px] w-full flex items-center justify-center overflow-hidden">
      <div class="absolute inset-0 z-0">
        <img
          :src="IMAGES.hero"
          alt="Global Logistics Network"
          class="w-full h-full object-cover object-center scale-105 animate-[pulse_20s_ease-in-out_infinite_alternate]"
        />
        <div class="absolute inset-0 bg-gradient-to-b from-[#0a0d16]/80 via-[#0a0d16]/60 to-[#0a0d16]"></div>
      </div>

      <div class="relative z-10 max-w-5xl mx-auto px-6 text-center mt-20">
        <h1
          v-motion
          :initial="{ opacity: 0, y: 30 }"
          :enter="{ opacity: 1, y: 0, transition: { duration: 800, delay: 100, ease: [0.16, 1, 0.3, 1] } }"
          class="text-5xl md:text-7xl lg:text-8xl font-semibold tracking-tight text-white leading-[1.1] mb-8"
        >
          全球物流<span class="text-transparent bg-clip-text bg-gradient-to-r from-blue-400 to-cyan-300">控制塔</span>
        </h1>

        <p
          v-motion
          :initial="{ opacity: 0, y: 30 }"
          :enter="{ opacity: 1, y: 0, transition: { duration: 800, delay: 200, ease: [0.16, 1, 0.3, 1] } }"
          class="text-xl md:text-2xl text-slate-300 font-light max-w-3xl mx-auto leading-relaxed"
        >
          全链路数字孪生预见异常，化被动等待为<span class="text-white font-medium">主动掌控</span>
        </p>
      </div>

      <div
        v-motion
        :initial="{ opacity: 0 }"
        :enter="{ opacity: 1, transition: { delay: 1000, duration: 1000 } }"
        class="absolute bottom-10 left-1/2 -translate-x-1/2 flex flex-col items-center gap-2 text-white/50"
      >
        <span class="text-xs uppercase tracking-widest">Scroll to explore</span>
        <ChevronDown class="w-5 h-5 animate-bounce" />
      </div>
    </section>

    <!-- KPI Stats -->
    <section class="relative z-20 -mt-24 max-w-7xl mx-auto px-6 lg:px-8">
      <div
        v-motion
        :initial="{ opacity: 0, y: 40 }"
        :visible="{ opacity: 1, y: 0, transition: { duration: 800, ease: [0.16, 1, 0.3, 1] } }"
        :visible-once="true"
        class="bg-white/10 backdrop-blur-2xl border border-white/20 rounded-[2rem] p-8 md:p-12 shadow-[0_30px_60px_-15px_rgba(0,0,0,0.3)] grid grid-cols-2 md:grid-cols-4 gap-8 divide-x divide-white/10"
      >
        <div v-for="(stat, idx) in STATS" :key="idx" :class="['text-center px-4', idx % 2 === 0 ? 'border-l-0 md:border-l' : '', idx === 0 ? 'border-l-0' : '']">
          <div class="text-4xl md:text-6xl font-light text-white mb-2 tracking-tight">{{ stat.value }}</div>
          <div class="text-slate-300 font-medium text-sm md:text-base tracking-wide mb-1">{{ stat.label }}</div>
          <div class="text-slate-500 text-xs uppercase tracking-wider">{{ stat.sub }}</div>
        </div>
      </div>
    </section>

    <!-- Capabilities Zig-Zag -->
    <section class="py-32 overflow-hidden bg-[#fafafa]">
      <div class="max-w-7xl mx-auto px-6 lg:px-8 space-y-32">
        <div
          v-for="cap in CAPABILITIES"
          :key="cap.id"
          v-motion
          :initial="{ opacity: 0, y: 50 }"
          :visible="{ opacity: 1, y: 0, transition: { duration: 800, ease: [0.16, 1, 0.3, 1] } }"
          :visible-once="true"
          :class="['flex flex-col lg:flex-row items-center gap-12 lg:gap-24', cap.reverse ? 'lg:flex-row-reverse' : '']"
        >
          <div class="flex-1 space-y-8 w-full">
            <div class="flex items-center space-x-4">
              <div class="text-sm font-bold text-slate-400 tracking-widest uppercase">Capability</div>
              <div class="h-px bg-slate-300 flex-1 max-w-[100px]"></div>
              <div class="text-4xl font-light text-slate-200">{{ cap.id }}</div>
            </div>

            <div>
              <h2 class="text-3xl md:text-5xl font-semibold text-slate-900 tracking-tight mb-4">{{ cap.title }}</h2>
              <div class="inline-flex items-center px-3 py-1 rounded-md bg-slate-100 text-slate-600 font-medium text-sm tracking-wide">
                侧重：{{ cap.tagline }}
              </div>
            </div>

            <p class="text-lg md:text-xl text-slate-500 font-light leading-relaxed">{{ cap.description }}</p>

            <div class="pt-4 flex items-center gap-4 text-blue-600 font-medium hover:text-blue-700 cursor-pointer group w-fit transition-colors">
              探索技术细节
              <ArrowRight class="w-5 h-5 group-hover:translate-x-1 transition-transform" />
            </div>
          </div>

          <div class="flex-1 w-full">
            <div class="relative rounded-[2.5rem] overflow-hidden aspect-[4/3] bg-slate-200 shadow-2xl shadow-slate-900/10 group transform-gpu">
              <img
                :src="cap.image"
                :alt="cap.title"
                class="object-cover w-full h-full transform transition-transform duration-1000 group-hover:scale-105"
              />
              <div :class="['absolute bottom-6 md:bottom-10 bg-white/90 backdrop-blur-xl p-4 md:p-6 rounded-2xl shadow-xl flex items-center gap-4 max-w-[280px]', cap.reverse ? 'left-6 md:left-10' : 'right-6 md:right-10']">
                <div class="bg-white p-3 rounded-xl shadow-sm">
                  <component :is="cap.icon" class="w-8 h-8" :class="cap.iconColor" />
                </div>
                <div>
                  <div class="text-xs font-bold text-slate-400 uppercase tracking-wider mb-1">Status</div>
                  <div class="text-sm font-semibold text-slate-900 leading-tight">{{ cap.title }}模块已激活</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Black Box → White Box -->
    <section class="relative py-32 bg-[#0a0d16] text-white overflow-hidden">
      <div class="absolute top-0 right-0 w-[800px] h-[800px] bg-blue-600/10 blur-[150px] rounded-full pointer-events-none mix-blend-screen"></div>
      <div class="absolute bottom-0 left-0 w-[600px] h-[600px] bg-cyan-600/10 blur-[120px] rounded-full pointer-events-none mix-blend-screen"></div>

      <div class="max-w-6xl mx-auto px-6 relative z-10">
        <div class="text-center max-w-5xl mx-auto mb-20 space-y-12">
          <div class="w-20 h-20 mx-auto bg-gradient-to-tr from-blue-600 to-cyan-400 rounded-3xl flex items-center justify-center shadow-[0_0_50px_rgba(56,189,248,0.3)] mb-8 transform -rotate-3 hover:rotate-0 transition-transform duration-500">
            <ShieldCheck class="w-10 h-10 text-white" />
          </div>

          <h2 class="text-3xl md:text-4xl font-light leading-[1.5] text-slate-300">
            可信交付的重点不是<span class="text-blue-400 font-medium px-2">运输执行</span>本身，而是全链路的可见性、风险的前置感知与合规的提前把关。
          </h2>

          <div class="pt-10 pb-4 relative">
            <div class="absolute inset-0 bg-gradient-to-r from-blue-500/0 via-blue-500/10 to-cyan-500/0 blur-2xl"></div>
            <h3 class="relative text-4xl md:text-6xl lg:text-7xl font-bold tracking-tight text-white mb-6 leading-[1.3] md:leading-[1.2]">
              让交付从<span class="text-slate-600 line-through decoration-red-500/60 decoration-4 px-3 relative">黑盒<div class="absolute inset-0 bg-red-500/10 blur-md -z-10"></div></span>变<span class="text-transparent bg-clip-text bg-gradient-to-r from-cyan-300 to-blue-500 px-3 drop-shadow-[0_0_20px_rgba(34,211,238,0.4)]">白盒</span>
            </h3>
            <p class="text-2xl md:text-3xl text-slate-400 font-light tracking-wide">
              从事后被动补救，走向<span class="text-white font-medium border-b-2 border-cyan-400 pb-1">事前主动管控</span>
            </p>
          </div>
        </div>

        <!-- Comparison Panels -->
        <div class="max-w-5xl mx-auto mb-24 relative">
          <div class="absolute inset-0 bg-gradient-to-r from-slate-800 to-blue-900/50 rounded-[2.5rem] blur-xl opacity-60"></div>

          <div class="relative bg-[#111524] border border-white/10 rounded-[2.5rem] p-2 md:p-3 backdrop-blur-2xl flex flex-col md:flex-row gap-3">
            <!-- Black Box -->
            <div class="flex-1 bg-black/50 rounded-[2rem] p-8 md:p-12 border border-white/5 relative overflow-hidden group">
              <div class="text-slate-500 text-sm font-bold uppercase tracking-widest mb-6 flex items-center gap-2">
                <EyeOff class="w-5 h-5" />
                Traditional / 过去
              </div>
              <ul class="space-y-8">
                <li class="flex gap-4">
                  <div class="mt-1 bg-red-500/10 text-red-400 p-1.5 rounded-full h-fit"><X class="w-4 h-4" /></div>
                  <div>
                    <div class="text-slate-300 font-medium mb-1">节点盲区大，轨迹靠人催</div>
                    <div class="text-slate-500 text-sm leading-relaxed">货物离开工厂后即进入盲区，ETA（预计到达时间）准确率不足 60%，客户反复催问进度导致沟通成本极高。</div>
                  </div>
                </li>
                <li class="flex gap-4">
                  <div class="mt-1 bg-red-500/10 text-red-400 p-1.5 rounded-full h-fit"><X class="w-4 h-4" /></div>
                  <div>
                    <div class="text-slate-300 font-medium mb-1">异常发现滞后，产生高昂附加费</div>
                    <div class="text-slate-500 text-sm leading-relaxed">塞港、甩柜、暴风雪等异常发生数日后才获知，经常导致高昂的滞港费（Demurrage）与空箱费（Detention）。</div>
                  </div>
                </li>
                <li class="flex gap-4">
                  <div class="mt-1 bg-red-500/10 text-red-400 p-1.5 rounded-full h-fit"><X class="w-4 h-4" /></div>
                  <div>
                    <div class="text-slate-300 font-medium mb-1">人工对账与报关，错漏风险高</div>
                    <div class="text-slate-500 text-sm leading-relaxed">跨越多个时区与币种，高度依赖人工 Excel 录入单证，极易引发扣关、罚款以及财务坏账的合规危机。</div>
                  </div>
                </li>
              </ul>
            </div>

            <div class="hidden md:flex absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 z-10">
              <div class="w-14 h-14 bg-[#1e243b] border-4 border-[#0a0d16] rounded-full flex items-center justify-center text-blue-400 shadow-2xl">
                <ArrowRight class="w-6 h-6" />
              </div>
            </div>

            <!-- White Box -->
            <div class="flex-1 bg-gradient-to-br from-blue-900/30 to-cyan-900/10 rounded-[2rem] p-8 md:p-12 border border-blue-500/20 relative overflow-hidden group">
              <div class="absolute inset-0 bg-blue-500/5 mix-blend-overlay group-hover:bg-blue-500/10 transition-colors duration-500"></div>
              <div class="relative z-10">
                <div class="text-cyan-400 text-sm font-bold uppercase tracking-widest mb-6 flex items-center gap-2">
                  <Eye class="w-5 h-5" />
                  AI Control Tower / 未来
                </div>
                <ul class="space-y-8">
                  <li class="flex gap-4">
                    <div class="mt-1 bg-cyan-500/20 text-cyan-300 p-1.5 rounded-full h-fit"><Check class="w-4 h-4" /></div>
                    <div>
                      <div class="text-white font-medium mb-1">全要素数字孪生，ETA 精准度 95%</div>
                      <div class="text-blue-200/70 text-sm leading-relaxed">聚合全球船司、港区、航司及 IoT 设备 API 数据，实现 SKU 级货品在途的无缝接力与厘米级追踪。</div>
                    </div>
                  </li>
                  <li class="flex gap-4">
                    <div class="mt-1 bg-cyan-500/20 text-cyan-300 p-1.5 rounded-full h-fit"><Check class="w-4 h-4" /></div>
                    <div>
                      <div class="text-white font-medium mb-1">风险前置感知，异常自动重路由</div>
                      <div class="text-blue-200/70 text-sm leading-relaxed">融合全球气象雷达与地缘冲突数据源，提前 48 小时预警受阻节点，AI 算法秒级生成最佳替代承运 B 计划。</div>
                    </div>
                  </li>
                  <li class="flex gap-4">
                    <div class="mt-1 bg-cyan-500/20 text-cyan-300 p-1.5 rounded-full h-fit"><Check class="w-4 h-4" /></div>
                    <div>
                      <div class="text-white font-medium mb-1">RPA 自动合规与账单秒级核销</div>
                      <div class="text-blue-200/70 text-sm leading-relaxed">内置最新全球贸易合规与关税规则库自动预审，多源异构费用单据由机器视觉 100% 自动稽核、对账与结算。</div>
                    </div>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>

        <div class="flex justify-center">
          <button class="px-10 py-5 rounded-full bg-white text-slate-900 font-bold text-lg hover:bg-slate-100 hover:scale-105 active:scale-95 transition-all duration-300 shadow-[0_0_40px_rgba(255,255,255,0.15)] flex items-center gap-3 group">
            <Activity class="w-5 h-5 text-blue-600" />
            开启供应链数字孪生
            <ArrowRight class="w-5 h-5 ml-1 text-slate-400 group-hover:translate-x-1 group-hover:text-slate-900 transition-all" />
          </button>
        </div>
      </div>
    </section>

    <!-- Ecosystem -->
    <section class="py-32 bg-white relative overflow-hidden">
      <div class="max-w-7xl mx-auto px-6 lg:px-8 relative z-10">
        <div class="text-center max-w-3xl mx-auto mb-20">
          <h2 class="text-3xl md:text-5xl font-semibold text-slate-900 mb-6 tracking-tight">开箱即用的全球生态网络</h2>
          <p class="text-lg md:text-xl text-slate-500 font-light leading-relaxed">
            预置全球 <span class="text-blue-600 font-medium">100+</span> 主流船东、港口、航司与海关系统的标准 API。无需漫长的 IT 对接，即刻点亮您的全球供应链。
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
          <div v-for="(eco, idx) in ECOSYSTEM" :key="idx" class="bg-[#fafafa] rounded-[2rem] p-8 border border-slate-100 hover:bg-white hover:shadow-[0_20px_40px_-15px_rgba(0,0,0,0.05)] transition-all duration-300 group cursor-pointer">
            <div :class="['w-14 h-14 rounded-2xl flex items-center justify-center mb-6 group-hover:scale-110 transition-all duration-300', eco.bgColor, eco.textColor, eco.hoverBg]">
              <component :is="eco.icon" class="w-7 h-7" />
            </div>
            <div class="text-3xl font-light text-slate-900 mb-2">{{ eco.count }}</div>
            <div class="text-slate-900 font-medium mb-1">{{ eco.title }}</div>
            <div class="text-slate-500 text-sm">{{ eco.sub }}</div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { markRaw } from 'vue'
import {
  Network, AlertTriangle, FileCheck, Calculator, ChevronDown,
  ArrowRight, ShieldCheck, Activity, Globe2, Lock, X, Check,
  Eye, EyeOff, Anchor, Plane, Building, Database
} from 'lucide-vue-next'

const IMAGES = {
  hero: "https://images.unsplash.com/photo-1684610529682-553625a1ffed?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHxnbG9iYWwlMjBnbG93aW5nJTIwZWFydGglMjBjb25uZWN0ZWQlMjBuZXR3b3JrJTIwZnV0dXJpc3RpYyUyMGRhcmt8ZW58MXx8fHwxNzgyMjg1NDQ3fDA&ixlib=rb-4.1.0&q=80&w=2000",
  tracking: "https://images.unsplash.com/photo-1579719558505-ad4a5fee0847?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHxjb250cm9sJTIwdG93ZXIlMjBzY3JlZW4lMjBkYXNoYm9hcmR8ZW58MXx8fHwxNzgyMjg1NDM5fDA&ixlib=rb-4.1.0&q=80&w=1080",
  warning: "https://images.unsplash.com/photo-1500740516770-92bd004b996e?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHx3ZWF0aGVyJTIwcmFkYXIlMjBzdG9ybSUyMGFic3RyYWN0fGVufDF8fHx8MTc4MjI4NTQzOXww&ixlib=rb-4.1.0&q=80&w=1080",
  customs: "https://images.unsplash.com/photo-1590935216109-8d3318de2c1c?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHxkaWdpdGFsJTIwZG9jdW1lbnQlMjBjb21wbGlhbmNlJTIwYWJzdHJhY3R8ZW58MXx8fHwxNzgyMjg1NDM5fDA&ixlib=rb-4.1.0&q=80&w=1080",
  settlement: "https://images.unsplash.com/photo-1762267683517-6e9bc20675e9?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHxmaW5hbmNpYWwlMjBkYXRhJTIwY2hhcnRzJTIwYWJzdHJhY3QlMjBkYXJrfGVufDF8fHx8MTc4MjI4NTQzOXww&ixlib=rb-4.1.0&q=80&w=1080"
}

const STATS = [
  { value: "95%", label: "物流节点可视率", sub: "End-to-End Visibility" },
  { value: "48h", label: "平均提前预警", sub: "Advance Warning" },
  { value: "99.2%", label: "清关合规率", sub: "Customs Compliance" },
  { value: "8x", label: "对账效率提升", sub: "Reconciliation Speed" }
]

const CAPABILITIES = [
  {
    id: "01", title: "全链路追踪", tagline: "数据打通 + 可视",
    description: "订单、工厂、货代、船公司、报关行——多方异构数据统一接入一张全局看板。系统内嵌高精度地缘风险监控，一旦发生冲突，自动关联受影响的航线与港口节点，让黑盒彻底透明化。",
    icon: markRaw(Network), iconColor: "text-blue-600",
    image: "https://images.unsplash.com/photo-1579719558505-ad4a5fee0847?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHxjb250cm9sJTIwdG93ZXIlMjBzY3JlZW4lMjBkYXNoYm9hcmR8ZW58MXx8fHwxNzgyMjg1NDM5fDA&ixlib=rb-4.1.0&q=80&w=1080",
    reverse: false
  },
  {
    id: "02", title: "异常预警", tagline: "风险前置",
    description: "AI 全天候 24h 不间断比对计划时刻表与实际物理进度。深度覆盖港口拥堵、航线中断、极端天气、地缘冲突等复杂场景；当风险超阈值时，自动触发预警并一键生成替代路线建议。",
    icon: markRaw(AlertTriangle), iconColor: "text-amber-500",
    image: "https://images.unsplash.com/photo-1500740516770-92bd004b996e?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHx3ZWF0aGVyJTIwcmFkYXIlMjBzdG9ybSUyMGFic3RyYWN0fGVufDF8fHx8MTc4MjI4NTQzOXww&ixlib=rb-4.1.0&q=80&w=1080",
    reverse: true
  },
  {
    id: "03", title: "关务通关", tagline: "合规前置",
    description: "基于先进 NLP 模型的 HS 编码辅助归类、FTA 优惠税率精准匹配与报关单证预审。内置全球关税政策变动实时追踪引擎（301/232/CBAM），彻底避免因一行编码填错导致的扣关与罚款风险。",
    icon: markRaw(FileCheck), iconColor: "text-emerald-600",
    image: "https://images.unsplash.com/photo-1590935216109-8d3318de2c1c?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHxkaWdpdGFsJTIwZG9jdW1lbnQlMjBjb21wbGlhbmNlJTIwYWJzdHJhY3R8ZW58MXx8fHwxNzgyMjg1NDM5fDA&ixlib=rb-4.1.0&q=80&w=1080",
    reverse: false
  },
  {
    id: "04", title: "结算对账", tagline: "多币种自动化",
    description: "彻底告别人工 Excel 对账。多源账单数据自动归集，AI 算法精准识别金额差异、漏付与重复计费。支持全球实时汇率自动换算并一键生成财务级合规报告，财务效能指数级跃升。",
    icon: markRaw(Calculator), iconColor: "text-purple-600",
    image: "https://images.unsplash.com/photo-1762267683517-6e9bc20675e9?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHxmaW5hbmNpYWwlMjBkYXRhJTIwY2hhcnRzJTIwYWJzdHJhY3QlMjBkYXJrfGVufDF8fHx8MTc4MjI4NTQzOXww&ixlib=rb-4.1.0&q=80&w=1080",
    reverse: true
  }
]

const ECOSYSTEM = [
  { count: "35+", title: "主流船东与港区", sub: "Top 20 Ocean Carriers", icon: markRaw(Anchor), bgColor: "bg-blue-50", textColor: "text-blue-600", hoverBg: "group-hover:bg-blue-600 group-hover:text-white" },
  { count: "80+", title: "国际航空货运", sub: "Global Airlines", icon: markRaw(Plane), bgColor: "bg-cyan-50", textColor: "text-cyan-600", hoverBg: "group-hover:bg-cyan-500 group-hover:text-white" },
  { count: "40+", title: "多国海关直连", sub: "Customs APIs", icon: markRaw(Building), bgColor: "bg-emerald-50", textColor: "text-emerald-600", hoverBg: "group-hover:bg-emerald-500 group-hover:text-white" },
  { count: "15+", title: "主流 ERP 预集成", sub: "Enterprise Systems", icon: markRaw(Database), bgColor: "bg-purple-50", textColor: "text-purple-600", hoverBg: "group-hover:bg-purple-500 group-hover:text-white" }
]
</script>
