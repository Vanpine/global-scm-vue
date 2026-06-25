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

      <div class="relative z-10 max-w-6xl mx-auto px-6 text-center -mt-20">
        <h1
          v-motion
          :initial="{ opacity: 0, y: 30 }"
          :enter="{ opacity: 1, y: 0, transition: { duration: 800, delay: 100, ease: [0.16, 1, 0.3, 1] } }"
          class="text-5xl md:text-7xl lg:text-8xl font-bold tracking-tight text-white mb-8">
          数据驱动，决策有据
        </h1>
        <p
          v-motion
          :initial="{ opacity: 0, y: 30 }"
          :enter="{ opacity: 1, y: 0, transition: { duration: 800, delay: 200, ease: [0.16, 1, 0.3, 1] } }"
          class="text-xl md:text-2xl text-slate-300 max-w-3xl mx-auto font-light leading-relaxed">
          全平台数据实时汇聚分析，每一次决策都有据可依
        </p>
      </div>
    </section>

    <!-- ===== KPI Cards Section ===== -->
    <section class="relative z-20 -mt-32 max-w-6xl mx-auto px-6 md:px-8">
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

    <!-- ===== AI Interactive Command Center (New Section) ===== -->
    <section class="w-full mx-auto px-6 md:px-8 py-16 md:py-24 bg-slate-900 text-white relative overflow-hidden mt-16">
      <div class="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1451187580459-43490279c0fa?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&q=80&w=2000')] bg-cover bg-center opacity-10 mix-blend-screen"></div>
      <div class="absolute inset-0 bg-gradient-to-b from-slate-900 via-slate-900/90 to-slate-900"></div>
      
      <div class="max-w-7xl mx-auto relative z-10">
        <div class="text-center mb-16">
          <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-blue-500/10 border border-blue-500/20 text-blue-400 text-sm font-semibold mb-6 backdrop-blur-md">
            <span class="relative flex h-2 w-2">
              <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-blue-400 opacity-75"></span>
              <span class="relative inline-flex rounded-full h-2 w-2 bg-blue-500"></span>
            </span>
            LIVE COMMAND CENTER
          </div>
          <h2 class="text-4xl md:text-5xl font-bold tracking-tight mb-6">全局可视，一键指挥</h2>
          <p class="text-xl text-slate-400 font-light max-w-3xl mx-auto">
            将散落在 ERP、CRM、物流系统中的海量数据，转化为直观的全局作战地图。支持自然语言交互，让供应链指挥像对话一样简单。
          </p>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
          <!-- Left: Chat/Command Interface -->
          <div class="lg:col-span-4 bg-white/5 border border-white/10 rounded-[2rem] p-6 backdrop-blur-xl flex flex-col h-[600px]">
            <div class="flex items-center gap-3 mb-6 pb-4 border-b border-white/10">
              <div class="w-10 h-10 rounded-full bg-blue-600 flex items-center justify-center">
                <Bot class="w-5 h-5 text-white" />
              </div>
              <div>
                <h3 class="font-semibold text-slate-200">AI 供应链助手</h3>
                <p class="text-xs text-slate-400">在线 · 实时监控中</p>
              </div>
            </div>
            
            <div class="flex-1 overflow-y-auto space-y-4 pr-2 custom-scrollbar">
              <div class="bg-white/10 rounded-2xl rounded-tl-none p-4 text-sm text-slate-300 w-11/12">
                系统检测到红海航线拥堵加剧，预计影响 3 个批次的欧洲交付订单，是否需要查看替代方案？
              </div>
              <div class="bg-blue-600 rounded-2xl rounded-tr-none p-4 text-sm text-white w-10/12 self-end ml-auto">
                列出受影响的订单，并评估空运替代成本。
              </div>
              <div class="bg-white/10 rounded-2xl rounded-tl-none p-4 text-sm text-slate-300 w-11/12 space-y-3">
                <p>已为您生成评估报告：</p>
                <div class="bg-black/20 rounded-xl p-3 border border-white/5">
                  <div class="flex justify-between mb-1"><span class="text-slate-400">受影响订单</span><span class="font-medium text-white">PO-202606-882 等 3 笔</span></div>
                  <div class="flex justify-between mb-1"><span class="text-slate-400">原定海运成本</span><span class="font-medium text-white">$12,500</span></div>
                  <div class="flex justify-between"><span class="text-slate-400">空运替代成本</span><span class="font-medium text-red-400">$45,000 (+260%)</span></div>
                </div>
                <p class="text-xs text-blue-300 cursor-pointer hover:text-blue-200">点击查看详细对比报告 &rarr;</p>
              </div>
            </div>
            
            <div class="mt-4 pt-4 border-t border-white/10 relative">
              <input type="text" placeholder="输入指令或询问供应链状态..." class="w-full bg-black/20 border border-white/10 rounded-full py-3 pl-4 pr-12 text-sm text-white focus:outline-none focus:border-blue-500 transition-colors" />
              <button class="absolute right-2 top-1/2 -translate-y-1/2 mt-2 w-8 h-8 rounded-full bg-blue-600 flex items-center justify-center hover:bg-blue-500 transition-colors">
                <Send class="w-4 h-4 text-white" />
              </button>
            </div>
          </div>

          <!-- Right: Visual Dashboard Mockup -->
          <div class="lg:col-span-8 bg-black/40 border border-white/10 rounded-[2rem] p-6 backdrop-blur-xl relative overflow-hidden h-[600px] flex flex-col">
            <div class="flex justify-between items-center mb-6">
              <h3 class="font-semibold text-slate-200 text-lg">全球物流实时监控网络</h3>
              <div class="flex gap-2">
                <span class="px-3 py-1 rounded-full bg-green-500/20 text-green-400 text-xs border border-green-500/30">正常 85%</span>
                <span class="px-3 py-1 rounded-full bg-yellow-500/20 text-yellow-400 text-xs border border-yellow-500/30">延误 12%</span>
                <span class="px-3 py-1 rounded-full bg-red-500/20 text-red-400 text-xs border border-red-500/30">中断 3%</span>
              </div>
            </div>
            
            <!-- Map Area -->
            <div class="flex-1 relative rounded-xl overflow-hidden border border-white/5 bg-slate-900/50">
              <img src="https://images.unsplash.com/photo-1524661135-423995f22d0b?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&q=80&w=1080" alt="World Map" class="absolute inset-0 w-full h-full object-cover opacity-30 mix-blend-luminosity" />
              
              <!-- Map Nodes & Connections (CSS generated for tech feel) -->
              <div class="absolute top-[30%] left-[20%] w-3 h-3 bg-blue-500 rounded-full shadow-[0_0_15px_rgba(59,130,246,1)]">
                <div class="absolute inset-0 bg-blue-400 rounded-full animate-ping opacity-75"></div>
              </div>
              <div class="absolute top-[40%] left-[50%] w-4 h-4 bg-emerald-500 rounded-full shadow-[0_0_15px_rgba(16,185,129,1)]">
                <div class="absolute inset-0 bg-emerald-400 rounded-full animate-ping opacity-75"></div>
              </div>
              <div class="absolute top-[35%] right-[25%] w-3 h-3 bg-red-500 rounded-full shadow-[0_0_15px_rgba(239,68,68,1)]">
                <div class="absolute inset-0 bg-red-400 rounded-full animate-ping opacity-75"></div>
              </div>
              
              <!-- SVG Lines -->
              <svg class="absolute inset-0 w-full h-full pointer-events-none" style="filter: drop-shadow(0 0 4px rgba(59,130,246,0.5));">
                <path d="M 20% 30% Q 35% 20% 50% 40%" fill="none" stroke="rgba(59,130,246,0.6)" stroke-width="2" stroke-dasharray="4 4" class="animate-[dash_20s_linear_infinite]" />
                <path d="M 50% 40% Q 65% 50% 75% 35%" fill="none" stroke="rgba(239,68,68,0.6)" stroke-width="2" stroke-dasharray="4 4" class="animate-[dash_20s_linear_infinite]" />
              </svg>
              
              <!-- Floating Info Panel -->
              <div class="absolute bottom-4 right-4 bg-black/60 backdrop-blur-md border border-white/10 rounded-xl p-4 w-64">
                <div class="text-xs text-slate-400 mb-1">当前焦点预警</div>
                <div class="font-medium text-red-400 mb-2">鹿特丹港拥堵</div>
                <div class="space-y-2">
                  <div class="flex justify-between text-xs"><span class="text-slate-400">滞留货船</span><span class="text-white">12 艘</span></div>
                  <div class="flex justify-between text-xs"><span class="text-slate-400">预计延误</span><span class="text-white">4-6 天</span></div>
                  <div class="w-full bg-white/10 h-1.5 rounded-full mt-1"><div class="bg-red-500 h-1.5 rounded-full w-[80%]"></div></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== Scenario Simulation (New Section) ===== -->
    <section class="w-full bg-[#0a0f1c] py-32 border-t border-white/5 relative overflow-hidden">
      <!-- Background Elements -->
      <div class="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1558494949-ef010cbdcc31?auto=format&fit=crop&w=2000&q=80')] bg-cover bg-center opacity-5 mix-blend-screen"></div>
      <div class="absolute inset-0 bg-[linear-gradient(to_right,rgba(255,255,255,0.02)_1px,transparent_1px),linear-gradient(to_bottom,rgba(255,255,255,0.02)_1px,transparent_1px)] bg-[size:3rem_3rem]"></div>
      
      <div class="max-w-[90rem] mx-auto px-6 lg:px-8 relative z-10">
        <div class="text-center mb-24">
          <div class="inline-flex items-center gap-2 px-4 py-1.5 rounded-full bg-indigo-500/10 border border-indigo-500/20 text-indigo-400 text-sm font-semibold mb-6">
            <Activity class="w-4 h-4" /> DIGITAL TWIN SIMULATION
          </div>
          <h2 class="text-4xl md:text-5xl font-bold tracking-tight text-white mb-6">沙盘推演，未雨绸缪</h2>
          <p class="text-xl text-slate-400 font-light max-w-2xl mx-auto">
            在真实风险发生前，通过供应链仿真引擎进行压力测试与预案演练。
          </p>
        </div>

        <!-- Carousel for Scenarios -->
        <div class="relative">
          <div ref="carouselRef" @scroll="onScroll"
            class="flex gap-6 overflow-x-auto snap-x snap-mandatory carousel-track pb-4">
            <div v-for="(scenario, idx) in scenarios" :key="idx"
              class="snap-start shrink-0 w-[85vw] md:w-[calc(50%-0.75rem)] lg:w-[calc(33.333%-1rem)] relative group">
              <div class="h-full bg-white/5 border border-white/10 rounded-[2.5rem] p-8 backdrop-blur-xl hover:bg-white/10 transition-colors duration-500 flex flex-col">
                <div class="relative w-full h-48 rounded-2xl overflow-hidden mb-8 border border-white/10">
                  <img :src="scenario.image" :alt="scenario.title" class="absolute inset-0 w-full h-full object-cover opacity-60 group-hover:opacity-100 group-hover:scale-110 transition-all duration-700 mix-blend-luminosity group-hover:mix-blend-normal" />
                  <div class="absolute inset-0 bg-gradient-to-t from-[#0a0f1c] to-transparent"></div>
                </div>
                <div class="flex-1 flex flex-col">
                  <h3 class="text-2xl font-bold text-white mb-3 group-hover:text-indigo-400 transition-colors">{{ scenario.title }}</h3>
                  <p class="text-slate-400 text-sm leading-relaxed mb-8 flex-1">{{ scenario.desc }}</p>
                  <div class="bg-black/40 rounded-2xl p-5 border border-white/5 font-mono">
                    <div class="text-xs text-indigo-400 mb-3 flex items-center gap-2">
                      <Zap class="w-3 h-3" /> EXPECTED_OUTPUTS
                    </div>
                    <ul class="space-y-3">
                      <li v-for="(item, i) in scenario.outputs" :key="i" class="flex items-start text-sm text-slate-300">
                        <span class="text-emerald-500 mr-2 mt-0.5">❯</span>
                        {{ item }}
                      </li>
                    </ul>
                  </div>
                </div>
                <div class="absolute inset-0 rounded-[2.5rem] border-2 border-indigo-500/0 group-hover:border-indigo-500/30 transition-colors duration-500 pointer-events-none"></div>
              </div>
            </div>
          </div>

          <!-- Prev / Next Buttons -->
          <button @click="prev"
            class="absolute -left-5 top-1/2 -translate-y-1/2 w-12 h-12 rounded-full bg-white/10 border border-white/20 backdrop-blur-xl flex items-center justify-center text-white hover:bg-white/20 transition-colors disabled:opacity-30 disabled:cursor-not-allowed"
            :disabled="currentIndex === 0">
            <ChevronLeft class="w-5 h-5" />
          </button>
          <button @click="next"
            class="absolute -right-5 top-1/2 -translate-y-1/2 w-12 h-12 rounded-full bg-white/10 border border-white/20 backdrop-blur-xl flex items-center justify-center text-white hover:bg-white/20 transition-colors disabled:opacity-30 disabled:cursor-not-allowed"
            :disabled="currentIndex >= maxIndex">
            <ChevronRight class="w-5 h-5" />
          </button>

          <!-- Dots -->
          <div class="flex justify-center gap-2 mt-8">
            <button v-for="(_, idx) in slidesCount" :key="idx" @click="goTo(idx)"
              class="w-2.5 h-2.5 rounded-full transition-all duration-300"
              :class="idx === currentIndex ? 'bg-indigo-400 w-8' : 'bg-white/20 hover:bg-white/40'" />
          </div>
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
import { markRaw, ref, computed, onMounted, onUnmounted } from 'vue'
import {
  BarChart3, TrendingUp, AlertTriangle, PackageSearch,
  ShoppingCart, Factory, ArrowRight, ShieldAlert, Target,
  CheckCircle2, Bot, Send, Globe, ChevronLeft, ChevronRight
} from 'lucide-vue-next'
import ImageWithFallback from '@/components/ImageWithFallback.vue'

