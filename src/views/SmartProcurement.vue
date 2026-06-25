<template>
  <div class="bg-[#F5F5F7] min-h-screen text-slate-900 selection:bg-blue-200">
    <!-- Hero -->
    <section
      class="relative h-screen min-h-[800px] w-full flex items-center justify-center overflow-hidden bg-[#020617]">
      <!-- Background Elements -->
      <div class="absolute inset-0 z-0">
        <!-- High-tech Node/Network Image -->
        <img src="https://images.unsplash.com/photo-1558494949-ef010cbdcc31?auto=format&fit=crop&w=2500&q=80"
          alt="Smart Procurement Network"
          class="w-full h-full object-cover object-center opacity-40 mix-blend-screen scale-105" />
        <!-- Gradient Overlays -->
        <div class="absolute inset-0 bg-gradient-to-b from-[#020617]/80 via-[#0f172a]/70 to-[#020617]"></div>

        <!-- Glowing Orbs for Tech Feel -->
        <div class="absolute top-1/4 left-1/4 w-[40rem] h-[40rem] bg-blue-600/20 rounded-full blur-[120px]"></div>
        <div class="absolute bottom-1/4 right-1/4 w-[40rem] h-[40rem] bg-indigo-600/20 rounded-full blur-[120px]"></div>

        <!-- Grid Pattern -->
        <div
          class="absolute inset-0 bg-[linear-gradient(to_right,rgba(255,255,255,0.03)_1px,transparent_1px),linear-gradient(to_bottom,rgba(255,255,255,0.03)_1px,transparent_1px)] bg-[size:4rem_4rem] [mask-image:radial-gradient(ellipse_80%_50%_at_50%_50%,#000_70%,transparent_100%)]">
        </div>
      </div>

      <div class="relative z-10 max-w-6xl mx-auto px-6 text-center -mt-20">
        <h1 v-motion :initial="{ opacity: 0, y: 30 }"
          :enter="{ opacity: 1, y: 0, transition: { duration: 800, delay: 100, ease: [0.16, 1, 0.3, 1] } }"
          class="text-5xl md:text-7xl lg:text-8xl font-bold tracking-tight text-white leading-[1.1] mb-8">
          全球寻源，精准匹配
        </h1>

        <p v-motion :initial="{ opacity: 0, y: 30 }"
          :enter="{ opacity: 1, y: 0, transition: { duration: 800, delay: 200, ease: [0.16, 1, 0.3, 1] } }"
          class="text-xl md:text-2xl text-slate-300 font-light max-w-3xl mx-auto leading-relaxed mb-12">
          AI 驱动的全球寻源与智能决策，让每一次采购都先人一步。
        </p>
      </div>

      <!-- Decorative Bottom Transition -->
      <div
        class="absolute bottom-0 left-0 w-full h-40 bg-gradient-to-t from-[#F5F5F7] to-transparent z-10 pointer-events-none">
      </div>
    </section>

    <!-- Content -->
    <div class="relative z-20 bg-[#F5F5F7] rounded-t-[3rem] -mt-16 pt-24 pb-32 shadow-[0_-20px_40px_rgba(0,0,0,0.1)]">

      <!-- Pipeline -->
      <section class="w-[85%] mx-auto px-6 lg:px-8 mb-40">
        <div class="text-center mb-24">
          <div class="text-4xl md:text-6xl font-bold tracking-widest text-slate-200 mb-6 uppercase">DECISION MATRIX
          </div>
          <h2 class="text-2xl md:text-3xl font-medium text-slate-500">全链路智能决策矩阵</h2>
        </div>

        <div class="space-y-24 md:space-y-32 mt-12">
          <div v-for="(stage, index) in pipelineStages" :key="stage.id" data-reveal
            :style="{ transitionDelay: index * 80 + 'ms' }"
            :class="['group relative flex flex-col items-center reveal-item', index % 2 === 1 ? 'md:flex-row-reverse' : 'md:flex-row']">
            <!-- Image Section (Larger, edge-to-edge feel) -->
            <div
              class="w-full md:w-2/3 relative h-[400px] md:h-[560px] rounded-[3rem] overflow-hidden shadow-2xl shadow-slate-200/50 z-0">
              <img :src="stage.image" :alt="stage.title"
                class="absolute inset-0 w-full h-full object-cover transform group-hover:scale-105 transition-transform duration-1000 ease-[cubic-bezier(0.16,1,0.3,1)]" />
              <div class="absolute inset-0 bg-slate-900/10 group-hover:bg-transparent transition-colors duration-700">
              </div>
            </div>

            <!-- Text Card Section (Overlapping Glassmorphism) -->
            <div
              :class="['w-[90%] md:w-[45%] relative z-10 -mt-20 md:mt-0 bg-white/85 backdrop-blur-2xl rounded-[2.5rem] p-8 md:p-12 shadow-[0_30px_60px_rgba(0,0,0,0.08)] border border-white hover:bg-white transition-colors duration-500', index % 2 === 1 ? 'md:-mr-24' : 'md:-ml-24']">
              <!-- Giant Watermark Number -->
              <div
                class="absolute top-0 right-6 -mt-8 text-[8rem] font-black text-slate-50 select-none pointer-events-none z-0 group-hover:text-blue-50 transition-colors duration-500">
                {{ stage.id }}
              </div>

              <div class="relative z-10 space-y-8">
                <!-- Icon -->
                <div
                  class="w-16 h-16 rounded-2xl bg-gradient-to-br from-blue-600 to-indigo-600 text-white flex items-center justify-center shadow-lg shadow-blue-500/30 transform group-hover:-translate-y-1 transition-transform duration-300">
                  <component :is="stage.icon" class="w-8 h-8" />
                </div>

                <!-- Title -->
                <div>
                  <h3
                    class="text-3xl md:text-4xl font-bold text-slate-900 mb-3 tracking-tight group-hover:text-blue-600 transition-colors duration-300">
                    {{ stage.title }}</h3>
                  <p class="text-blue-600/80 font-semibold tracking-widest text-sm uppercase">{{ stage.subtitle }}</p>
                </div>

                <!-- Details List -->
                <ul class="space-y-5 pt-6 border-t border-slate-100">
                  <li v-for="(detail, idx) in stage.details" :key="idx" class="flex items-start group/item">
                    <div
                      class="mt-2.5 mr-4 shrink-0 w-2 h-2 rounded-full bg-transparent border-2 border-blue-400 group-hover/item:bg-blue-500 group-hover/item:border-blue-500 group-hover/item:scale-150 transition-all duration-300">
                    </div>
                    <span class="text-slate-600 text-lg font-light leading-relaxed">{{ detail }}</span>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Bento Grid -->
      <section class="w-[85%] mx-auto px-6 lg:px-8 mb-40">
        <div class="mb-24 text-center">
          <div class="text-4xl md:text-6xl font-bold tracking-widest text-slate-200 mb-6 uppercase">CORE TECH</div>
          <h2 class="text-2xl md:text-3xl font-medium text-slate-500">核心技术底座</h2>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-6 auto-rows-[280px]">
          <div v-for="(cap, idx) in coreCapabilities" :key="idx" data-reveal
            :style="{ transitionDelay: idx * 80 + 'ms' }"
            :class="['reveal-item group relative rounded-[2.5rem] p-10 overflow-hidden shadow-[0_8px_30px_rgb(0,0,0,0.04)] hover:shadow-[0_20px_40px_rgb(0,0,0,0.08)] transition-all duration-500 cursor-pointer', idx === 0 || idx === 3 ? 'bg-slate-900 text-white' : 'bg-white text-slate-900']">
            <div v-if="idx === 0 || idx === 3"
              class="absolute -top-20 -right-20 w-64 h-64 bg-blue-500/20 blur-[60px] rounded-full group-hover:bg-blue-500/30 transition-colors duration-500">
            </div>

            <div class="relative z-10 flex flex-col h-full justify-between">
              <div
                :class="['w-14 h-14 rounded-2xl flex items-center justify-center', idx === 0 || idx === 3 ? 'bg-white/10 text-white backdrop-blur-md' : 'bg-blue-50 text-blue-600']">
                <component :is="cap.icon" class="w-7 h-7" />
              </div>
              <div>
                <h3 :class="['text-2xl font-semibold mb-3', idx === 0 || idx === 3 ? 'text-white' : 'text-slate-900']">
                  {{ cap.title }}</h3>
                <p
                  :class="['font-light leading-relaxed text-lg', idx === 0 || idx === 3 ? 'text-slate-300' : 'text-slate-500']">
                  {{ cap.description }}</p>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Stats -->
      <section class="w-full mx-auto px-6 lg:px-8 mb-32">
        <div class="bg-white rounded-[3rem] p-12 md:p-20 shadow-[0_8px_30px_rgb(0,0,0,0.04)]">
          <div class="grid grid-cols-2 md:grid-cols-4 gap-12 md:gap-8 divide-x divide-slate-100">
            <div v-for="(stat, idx) in stats" :key="idx" class="text-center px-4">
              <div v-motion :initial="{ opacity: 0, scale: 0.9 }"
                :visible="{ opacity: 1, scale: 1, transition: { duration: 600, delay: idx * 100, ease: [0.16, 1, 0.3, 1] } }"
                :visible-once="true" class="text-5xl md:text-6xl font-semibold text-slate-900 mb-4">
                {{ stat.value }}
              </div>
              <p class="text-slate-500 text-sm md:text-base font-light">{{ stat.label }}</p>
            </div>
          </div>
        </div>
      </section>

      <!-- CTA -->
      <section class="max-w-4xl mx-auto px-6 text-center space-y-10 pb-12">
        <h2 class="text-4xl md:text-6xl font-semibold tracking-tight text-slate-900">
          准备好让您的供应链进化了吗？
        </h2>
        <p class="text-xl text-slate-500 font-light max-w-2xl mx-auto">
          加入全球顶尖企业的行列，用 AI 赋能每一次采购决策。
        </p>
        <div class="flex justify-center pt-6">
          <RouterLink to="/join"
            class="px-10 py-5 rounded-full bg-slate-900 text-white font-medium text-lg hover:bg-slate-800 hover:scale-105 active:scale-95 transition-all duration-300 flex items-center justify-center group shadow-xl shadow-slate-900/20">
            申请加入
            <ArrowRight class="w-5 h-5 ml-2 group-hover:translate-x-1 transition-transform" />
          </RouterLink>
        </div>
      </section>

    </div>
  </div>
