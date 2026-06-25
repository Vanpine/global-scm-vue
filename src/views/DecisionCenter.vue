<template>
  <div class="min-h-screen bg-[#Fbfbfd] text-slate-900 font-sans selection:bg-blue-200">

    <!-- ===== Hero Section ===== -->
    <section class="relative h-screen min-h-[800px] flex items-center justify-center overflow-hidden">
      <div class="absolute inset-0 z-0">
        <ImageWithFallback
          src="https://images.unsplash.com/photo-1644088379091-d574269d422f?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHxhYnN0cmFjdCUyMGdsb3dpbmclMjBuZXR3b3JrJTIwZGF0YSUyMHN0cmVhbXN8ZW58MXx8fHwxNzgyMjkxNzg2fDA&ixlib=rb-4.1.0&q=80&w=1080"
          alt="AI Data Streams" class="w-full h-full object-cover" />
        <div class="absolute inset-0 bg-gradient-to-b from-slate-900/60 via-slate-900/80 to-[#Fbfbfd]"></div>
      </div>

      <div class="relative z-10 container mx-auto px-6 md:px-12 text-center transform translate-y-[-5%]">
        <h1
          class="text-5xl md:text-7xl lg:text-8xl font-bold tracking-tight text-white mb-6 animate-in fade-in slide-in-from-bottom-6 duration-700 delay-150">
          决策中枢
        </h1>
        <p
          class="text-xl md:text-3xl text-slate-300 max-w-3xl mx-auto font-light tracking-wide animate-in fade-in slide-in-from-bottom-8 duration-700 delay-300">
          自动化决策闭环，数据驱动告别经验拍板
        </p>
      </div>
    </section>

    <!-- ===== KPI Cards Section ===== -->
    <section class="relative z-20 -mt-32 w-full mx-auto px-6 md:px-8 mb-24">
      <div class="grid grid-cols-2 md:grid-cols-4 gap-4 md:gap-6">
        <div v-for="(kpi, idx) in kpis" :key="idx"
          class="bg-white/70 backdrop-blur-2xl border border-white p-6 rounded-3xl shadow-[0_8px_30px_rgba(0,0,0,0.04)] hover:shadow-[0_20px_40px_rgba(0,0,0,0.08)] hover:-translate-y-1 transition-all duration-500 ease-[cubic-bezier(0.16,1,0.3,1)] group">
          <div
            class="w-10 h-10 rounded-full bg-blue-50 text-blue-600 flex items-center justify-center mb-4 group-hover:scale-110 transition-transform duration-500">
            <component :is="kpi.icon" class="w-5 h-5" />
          </div>
          <div class="text-3xl md:text-4xl font-bold tracking-tight text-slate-900 mb-1">{{ kpi.value }}</div>
          <div class="text-sm font-medium text-slate-500">{{ kpi.title }}</div>
        </div>
      </div>
    </section>

    <!-- ===== Core Capabilities (Bento Grid) ===== -->
    <section class="w-[85%] mx-auto px-6 md:px-8 py-12 md:py-24">
      <div class="mb-16">
        <h2 class="text-4xl md:text-5xl font-bold tracking-tight text-slate-900 mb-4">四大核心能力</h2>
        <p class="text-xl text-slate-500 font-light">打破数据孤岛，实现从需求感知到生产排程的智能闭环。</p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-6 auto-rows-[280px]">

        <!-- Card 1: 销量预测 -->
        <div
          class="md:col-span-2 row-span-2 group relative overflow-hidden rounded-[2rem] bg-white border border-slate-100 shadow-sm hover:shadow-xl transition-all duration-700 ease-out p-8 md:p-12 flex flex-col justify-between">
          <div
            class="absolute top-0 right-0 w-96 h-96 bg-gradient-to-br from-blue-50 to-transparent rounded-full blur-3xl -z-10 opacity-50 group-hover:opacity-100 transition-opacity duration-700">
          </div>

          <div>
            <div
              class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full bg-blue-50 text-blue-600 text-sm font-semibold mb-6">
              <TrendingUp class="w-4 h-4" /> 销量预测
            </div>
            <h3
              class="text-3xl md:text-4xl font-bold tracking-tight text-slate-900 mb-4 group-hover:text-blue-600 transition-colors">
              "下个月能卖多少"<br />决定采购和现金流
            </h3>
            <p class="text-lg text-slate-500 leading-relaxed max-w-lg">
              多维信号融合（历史 + 宏观 + 竞品 + 社交情绪），实现滚动12周预测，越近越准，并支持偏差自校正。
            </p>
          </div>

          <div class="mt-8 flex gap-4">
            <div class="flex-1 bg-slate-50 rounded-2xl p-4 border border-slate-100/50">
              <div class="text-xs font-semibold text-slate-400 mb-1 uppercase tracking-wider">预测精度</div>
              <div class="text-2xl font-bold text-slate-800">98.2%</div>
              <div class="w-full h-1.5 bg-slate-200 rounded-full mt-3 overflow-hidden">
                <div class="h-full bg-blue-500 rounded-full w-[98.2%]"></div>
              </div>
            </div>
            <div class="flex-1 bg-slate-50 rounded-2xl p-4 border border-slate-100/50">
              <div class="text-xs font-semibold text-slate-400 mb-1 uppercase tracking-wider">模型自校正频率</div>
              <div class="text-2xl font-bold text-slate-800">实时</div>
              <div class="w-full h-1.5 bg-slate-200 rounded-full mt-3 overflow-hidden">
                <div class="h-full bg-indigo-500 rounded-full w-full"></div>
              </div>
            </div>
          </div>
        </div>

        <!-- Card 2: 生产计划优化 -->
        <div
          class="md:col-span-1 row-span-2 group relative overflow-hidden rounded-[2rem] bg-slate-900 text-white shadow-xl hover:shadow-2xl hover:shadow-indigo-500/20 transition-all duration-700 ease-out p-8 md:p-10 flex flex-col">
          <div
            class="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1551288049-bebda4e38f71?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&q=80&w=1080')] bg-cover bg-center opacity-10 group-hover:opacity-20 transition-opacity duration-700 mix-blend-luminosity">
          </div>
          <div class="absolute inset-0 bg-gradient-to-t from-slate-900 via-slate-900/80 to-slate-900/40"></div>

          <div class="relative z-10 flex-1">
            <div
              class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full bg-white/10 text-white text-sm font-semibold mb-6 backdrop-blur-md">
              <Factory class="w-4 h-4" /> 生产计划优化
            </div>
            <h3 class="text-2xl md:text-3xl font-bold tracking-tight mb-4">
              告别Excel排产<br />自动响应产线切换
            </h3>
            <p class="text-slate-300 leading-relaxed mb-8">
              基于订单优先级与物料齐套率自动排程。建立产能约束模型，当遇到插单、延迟或故障等异常事件时，系统自动重排。
            </p>
          </div>

          <div class="relative z-10 space-y-3">
            <div class="bg-white/5 border border-white/10 rounded-2xl p-4 backdrop-blur-md">
              <div class="flex justify-between items-center mb-2">
                <span class="text-sm font-medium text-slate-300">物料齐套率</span>
                <span class="text-sm font-bold text-green-400">100%</span>
              </div>
              <div class="w-full h-1 bg-white/10 rounded-full">
                <div class="h-full bg-green-400 rounded-full w-full"></div>
              </div>
            </div>
            <div class="bg-white/5 border border-white/10 rounded-2xl p-4 backdrop-blur-md">
              <div class="flex justify-between items-center mb-2">
                <span class="text-sm font-medium text-slate-300">产能利用率</span>
                <span class="text-sm font-bold text-blue-400">92.5%</span>
              </div>
              <div class="w-full h-1 bg-white/10 rounded-full">
                <div class="h-full bg-blue-400 rounded-full w-[92.5%]"></div>
              </div>
            </div>
          </div>
        </div>

        <!-- Card 3: 库存预测 -->
        <div
          class="md:col-span-1 row-span-1 group relative overflow-hidden rounded-[2rem] bg-white border border-slate-100 shadow-sm hover:shadow-xl transition-all duration-700 ease-out p-8 flex flex-col justify-center">
          <div
            class="w-12 h-12 rounded-2xl bg-indigo-50 text-indigo-600 flex items-center justify-center mb-6 group-hover:scale-110 transition-transform duration-500">
            <BarChart3 class="w-6 h-6" />
          </div>
          <h3
            class="text-xl font-bold tracking-tight text-slate-900 mb-3 group-hover:text-indigo-600 transition-colors">
            库存预测</h3>
          <p class="text-sm text-slate-500 leading-relaxed">
            解决库存积压与热销缺货难题。<br />
            <strong class="text-slate-700 font-semibold">SKU级需求感知 → 动态安全库存水位 → 积压/缺货自动预警。</strong>
          </p>
        </div>

        <!-- Card 4: 补货建议 -->
        <div
          class="md:col-span-2 row-span-1 group relative overflow-hidden rounded-[2rem] bg-white border border-slate-100 shadow-sm hover:shadow-xl transition-all duration-700 ease-out p-8 flex flex-col md:flex-row items-center gap-8">
          <div class="flex-1">
            <div
              class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full bg-teal-50 text-teal-700 text-sm font-semibold mb-4">
              <ShoppingCart class="w-4 h-4" /> 补货建议
            </div>
            <h3
              class="text-2xl font-bold tracking-tight text-slate-900 mb-3 group-hover:text-teal-600 transition-colors">
              自动计算多变量，审核即下单</h3>
            <p class="text-slate-500 leading-relaxed">
              实时追踪库存状态，综合考虑交期、价格、MOQ（最小起订量）和运费，输出最优补货方案。
            </p>
          </div>
          <div class="w-full md:w-64 bg-slate-50 rounded-2xl p-5 border border-slate-100 shrink-0">
            <div class="flex items-center justify-between text-sm mb-3">
              <span class="text-slate-500">待审核补货单</span>
              <span class="font-bold text-slate-900">12</span>
            </div>
            <div class="flex items-center gap-2 text-xs font-medium text-teal-600 bg-teal-50 px-3 py-2 rounded-lg">
              <CheckCircle2 class="w-4 h-4" /> 最优成本方案已生成
            </div>
          </div>
        </div>

      </div>
    </section>

    <!-- ===== Highlight: Embedded Supply Risk ===== -->
    <section class="bg-slate-900 text-white py-24 relative overflow-hidden mt-12">
      <div class="absolute inset-0 z-0 opacity-20">
        <div class="absolute top-0 right-0 w-[800px] h-[800px] bg-red-500/20 rounded-full blur-[120px]"></div>
        <div class="absolute bottom-0 left-0 w-[600px] h-[600px] bg-blue-500/20 rounded-full blur-[100px]"></div>
      </div>

      <div class="w-[85%] mx-auto px-6 md:px-8 relative z-10">
        <div class="flex flex-col md:flex-row items-center gap-12 lg:gap-24">

          <div class="flex-1">
            <div
              class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full bg-red-500/20 border border-red-500/30 text-red-300 text-sm font-semibold mb-6">
              <ShieldAlert class="w-4 h-4" /> 核心亮点：内嵌供应风险
            </div>
            <h2 class="text-4xl md:text-5xl font-bold tracking-tight mb-6">
              预见断供危机<br /><span class="text-slate-400">自动触发B计划</span>
            </h2>
            <p class="text-xl text-slate-300 font-light leading-relaxed mb-8">
              补货建议和生产排程深度集成供应商断供风险模型。当感知到高风险供应商时，系统自动触发替代方案；若发生物料延迟，立刻重排生产计划并推送备用供应商，确保供应链永不断链。
            </p>

            <button
              class="flex items-center gap-2 text-white font-medium hover:gap-4 transition-all duration-300 group">
              <span class="border-b border-white/30 group-hover:border-white pb-1 transition-colors">查看风险感知模型详情</span>
              <ArrowRight class="w-5 h-5" />
            </button>
          </div>

          <div class="flex-1 w-full max-w-lg">
            <div class="bg-white/10 backdrop-blur-2xl border border-white/20 rounded-[2rem] p-8 shadow-2xl">
              <div class="flex items-center justify-between mb-8 pb-6 border-b border-white/10">
                <h4 class="text-lg font-semibold">实时风险雷达</h4>
                <div class="flex items-center gap-2">
                  <span class="relative flex h-3 w-3">
                    <span
                      class="animate-ping absolute inline-flex h-full w-full rounded-full bg-red-400 opacity-75"></span>
                    <span class="relative inline-flex rounded-full h-3 w-3 bg-red-500"></span>
                  </span>
                  <span class="text-sm font-medium text-red-400">发现异常</span>
                </div>
              </div>

              <div class="space-y-4">
                <div class="bg-red-500/10 border border-red-500/20 rounded-2xl p-4 flex gap-4 items-start">
                  <AlertTriangle class="w-6 h-6 text-red-400 shrink-0" />
                  <div>
                    <div class="text-sm font-bold text-red-200 mb-1">供应商 A - 交付延迟预警</div>
                    <div class="text-xs text-slate-400 mb-3">受台风影响，预计MCU组件延迟 5 天交付。</div>
                    <div class="flex gap-2">
                      <button
                        class="text-xs bg-red-500 hover:bg-red-600 text-white px-3 py-1.5 rounded-lg transition-colors font-medium">重排生产计划</button>
                      <button
                        class="text-xs bg-white/10 hover:bg-white/20 text-white px-3 py-1.5 rounded-lg transition-colors font-medium">启用替代供应商</button>
                    </div>
                  </div>
                </div>

                <div class="bg-white/5 border border-white/10 rounded-2xl p-4 flex gap-4 items-center">
                  <div class="w-2 h-2 rounded-full bg-green-400"></div>
                  <div class="flex-1">
                    <div class="text-sm font-medium text-slate-200">供应商 B - 产能评估通过</div>
                  </div>
                  <div class="text-xs text-slate-400">2 mins ago</div>
                </div>
              </div>
            </div>
          </div>

        </div>
      </div>
    </section>

  </div>
</template>

<script setup>
import { markRaw } from 'vue'
import {
  BarChart3, TrendingUp, AlertTriangle, PackageSearch,
  ShoppingCart, Factory, ArrowRight, ShieldAlert, Target,
  CheckCircle2
} from 'lucide-vue-next'
import ImageWithFallback from '@/components/ImageWithFallback.vue'

const kpis = [
  { title: "库存周转提升", value: "+32%", icon: markRaw(PackageSearch) },
  { title: "预测精度改善", value: "95.8%", icon: markRaw(Target) },
  { title: "补货效率提升", value: "4x", icon: markRaw(ShoppingCart) },
  { title: "排产优化节省", value: "-45%", icon: markRaw(Factory) }
]
</script>