const carouselRef = ref(null)
const currentIndex = ref(0)
const slidesPerView = ref(3)

const maxIndex = computed(() => Math.max(0, scenarios.length - slidesPerView.value))
const slidesCount = computed(() => Math.max(1, scenarios.length - slidesPerView.value + 1))

function getCardWidth() {
  const card = carouselRef.value?.children[0]
  return card ? card.offsetWidth + 24 : 300 // 24 = gap-6
}

function scrollToCard(index) {
  const w = getCardWidth()
  carouselRef.value?.scrollTo({ left: index * w, behavior: 'smooth' })
}

function prev() {
  if (currentIndex.value > 0) {
    currentIndex.value--
    scrollToCard(currentIndex.value)
  }
}
function next() {
  if (currentIndex.value < maxIndex.value) {
    currentIndex.value++
    scrollToCard(currentIndex.value)
  }
}
function goTo(idx) {
  currentIndex.value = Math.min(idx, maxIndex.value)
  scrollToCard(currentIndex.value)
}

function onScroll() {
  const w = getCardWidth()
  if (!w || !carouselRef.value) return
  const idx = Math.round(carouselRef.value.scrollLeft / w)
  currentIndex.value = Math.min(idx, maxIndex.value)
}

function updateSlides() {
  slidesPerView.value = window.innerWidth >= 1024 ? 3 : window.innerWidth >= 768 ? 2 : 1
  if (currentIndex.value > maxIndex.value) currentIndex.value = maxIndex.value
}
onMounted(() => {
  updateSlides()
  window.addEventListener('resize', updateSlides)
})
onUnmounted(() => {
  window.removeEventListener('resize', updateSlides)
})
const kpis = [
  { title: "库存周转提升", value: "+32%", icon: markRaw(PackageSearch) },
  { title: "预测准确率", value: "95.8%", icon: markRaw(Target) },
  { title: "补货效率提升", value: "4x", icon: markRaw(ShoppingCart) },
  { title: "排产优化节省", value: "-45%", icon: markRaw(Factory) }
]