</template>

<script setup>
import { markRaw, onMounted } from 'vue'
import { RouterLink } from 'vue-router'
import {
  Globe, Cpu, ShieldCheck, Zap, Search,
  MessageSquare, Scale, FileText, Lightbulb, ArrowRight
} from 'lucide-vue-next'

onMounted(() => {
  const els = document.querySelectorAll('[data-reveal]')
  const obs = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('visible')
        obs.unobserve(entry.target)
      }
    })
  }, { threshold: 0.1 })
  els.forEach(el => obs.observe(el))
})

const pipelineStages = [
  {
    id: "01",
    title: "智能寻源",
    subtitle: "Intelligent Sourcing",
    details: [
      "千万级供应商智能匹配与多维度资质交叉验证",
      "供应商财务健康度、ESG 合规、反贿赂与制裁清单自动尽调",
      "全球地缘风险与贸易合规自动扫描"
    ],
    icon: markRaw(Search),
    image: "https://images.unsplash.com/photo-1494412519320-aa613dfb7738?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHxnbG9iYWwlMjBsb2dpc3RpY3MlMjBuZXR3b3JrfGVufDF8fHx8MTc4MjI4MDgxN3ww&ixlib=rb-4.1.0&q=80&w=1080"
  },
  {
    id: "02",
    title: "自动询盘",
    subtitle: "Automated Inquiry",
    details: [
      "需求一键提取，自动生成多语言询价单",
      "RFP/RFQ 点对点分发与全流程进度追踪",
      "供应商反馈数据结构化提取与自动归档"
    ],
    icon: markRaw(MessageSquare),
    image: "https://images.unsplash.com/photo-1650870218354-0a185ae8181a?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHxtb2Rlcm4lMjBzZXJ2ZXIlMjByb29tJTIwYmx1ZXxlbnwxfHx8fDE3ODIyODA4MTh8MA&ixlib=rb-4.1.0&q=80&w=1080"
  },
  {
    id: "03",
    title: "智能比价",
    subtitle: "Smart Price Comparison",
    details: [
      "历史价格走势与宏观指数实时对标分析",
      "TCO（总拥有成本）多维深度拆解与量化分析",
      "隐含成本预警与异常报价 AI 自动标注"
    ],
    icon: markRaw(Scale),
    image: "https://images.unsplash.com/photo-1551288049-bebda4e38f71?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHxkYXRhJTIwYW5hbHl0aWNzJTIwZGFzaGJvYXJkJTIwbWluaW1hbGlzdHxlbnwxfHx8fDE3ODIyODA4MTh8MA&ixlib=rb-4.1.0&q=80&w=1080"
  },
  {
    id: "04",
    title: "合同管理",
    subtitle: "Contract Management",
    details: [
      "NLP 语义引擎自动核查法务条款与商业风险",
      "履约关键节点智能预警与自动化监控",
      "全球多地电子签名集成与区块链防篡改存证"
    ],
    icon: markRaw(FileText),
    image: "https://images.unsplash.com/photo-1672380135241-c024f7fbfa13?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHxidXNpbmVzcyUyMGNvbnRyYWN0JTIwaGFuZHNoYWtlJTIwbWluaW1hbHxlbnwxfHx8fDE3ODIyODA4MTh8MA&ixlib=rb-4.1.0&q=80&w=1080"
  },
  {
    id: "05",
    title: "方案生成",
    subtitle: "Solution Generation",
    details: [
      "产能、交期与成本多目标最优解推演",
      "不同风险偏好下的一键备选采购策略",
      "全局 ROI 可视化看板，一键辅助决策"
    ],
    icon: markRaw(Lightbulb),
    image: "https://images.unsplash.com/photo-1622547748225-3fc4abd2cca0?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHxtaW5pbWFsaXN0JTIwdGVjaG5vbG9neSUyMGFic3RyYWN0fGVufDF8fHx8MTc4MjI4MDgxOHww&ixlib=rb-4.1.0&q=80&w=1080"
  }
]

const coreCapabilities = [
  {
    title: "全局数据视野",
    description: "直连全球主流商业数据库，实时洞察多地区市场动态、汇率波动与大盘价格走势。",
    icon: markRaw(Globe)
  },
  {
    title: "AI 算力引擎",
    description: "百亿级参数模型针对供应链场景深度微调，提供超越人工经验的洞察与推演。",
    icon: markRaw(Cpu)
  },
  {
    title: "主动风险阻断",
    description: "全天候监控供应商舆情与宏观黑天鹅事件，秒级触发预警并一键生成替代方案。",
    icon: markRaw(ShieldCheck)
  },
  {
    title: "全球毫秒级协同",
    description: "云原生分布式架构支撑千万级并发，全球采购节点数据实时同步无延迟。",
    icon: markRaw(Zap)
  }
]

const stats = [
  { value: "50M+", label: "全球活跃供应商网络" },
  { value: "99.9%", label: "高危合规风险拦截率" },
  { value: "15%", label: "平均采购降本率" },
  { value: "10W+", label: "每日监控动态风险事件" }
]
</script>

<style scoped>
.reveal-item {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.5s ease, transform 0.5s ease;
}

.reveal-item.visible {
  opacity: 1;
  transform: translateY(0);
}
</style>