const scenarios = [
  {
    title: "地缘政治冲突模拟",
    desc: "模拟特定海峡封锁或关税突增对全局交付成本与时效的影响，提前锁定替代产能。",
    icon: markRaw(Globe),
    image: "https://images.unsplash.com/photo-1586528116311-ad8dd3c8310d?auto=format&fit=crop&w=1200&q=80",
    outputs: ["航线重路由方案", "关税成本对冲策略", "备用供应商激活清单"]
  },
  {
    title: "极端天气灾害推演",
    desc: "结合全球气象数据，预测台风、洪涝对关键港口及核心物料产区的破坏程度。",
    icon: markRaw(AlertTriangle),
    image: "https://images.unsplash.com/photo-1470071459604-3b5ec3a7fe05?auto=format&fit=crop&w=1200&q=80",
    outputs: ["安全库存动态调拨", "受灾节点订单转移", "物流延误客户预警"]
  },
  {
    title: "需求暴增/骤降测试",
    desc: "模拟大促爆单或黑天鹅事件导致的需求断崖，测试当前产能弹性和库存缓冲能力。",
    icon: markRaw(TrendingUp),
    image: "https://images.unsplash.com/photo-1460925895917-afdab827c52f?auto=format&fit=crop&w=1200&q=80",
    outputs: ["产能瓶颈定位", "牛鞭效应抑制方案", "现金流压力测试报告"]
  },
  {
    title: "供应商断供推演",
    desc: "模拟核心供应商突然破产、产能被锁定或重大质量事故，评估对交付链的级联冲击。",
    icon: markRaw(ShieldAlert),
    image: "https://images.unsplash.com/photo-1586528116311-ad8dd3c8310d?auto=format&fit=crop&w=1200&q=80",
    outputs: ["替代供应商切换时效", "安全库存消耗曲线", "客户订单分批交付预案"]
  },
  {
    title: "关键物流枢纽中断",
    desc: "模拟世界级港口罢工、运河封闭或核心中转机场停运，推演全球货物流的迂回能力。",
    icon: markRaw(PackageSearch),
    image: "https://images.unsplash.com/photo-1494412574643-ff11b0a5c1c3?auto=format&fit=crop&w=1200&q=80",
    outputs: ["替代路线时效对比", "滞留附加费估算", "多式联运切换方案"]
  },
  {
    title: "汇率与大宗商品波动",
    desc: "模拟人民币/美元剧烈波动或铜、锂等关键原材料暴涨，量化对采购成本和利润率的冲击。",
    icon: markRaw(BarChart3),
    image: "https://images.unsplash.com/photo-1611974789855-9c2a0a7236a3?auto=format&fit=crop&w=1200&q=80",
    outputs: ["成本敏感性矩阵", "套期保值策略建议", "替代材料/供应商比价"]
  }
]
</script>

<style scoped>
.carousel-track {
  scrollbar-width: none;
  -ms-overflow-style: none;
}
.carousel-track::-webkit-scrollbar {
  display: none;
}
</style>

