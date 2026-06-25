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
        <h1 v-motion :initial="{ opacity: 0, y: 30 }"
          :enter="{ opacity: 1, y: 0, transition: { duration: 800, delay: 100, ease: [0.16, 1, 0.3, 1] } }"
          class="text-5xl md:text-7xl lg:text-8xl font-bold tracking-tight text-white mb-8">
          数据驱动，决策有据
        </h1>
        <p v-motion :initial="{ opacity: 0, y: 30 }"
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

    <!-- ===== Core Capabilities (Bento Grid) ===== -->
    <section class="w-[85%] mx-auto px-6 md:px-8 py-12 md:py-24 mt-16">
      <div class="mb-16">
        <div class="text-sm font-bold text-slate-300 tracking-[0.3em] uppercase mb-4">Core Capabilities</div>
        <h2 class="text-4xl md:text-5xl font-bold tracking-tight text-slate-900 mb-4">四大核心能力</h2>
        <p class="text-xl text-slate-500 font-light">融合信号、预测变化、推演预案、自动响应，构建供应链决策完整闭环。</p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-6 auto-rows-[280px]">

        <div
          class="md:col-span-2 row-span-2 group relative overflow-hidden rounded-[2rem] bg-white border border-slate-100 shadow-sm hover:shadow-xl transition-all duration-700 ease-out p-8 md:p-12 flex flex-col justify-between">
          <div
            class="absolute top-0 right-0 w-96 h-96 bg-gradient-to-br from-blue-50 to-transparent rounded-full blur-3xl -z-10 opacity-50 group-hover:opacity-100 transition-opacity duration-700">
          </div>
          <div>
            <div
              class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full bg-blue-50 text-blue-600 text-sm font-semibold mb-6">
              <Globe class="w-4 h-4" /> 多维信号融合
            </div>
            <h3
              class="text-3xl md:text-4xl font-bold tracking-tight text-slate-900 mb-4 group-hover:text-blue-600 transition-colors">
              汇聚千维信号<br />洞察万变先机
            </h3>
            <p class="text-lg text-slate-500 leading-relaxed max-w-lg">
              直连全球地缘政治、气象雷达、港口卫星与金融市场数据源，构建秒级同步的供应链风险全景图，让黑天鹅无所遁形。
            </p>
          </div>
          <div class="mt-8 flex gap-4">
            <div class="flex-1 bg-slate-50 rounded-2xl p-4 border border-slate-100/50">
              <div class="text-xs font-semibold text-slate-400 mb-1 uppercase tracking-wider">地缘风险监控</div>
              <div class="text-2xl font-bold text-slate-800">200+</div>
              <div class="w-full h-1.5 bg-slate-200 rounded-full mt-3 overflow-hidden">
                <div class="h-full bg-blue-500 rounded-full w-[85%]"></div>
              </div>
            </div>
            <div class="flex-1 bg-slate-50 rounded-2xl p-4 border border-slate-100/50">
              <div class="text-xs font-semibold text-slate-400 mb-1 uppercase tracking-wider">数据源接入</div>
              <div class="text-2xl font-bold text-slate-800">50+</div>
              <div class="w-full h-1.5 bg-slate-200 rounded-full mt-3 overflow-hidden">
                <div class="h-full bg-indigo-500 rounded-full w-[90%]"></div>
              </div>
            </div>
          </div>
        </div>

        <div
          class="md:col-span-1 row-span-2 group relative overflow-hidden rounded-[2rem] bg-slate-900 text-white shadow-xl hover:shadow-2xl hover:shadow-indigo-500/20 transition-all duration-700 ease-out p-8 md:p-10 flex flex-col">
          <div
            class="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1551288049-bebda4e38f71?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&q=80&w=1080')] bg-cover bg-center opacity-10 group-hover:opacity-20 transition-opacity duration-700 mix-blend-luminosity">
          </div>
          <div class="absolute inset-0 bg-gradient-to-t from-slate-900 via-slate-900/80 to-slate-900/40"></div>
          <div class="relative z-10 flex-1">
            <div
              class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full bg-white/10 text-white text-sm font-semibold mb-6 backdrop-blur-md">
              <TrendingUp class="w-4 h-4" /> 智能预测引擎
            </div>
            <h3 class="text-2xl md:text-3xl font-bold tracking-tight mb-4">先于波动<br />做出决策</h3>
            <p class="text-slate-300 leading-relaxed mb-8">
              百亿参数供应链大模型，融合历史趋势、宏观指标与社交情绪信号，滚动预测需求、价格与交付风险，偏差实时自校正。
            </p>
          </div>
          <div class="relative z-10 space-y-3">
            <div class="bg-white/5 border border-white/10 rounded-2xl p-4 backdrop-blur-md">
              <div class="flex justify-between items-center mb-2"><span
                  class="text-sm font-medium text-slate-300">需求预测准确率</span><span
                  class="text-sm font-bold text-green-400">95.8%</span></div>
              <div class="w-full h-1 bg-white/10 rounded-full">
                <div class="h-full bg-green-400 rounded-full w-[95.8%]"></div>
              </div>
            </div>
            <div class="bg-white/5 border border-white/10 rounded-2xl p-4 backdrop-blur-md">
              <div class="flex justify-between items-center mb-2"><span
                  class="text-sm font-medium text-slate-300">模型自校正频率</span><span
                  class="text-sm font-bold text-blue-400">实时</span></div>
              <div class="w-full h-1 bg-white/10 rounded-full">
                <div class="h-full bg-blue-400 rounded-full w-full"></div>
              </div>
            </div>
          </div>
        </div>

        <div
          class="md:col-span-1 row-span-1 group relative overflow-hidden rounded-[2rem] bg-white border border-slate-100 shadow-sm hover:shadow-xl transition-all duration-700 ease-out p-8 flex flex-col justify-center">
          <div
            class="w-12 h-12 rounded-2xl bg-indigo-50 text-indigo-600 flex items-center justify-center mb-6 group-hover:scale-110 transition-transform duration-500">
            <Activity class="w-6 h-6" />
          </div>
          <h3
            class="text-xl font-bold tracking-tight text-slate-900 mb-3 group-hover:text-indigo-600 transition-colors">
            仿真推演平台</h3>
          <p class="text-sm text-slate-500 leading-relaxed">
            一键启动数字沙盘，秒级评估"如果 X 发生会怎样"。<br />
            <strong class="text-slate-700 font-semibold">断供 → 替代方案 / 爆单 → 产能调配 / 汇率暴涨 → 对冲策略。</strong>
          </p>
        </div>

        <div
          class="md:col-span-2 row-span-1 group relative overflow-hidden rounded-[2rem] bg-white border border-slate-100 shadow-sm hover:shadow-xl transition-all duration-700 ease-out p-8 flex flex-col md:flex-row items-center gap-8">
          <div class="flex-1">
            <div
              class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full bg-emerald-50 text-emerald-700 text-sm font-semibold mb-4">
              <Zap class="w-4 h-4" /> 自动决策中枢
            </div>
            <h3
              class="text-2xl font-bold tracking-tight text-slate-900 mb-3 group-hover:text-emerald-600 transition-colors">
              从预警到执行，无人值守</h3>
            <p class="text-slate-500 leading-relaxed">当风险超阈值时自动触发预案，决策结果直连业务系统生成调整指令，实现感知→分析→执行的智能闭环。</p>
          </div>
          <div class="w-full md:w-64 bg-slate-50 rounded-2xl p-5 border border-slate-100 shrink-0">
            <div class="flex items-center justify-between text-sm mb-3"><span class="text-slate-500">自动响应延迟</span><span
                class="font-bold text-slate-900">&lt; 3s</span></div>
            <div
              class="flex items-center gap-2 text-xs font-medium text-emerald-600 bg-emerald-50 px-3 py-2 rounded-lg">
              <CheckCircle2 class="w-4 h-4" /> 预案已就绪
            </div>
          </div>
        </div>

      </div>
    </section>

    <!-- ===== Scenario Simulation ===== -->
    <section class="w-full bg-[#Fbfbfd] py-32 relative overflow-hidden">
      <div class="max-w-[90rem] mx-auto px-6 lg:px-8 relative z-10">
        <div class="text-center mb-20 max-w-4xl mx-auto">
          <h2 class="text-5xl md:text-6xl font-bold tracking-tight text-slate-900 mb-6">
            沙盘推演，未雨绸缪
          </h2>
          <p class="text-xl md:text-2xl text-slate-500 font-light leading-relaxed">
            六大供应链风险场景模拟。<br/>在真正的危机发生前，预演每一个可能，生成万全对策。
          </p>
        </div>

        <!-- Carousel for Scenarios -->
        <div class="relative">
          <div ref="carouselRef" @scroll="onScroll"
            class="flex gap-6 overflow-x-auto snap-x snap-mandatory carousel-track pb-12 pt-4 px-4 -mx-4">
            <div v-for="(scenario, idx) in scenarios" :key="idx"
              class="snap-start shrink-0 w-[85vw] md:w-[400px] lg:w-[420px] h-[600px] relative group rounded-[3rem] overflow-hidden shadow-[0_10px_40px_rgba(0,0,0,0.08)] hover:shadow-[0_20px_60px_rgba(0,0,0,0.15)] transition-all duration-700 cursor-pointer">
              
              <!-- Background Image -->
              <img :src="scenario.image" :alt="scenario.title" class="absolute inset-0 w-full h-full object-cover group-hover:scale-105 transition-transform duration-1000 ease-[cubic-bezier(0.16,1,0.3,1)]" />
              
              <!-- Gradient Overlay -->
              <div class="absolute inset-0 bg-gradient-to-t from-black/95 via-black/40 to-transparent"></div>
              
              <!-- Content Area -->
              <div class="absolute inset-x-0 bottom-0 p-8 md:p-10 flex flex-col justify-end h-full">
                <!-- Text Content -->
                <h3 class="text-3xl font-bold text-white mb-3 tracking-tight">{{ scenario.title }}</h3>
                <p class="text-slate-300 font-light leading-relaxed mb-6">{{ scenario.desc }}</p>
                
                <!-- Sleek Outputs Box -->
                <div class="bg-white/10 backdrop-blur-xl rounded-2xl p-5 border border-white/20">
                  <div class="text-[11px] text-white/60 font-semibold mb-3 flex items-center gap-2 uppercase tracking-widest">
                    <Activity class="w-3.5 h-3.5" /> 预案产出 (Outputs)
                  </div>
                  <ul class="space-y-2.5">
                    <li v-for="(item, i) in scenario.outputs" :key="i" class="flex items-start text-sm text-white/90 font-light leading-relaxed">
                      <CheckCircle2 class="w-4 h-4 text-white/40 mr-2.5 shrink-0 mt-0.5" />
                      {{ item }}
                    </li>
                  </ul>
                </div>
              </div>
            </div>
          </div>

          <!-- Prev / Next Buttons (Floating outside) -->
          <button @click="prev"
            class="hidden md:flex absolute -left-6 top-1/2 -translate-y-1/2 w-14 h-14 rounded-full bg-white/80 backdrop-blur-lg border border-slate-200/50 shadow-lg items-center justify-center text-slate-700 hover:scale-105 hover:bg-white transition-all disabled:opacity-0 disabled:scale-95 disabled:pointer-events-none z-20"
            :disabled="currentIndex === 0">
            <ChevronLeft class="w-6 h-6" />
          </button>
          <button @click="next"
            class="hidden md:flex absolute -right-6 top-1/2 -translate-y-1/2 w-14 h-14 rounded-full bg-white/80 backdrop-blur-lg border border-slate-200/50 shadow-lg items-center justify-center text-slate-700 hover:scale-105 hover:bg-white transition-all disabled:opacity-0 disabled:scale-95 disabled:pointer-events-none z-20"
            :disabled="currentIndex >= maxIndex">
            <ChevronRight class="w-6 h-6" />
          </button>

          <!-- Dots (Pill style) -->
          <div class="flex justify-center gap-2 mt-8">
            <button v-for="(_, idx) in slidesCount" :key="idx" @click="goTo(idx)"
              class="h-2 rounded-full transition-all duration-300"
              :class="idx === currentIndex ? 'bg-slate-800 w-8' : 'bg-slate-300 w-2 hover:bg-slate-400'" />
          </div>
        </div>
      </div>
    </section>

    <!-- ===== Decision Loop ===== -->
    <section class="w-full mx-auto px-6 md:px-8 py-24 md:py-32 bg-[#Fbfbfd]">
      <div class="text-center mb-24">
        <div class="text-3xl md:text-5xl font-bold tracking-widest text-slate-200 mb-4 uppercase">Decision Loop</div>
        <h2 class="text-2xl md:text-3xl font-medium text-slate-500">感知 · 分析 · 决策 · 执行 — 四步智能闭环，从洞察到行动零延迟</h2>
      </div>
      <div class="max-w-[85rem] mx-auto grid grid-cols-1 md:grid-cols-2 gap-6 md:gap-8">
        <div
          class="group relative bg-white rounded-[2.5rem] p-10 md:p-14 overflow-hidden shadow-[0_8px_30px_rgb(0,0,0,0.04)] hover:shadow-[0_20px_40px_rgb(0,0,0,0.08)] transition-all duration-700 flex flex-col h-[500px]">
          <div class="relative z-10 w-full max-w-md">
            <div class="text-sm font-bold tracking-widest text-slate-400 uppercase mb-4">Step 1 — Perception</div>
            <h3 class="text-3xl md:text-4xl font-bold tracking-tight text-slate-900 mb-4">全域感知</h3>
            <p class="text-lg text-slate-500 font-light leading-relaxed">跨越孤岛。实时汇聚订单、库存、物流与宏观数据流，毫秒级捕捉每一个微小变化，消除供应链盲区。
            </p>
          </div>
          <div
            class="absolute bottom-0 right-0 w-[80%] h-[60%] translate-y-10 translate-x-10 group-hover:translate-y-0 group-hover:translate-x-0 transition-transform duration-700 ease-[cubic-bezier(0.16,1,0.3,1)]">
            <img src="https://images.unsplash.com/photo-1558494949-ef010cbdcc31?auto=format&fit=crop&q=80&w=1200"
              alt="Perception" class="w-full h-full object-cover rounded-tl-[2rem] shadow-2xl" />
            <div class="absolute inset-0 bg-gradient-to-t from-white via-transparent to-transparent mix-blend-screen">
            </div>
          </div>
        </div>
        <div
          class="group relative bg-slate-900 rounded-[2.5rem] p-10 md:p-14 overflow-hidden shadow-[0_8px_30px_rgb(0,0,0,0.08)] hover:shadow-[0_20px_40px_rgb(0,0,0,0.15)] transition-all duration-700 flex flex-col h-[500px]">
          <div class="relative z-10 w-full max-w-md">
            <div class="text-sm font-bold tracking-widest text-blue-400 uppercase mb-4">Step 2 — Analysis</div>
            <h3 class="text-3xl md:text-4xl font-bold tracking-tight text-white mb-4">智能分析</h3>
            <p class="text-lg text-slate-400 font-light leading-relaxed">
              透过表象看本质。百亿参数大模型深度挖掘数据关联，精准识别异常背后的根因，量化潜在风险与业务影响。</p>
          </div>
          <div
            class="absolute bottom-0 right-0 w-[75%] h-[65%] rounded-tl-[2rem] overflow-hidden translate-y-8 translate-x-8 group-hover:translate-y-0 group-hover:scale-105 transition-transform duration-700 ease-[cubic-bezier(0.16,1,0.3,1)]">
            <img src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?auto=format&fit=crop&q=80&w=1200"
              alt="Analysis" class="w-full h-full object-cover opacity-80 mix-blend-luminosity" />
            <div class="absolute inset-0 bg-gradient-to-tr from-slate-900 via-transparent to-blue-900/40"></div>
          </div>
        </div>
        <div
          class="group relative bg-gradient-to-br from-blue-50 to-indigo-50/30 rounded-[2.5rem] p-10 md:p-14 overflow-hidden shadow-[0_8px_30px_rgb(0,0,0,0.04)] hover:shadow-[0_20px_40px_rgb(0,0,0,0.08)] transition-all duration-700 flex flex-col h-[500px]">
          <div class="relative z-10 w-full max-w-md">
            <div class="text-sm font-bold tracking-widest text-indigo-500 uppercase mb-4">Step 3 — Decision</div>
            <h3 class="text-3xl md:text-4xl font-bold tracking-tight text-slate-900 mb-4">最优决策</h3>
            <p class="text-lg text-slate-600 font-light leading-relaxed">多目标约束下的沙盘推演。在成本、时效、风险间自动寻找最优解，秒级输出可替代方案与调度策略。
            </p>
          </div>
          <div
            class="absolute bottom-0 right-0 w-[80%] h-[70%] translate-y-12 translate-x-12 group-hover:-translate-y-2 group-hover:-translate-x-2 transition-transform duration-700 ease-[cubic-bezier(0.16,1,0.3,1)]">
            <img src="https://images.unsplash.com/photo-1451187580459-43490279c0fa?auto=format&fit=crop&q=80&w=1200"
              alt="Decision" class="w-full h-full object-cover rounded-tl-[2rem] shadow-2xl opacity-90" />
          </div>
        </div>
        <div
          class="group relative bg-white rounded-[2.5rem] p-10 md:p-14 overflow-hidden shadow-[0_8px_30px_rgb(0,0,0,0.04)] hover:shadow-[0_20px_40px_rgb(0,0,0,0.08)] transition-all duration-700 flex flex-col h-[500px]">
          <div class="relative z-10 w-full max-w-md">
            <div class="text-sm font-bold tracking-widest text-emerald-500 uppercase mb-4">Step 4 — Execution</div>
            <h3 class="text-3xl md:text-4xl font-bold tracking-tight text-slate-900 mb-4">无缝执行</h3>
            <p class="text-lg text-slate-500 font-light leading-relaxed">告别手动搬运。决策结果通过 API
              直连业务系统，自动生成采购单、排程计划与调拨指令，一气呵成。</p>
          </div>
          <div
            class="absolute bottom-0 right-0 w-[70%] h-[60%] translate-y-8 translate-x-8 group-hover:scale-105 group-hover:rotate-2 transition-transform duration-700 ease-[cubic-bezier(0.16,1,0.3,1)]">
            <img src="https://images.unsplash.com/photo-1518770660439-4636190af475?auto=format&fit=crop&q=80&w=1200"
              alt="Execution"
              class="w-full h-full object-cover rounded-tl-[2rem] shadow-2xl opacity-90 mix-blend-luminosity sepia-[0.2]" />
          </div>
        </div>
      </div>
    </section>

    <!-- ===== AI Command Center ===== -->
    <section class="w-full mx-auto px-6 md:px-8 py-16 md:py-24 bg-slate-900 text-white relative overflow-hidden mt-16">
      <div
        class="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1451187580459-43490279c0fa?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&q=80&w=2000')] bg-cover bg-center opacity-10 mix-blend-screen">
      </div>
      <div class="absolute inset-0 bg-gradient-to-b from-slate-900 via-slate-900/90 to-slate-900"></div>
      <div class="max-w-7xl mx-auto relative z-10">
        <div class="text-center mb-16">
          <div
            class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-blue-500/10 border border-blue-500/20 text-blue-400 text-sm font-semibold mb-6 backdrop-blur-md">
            <span class="relative flex h-2 w-2"><span
                class="animate-ping absolute inline-flex h-full w-full rounded-full bg-blue-400 opacity-75"></span><span
                class="relative inline-flex rounded-full h-2 w-2 bg-blue-500"></span></span>
            LIVE COMMAND CENTER
          </div>
          <h2 class="text-4xl md:text-5xl font-bold tracking-tight mb-6">智能指挥，对话即决策</h2>
          <p class="text-xl text-slate-400 font-light max-w-3xl mx-auto">用自然语言直接询问供应链状态与经营数据，AI
            实时分析并输出可执行策略，让复杂决策像聊天一样简单。</p>
        </div>
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
          <div
            class="lg:col-span-4 bg-black/40 border border-white/10 rounded-[2rem] p-6 backdrop-blur-xl flex flex-col h-[600px] shadow-2xl relative overflow-hidden group">
            <div
              class="absolute top-0 right-0 w-64 h-64 bg-blue-500/10 rounded-full blur-[80px] pointer-events-none group-hover:bg-blue-500/20 transition-colors duration-700">
            </div>
            <div class="flex justify-between items-center mb-6 pb-4 border-b border-white/10 relative z-10">
              <div class="flex items-center gap-3">
                <div
                  class="w-10 h-10 rounded-xl bg-gradient-to-br from-blue-500 to-indigo-600 flex items-center justify-center shadow-[0_0_15px_rgba(59,130,246,0.3)]">
                  <Cpu class="w-5 h-5 text-white" />
                </div>
                <div>
                  <h3 class="font-bold text-slate-100 tracking-wide">AI 决策引擎</h3>
                  <div class="flex items-center gap-1.5 mt-0.5"><span class="relative flex h-2 w-2"><span
                        class="animate-ping absolute inline-flex h-full w-full rounded-full bg-emerald-400 opacity-75"></span><span
                        class="relative inline-flex rounded-full h-2 w-2 bg-emerald-500"></span></span><span
                      class="text-[10px] text-emerald-400 font-mono uppercase tracking-wider">System Online</span></div>
                </div>
              </div>
              <div
                class="px-2.5 py-1 rounded-lg bg-white/5 border border-white/10 text-[10px] text-slate-400 font-mono">
                ID: NODE-77A</div>
            </div>
            <div class="flex-1 overflow-y-auto space-y-6 pr-2 custom-scrollbar relative z-10 pb-4">
              <div class="flex gap-3 w-11/12">
                <div
                  class="w-8 h-8 rounded-full bg-red-500/20 border border-red-500/30 flex items-center justify-center shrink-0 shadow-[0_0_10px_rgba(239,68,68,0.2)]">
                  <AlertTriangle class="w-4 h-4 text-red-400" />
                </div>
                <div class="space-y-1.5 w-full">
                  <div class="text-[10px] text-slate-500 font-mono ml-1 flex items-center gap-2">
                    <span>SYSTEM_ALERT</span><span class="w-1 h-1 rounded-full bg-slate-600"></span><span>08:42
                      AM</span></div>
                  <div
                    class="bg-gradient-to-br from-red-500/10 to-transparent border border-red-500/20 rounded-2xl rounded-tl-none p-4 text-sm text-red-100/90 leading-relaxed">
                    预测到下季度欧洲市场核心 <span class="font-bold text-red-400">MCU 组件需求将激增 40%</span>，按现有采购计划，库存将在 <span
                      class="font-bold text-red-400">15 天后击穿</span>。是否需要生成产能保障策略？</div>
                </div>
              </div>
              <div class="flex gap-3 w-10/12 self-end ml-auto flex-row-reverse">
                <div
                  class="w-8 h-8 rounded-full bg-slate-800 border border-slate-600 flex items-center justify-center shrink-0">
                  <span class="text-[10px] font-black text-slate-300">CMD</span></div>
                <div class="space-y-1.5 w-full flex flex-col items-end">
                  <div class="text-[10px] text-slate-500 font-mono mr-1 flex items-center gap-2"><span>08:45
                      AM</span><span class="w-1 h-1 rounded-full bg-slate-600"></span><span>DIRECTOR_INPUT</span></div>
                  <div
                    class="bg-gradient-to-r from-blue-600 to-indigo-600 shadow-[0_5px_15px_rgba(37,99,235,0.2)] rounded-2xl rounded-tr-none p-4 text-sm text-white leading-relaxed text-left w-full">
                    列出备选方案，并对比调拨与紧急采购的资金占用。</div>
                </div>
              </div>
              <div class="flex gap-3 w-11/12">
                <div
                  class="w-8 h-8 rounded-full bg-blue-500/20 border border-blue-500/30 flex items-center justify-center shrink-0 shadow-[0_0_10px_rgba(59,130,246,0.2)]">
                  <Bot class="w-4 h-4 text-blue-400" />
                </div>
                <div class="space-y-1.5 w-full">
                  <div class="text-[10px] text-slate-500 font-mono ml-1 flex items-center gap-2">
                    <span>AI_ANALYSIS</span><span class="w-1 h-1 rounded-full bg-slate-600"></span><span>08:46 AM</span>
                  </div>
                  <div
                    class="bg-blue-500/5 border border-blue-500/20 rounded-2xl rounded-tl-none p-4 text-sm text-slate-300 space-y-4">
                    <p class="flex items-center gap-2 text-blue-300 font-medium">
                      <Zap class="w-4 h-4 text-blue-400" /> 已为您测算 2 套最优方案：
                    </p>
                    <div
                      class="bg-[#0a0f1c] rounded-xl p-4 border border-emerald-500/40 relative overflow-hidden group/opt shadow-[0_0_15px_rgba(16,185,129,0.1)]">
                      <div
                        class="absolute inset-0 bg-emerald-500/5 group-hover/opt:bg-emerald-500/10 transition-colors">
                      </div>
                      <div class="relative">
                        <div class="flex justify-between items-center mb-3"><span
                            class="font-bold text-emerald-400 flex items-center gap-2">
                            <CheckCircle2 class="w-4 h-4" /> 方案 A：亚太仓调拨
                          </span><span
                            class="text-[10px] px-2 py-1 rounded bg-emerald-500/20 text-emerald-300 border border-emerald-500/30 tracking-wide">最优选</span>
                        </div>
                        <div class="grid grid-cols-2 gap-3 mt-3">
                          <div class="bg-white/5 border border-white/5 rounded-lg p-2.5">
                            <div class="text-[10px] text-slate-400 mb-1">时效预估</div>
                            <div class="text-xs font-mono text-white">5-7 DAYS</div>
                          </div>
                          <div class="bg-white/5 border border-white/5 rounded-lg p-2.5">
                            <div class="text-[10px] text-slate-400 mb-1">成本变化</div>
                            <div class="text-xs font-mono text-emerald-400">+3.5% ($12K)</div>
                          </div>
                        </div>
                      </div>
                    </div>
                    <div class="bg-[#0a0f1c]/50 rounded-xl p-4 border border-white/10 opacity-80">
                      <div class="flex justify-between items-center mb-3"><span class="font-bold text-slate-400">方案
                          B：现货紧急寻源</span></div>
                      <div class="grid grid-cols-2 gap-3 mt-3">
                        <div class="bg-white/5 border border-white/5 rounded-lg p-2.5">
                          <div class="text-[10px] text-slate-400 mb-1">时效预估</div>
                          <div class="text-xs font-mono text-slate-300">10-12 DAYS</div>
                        </div>
                        <div class="bg-white/5 border border-white/5 rounded-lg p-2.5">
                          <div class="text-[10px] text-slate-400 mb-1">成本变化</div>
                          <div class="text-xs font-mono text-red-400">+18.0% ($65K)</div>
                        </div>
                      </div>
                    </div>
                    <div class="pt-2"><button
                        class="w-full py-3 rounded-xl bg-gradient-to-r from-blue-600 to-blue-500 text-white text-sm font-semibold tracking-wide transition-all shadow-[0_0_20px_rgba(37,99,235,0.4)] pointer-events-none flex items-center justify-center gap-2">
                        <CheckCircle2 class="w-4 h-4" /> 确认下发方案 A 指令
                      </button></div>
                  </div>
                </div>
              </div>
            </div>
            <div class="mt-2 pt-5 border-t border-white/10 relative select-none pointer-events-none z-10">
              <div
                class="w-full bg-[#0a0f1c] border border-white/10 rounded-xl py-3.5 px-4 flex items-center justify-between shadow-inner">
                <div class="flex items-center gap-3"><span
                    class="text-blue-500 font-mono text-lg leading-none font-bold">></span><span
                    class="text-xs font-mono text-slate-400 tracking-wider flex items-center uppercase">Awaiting_Command<span
                      class="animate-pulse ml-2 w-1.5 h-3.5 bg-blue-500 rounded-sm inline-block"></span></span></div>
                <div class="flex gap-1.5 opacity-50">
                  <div class="w-1.5 h-1.5 rounded-full bg-slate-500"></div>
                  <div class="w-1.5 h-1.5 rounded-full bg-slate-500"></div>
                  <div class="w-1.5 h-1.5 rounded-full bg-slate-500"></div>
                </div>
              </div>
            </div>
          </div>
          <div
            class="lg:col-span-8 bg-black/40 border border-white/10 rounded-[2rem] p-6 backdrop-blur-xl relative overflow-hidden h-[600px] flex flex-col">
            <div class="flex justify-between items-center mb-6">
              <h3 class="font-semibold text-slate-200 text-lg">全局供需与库存态势图</h3>
              <div class="flex gap-2"><span
                  class="px-3 py-1 rounded-full bg-green-500/20 text-green-400 text-xs border border-green-500/30">供需平衡
                  92%</span><span
                  class="px-3 py-1 rounded-full bg-yellow-500/20 text-yellow-400 text-xs border border-yellow-500/30">库存预警
                  5项</span><span
                  class="px-3 py-1 rounded-full bg-indigo-500/20 text-indigo-400 text-xs border border-indigo-500/30">产线高负荷
                  2项</span></div>
            </div>
            <div class="flex-1 relative rounded-xl overflow-hidden border border-white/5 bg-slate-900/50">
              <img
                src="https://images.unsplash.com/photo-1524661135-423995f22d0b?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&q=80&w=1080"
                alt="Dashboard" class="absolute inset-0 w-full h-full object-cover opacity-30 mix-blend-luminosity" />
              <div v-for="node in mapNodes" :key="node.id" @click="activeNode = node"
                class="absolute w-4 h-4 rounded-full cursor-pointer z-20 group transition-transform hover:scale-125"
                :class="node.colorBase"
                :style="`top: ${node.top}; left: ${node.left}; box-shadow: 0 0 15px ${node.shadow};`">
                <div :class="['absolute inset-0 rounded-full animate-ping opacity-75', node.colorPing]"></div>
                <div
                  :class="['absolute -top-7 left-1/2 -translate-x-1/2 text-[10px] font-bold bg-black/50 px-2 py-0.5 rounded whitespace-nowrap pointer-events-none transition-all', node.colorText, activeNode.id === node.id ? 'opacity-100 scale-110' : 'opacity-80 group-hover:opacity-100']">
                  {{ node.name }} - {{ node.status }}</div>
                <div v-if="activeNode.id === node.id"
                  class="absolute -inset-2 rounded-full border border-white/50 animate-[spin_3s_linear_infinite]"></div>
              </div>
              <svg class="absolute inset-0 w-full h-full pointer-events-none"
                style="filter: drop-shadow(0 0 4px rgba(59,130,246,0.5));">
                <path d="M 65% 35% Q 55% 20% 45% 25%" fill="none" stroke="rgba(16,185,129,0.6)" stroke-width="2"
                  stroke-dasharray="4 4" class="animate-[dash_15s_linear_infinite]" />
                <path d="M 65% 35% Q 45% 50% 25% 45%" fill="none" stroke="rgba(59,130,246,0.6)" stroke-width="2"
                  stroke-dasharray="4 4" class="animate-[dash_15s_linear_infinite]" />
              </svg>
              <transition enter-active-class="transition duration-300 ease-out"
                enter-from-class="transform translate-y-4 opacity-0"
                enter-to-class="transform translate-y-0 opacity-100"
                leave-active-class="transition duration-200 ease-in"
                leave-from-class="transform translate-y-0 opacity-100"
                leave-to-class="transform translate-y-4 opacity-0" mode="out-in">
                <div :key="activeNode.id"
                  class="absolute bottom-4 right-4 bg-black/70 backdrop-blur-xl border border-white/10 rounded-xl p-5 w-72 z-30 shadow-2xl">
                  <div class="flex items-center gap-2 mb-3">
                    <div :class="['w-2 h-2 rounded-full animate-pulse', activeNode.colorBase]"></div>
                    <div class="text-sm font-semibold text-white">{{ activeNode.panelTitle }}</div>
                  </div>
                  <div class="text-xs text-slate-400 mb-4">{{ activeNode.desc }}</div>
                  <div class="space-y-3">
                    <div v-for="(metric, idx) in activeNode.metrics" :key="idx" class="relative">
                      <div class="flex justify-between items-end mb-1.5">
                        <div class="text-xs text-slate-400">{{ metric.label }}</div>
                        <div :class="['text-sm font-bold', metric.valueColor]">{{ metric.value }}</div>
                      </div>
                      <div v-if="metric.progress" class="w-full bg-white/10 h-1.5 rounded-full overflow-hidden">
                        <div :class="['h-full rounded-full', metric.barColor]" :style="{ width: metric.progress }">
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </transition>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== CTA ===== -->
    <section class="w-full bg-white py-32 md:py-48 overflow-hidden relative">
      <div class="max-w-4xl mx-auto px-6 text-center relative z-10">
        <div
          class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-slate-100 text-slate-600 text-xs font-semibold tracking-widest uppercase mb-8">
          Next Generation SCM</div>
        <h2 class="text-5xl md:text-7xl font-bold tracking-tight text-slate-900 mb-8 leading-[1.1]">准备好让您的供应链<br /><span
            class="text-transparent bg-clip-text bg-gradient-to-r from-blue-600 to-indigo-500">拥有思考能力了吗？</span></h2>
        <p class="text-xl md:text-2xl text-slate-500 font-light max-w-2xl mx-auto mb-14 leading-relaxed">
          体验前所未有的供应链管理方式。<br class="hidden md:block" />从被动应对到主动预测，一切尽在掌握。</p>
        <div class="flex flex-col sm:flex-row items-center justify-center gap-4">
          <RouterLink to="/join"
            class="w-full sm:w-auto px-8 py-4 rounded-full bg-slate-900 text-white font-medium text-lg hover:bg-slate-800 hover:scale-105 transition-all duration-300 flex items-center justify-center group shadow-xl shadow-slate-900/20">
            免费申请演示</RouterLink>
          <RouterLink to="/contact"
            class="w-full sm:w-auto px-8 py-4 rounded-full bg-white text-slate-900 font-medium text-lg border border-slate-200 hover:bg-slate-50 hover:border-slate-300 transition-all duration-300 flex items-center justify-center group">
            联系解决方案专家
            <ArrowRight
              class="w-5 h-5 ml-2 text-slate-400 group-hover:translate-x-1 group-hover:text-slate-900 transition-all" />
          </RouterLink>
        </div>
      </div>
      <div
        class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[800px] bg-gradient-to-tr from-blue-50 to-indigo-50/50 rounded-full blur-[100px] -z-10 pointer-events-none">
      </div>
    </section>

  </div>
</template>

<script setup>
import { markRaw, ref, computed, onMounted, onUnmounted } from 'vue'
import { RouterLink } from 'vue-router'
import {
  BarChart3, TrendingUp, AlertTriangle, PackageSearch,
  ShoppingCart, Factory, ArrowRight, ShieldAlert, Target,
  CheckCircle2, Bot, Send, Globe, ChevronLeft, ChevronRight,
  Cpu, Zap, Activity
} from 'lucide-vue-next'
import ImageWithFallback from '@/components/ImageWithFallback.vue'

const carouselRef = ref(null)
const currentIndex = ref(0)
const slidesPerView = ref(3)

const mapNodes = ref([
  { id: 'apac', name: '亚太总仓', top: '35%', left: '65%', colorBase: 'bg-emerald-500', colorPing: 'bg-emerald-400', colorText: 'text-emerald-300', shadow: 'rgba(16,185,129,1)', status: '库存充裕', panelTitle: '运营监控：亚太总仓', desc: '核心零部件储备充足。', metrics: [{ label: '当前库存量', value: '1,250,000 件', valueColor: 'text-emerald-400', progress: '90%', barColor: 'bg-emerald-500' }] },
  { id: 'na', name: '北美组装中心', top: '45%', left: '25%', colorBase: 'bg-yellow-500', colorPing: 'bg-yellow-400', colorText: 'text-yellow-300', shadow: 'rgba(234,179,8,1)', status: '产能告急', panelTitle: '产能预警：北美组装中心', desc: '订单量激增，产线负荷已近极限。', metrics: [{ label: '产线负荷率', value: '98.5%', valueColor: 'text-yellow-400', progress: '98.5%', barColor: 'bg-yellow-500' }] },
  { id: 'eu', name: '欧洲工厂', top: '25%', left: '45%', colorBase: 'bg-red-500', colorPing: 'bg-red-400', colorText: 'text-red-300', shadow: 'rgba(239,68,68,1)', status: 'MCU缺口', panelTitle: '焦点预警：欧洲区产线', desc: 'T-200 订单激增，核心物料库配比失衡。', metrics: [{ label: '预计缺口', value: '50,000 件', valueColor: 'text-red-400', progress: '85%', barColor: 'bg-red-500' }] }
])
const activeNode = ref(mapNodes.value[2])

const maxIndex = computed(() => Math.max(0, scenarios.length - slidesPerView.value))
const slidesCount = computed(() => Math.max(1, scenarios.length - slidesPerView.value + 1))

function getCardWidth() { const card = carouselRef.value?.children[0]; return card ? card.offsetWidth + 24 : 300 }
function scrollToCard(index) { const w = getCardWidth(); carouselRef.value?.scrollTo({ left: index * w, behavior: 'smooth' }) }
function prev() { if (currentIndex.value > 0) { currentIndex.value--; scrollToCard(currentIndex.value) } }
function next() { if (currentIndex.value < maxIndex.value) { currentIndex.value++; scrollToCard(currentIndex.value) } }
function goTo(idx) { currentIndex.value = Math.min(idx, maxIndex.value); scrollToCard(currentIndex.value) }
function onScroll() { const w = getCardWidth(); if (!w || !carouselRef.value) return; const idx = Math.round(carouselRef.value.scrollLeft / w); currentIndex.value = Math.min(idx, maxIndex.value) }
function updateSlides() { slidesPerView.value = window.innerWidth >= 1024 ? 3 : window.innerWidth >= 768 ? 2 : 1; if (currentIndex.value > maxIndex.value) currentIndex.value = maxIndex.value }
onMounted(() => { updateSlides(); window.addEventListener('resize', updateSlides) })
onUnmounted(() => { window.removeEventListener('resize', updateSlides) })

const kpis = [
  { title: "库存周转提升", value: "+32%", icon: markRaw(PackageSearch) },
  { title: "预测准确率", value: "95.8%", icon: markRaw(Target) },
  { title: "补货效率提升", value: "4x", icon: markRaw(ShoppingCart) },
  { title: "排产优化节省", value: "-45%", icon: markRaw(Factory) }
]

const scenarios = [
  { title: "地缘政治冲突模拟", desc: "模拟特定海峡封锁或关税突增对全局交付成本与时效的影响，提前锁定替代产能。", icon: markRaw(Globe), image: "https://images.unsplash.com/photo-1586528116311-ad8dd3c8310d?auto=format&fit=crop&w=1200&q=80", outputs: ["航线重路由方案", "关税成本对冲策略", "备用供应商激活清单"] },
  { title: "极端天气灾害推演", desc: "结合全球气象数据，预测台风、洪涝对关键港口及核心物料产区的破坏程度。", icon: markRaw(AlertTriangle), image: "https://images.unsplash.com/photo-1470071459604-3b5ec3a7fe05?auto=format&fit=crop&w=1200&q=80", outputs: ["安全库存动态调拨", "受灾节点订单转移", "物流延误客户预警"] },
  { title: "需求暴增/骤降测试", desc: "模拟大促爆单或黑天鹅事件导致的需求断崖，测试当前产能弹性和库存缓冲能力。", icon: markRaw(TrendingUp), image: "https://images.unsplash.com/photo-1460925895917-afdab827c52f?auto=format&fit=crop&w=1200&q=80", outputs: ["产能瓶颈定位", "牛鞭效应抑制方案", "现金流压力测试报告"] },
  { title: "供应商断供推演", desc: "模拟核心供应商突然破产、产能被锁定或重大质量事故，评估对交付链的级联冲击。", icon: markRaw(ShieldAlert), image: "https://images.unsplash.com/photo-1586528116311-ad8dd3c8310d?auto=format&fit=crop&w=1200&q=80", outputs: ["替代供应商切换时效", "安全库存消耗曲线", "客户订单分批交付预案"] },
  { title: "关键物流枢纽中断", desc: "模拟世界级港口罢工、运河封闭或核心中转机场停运，推演全球货物流的迂回能力。", icon: markRaw(PackageSearch), image: "https://images.unsplash.com/photo-1494412574643-ff11b0a5c1c3?auto=format&fit=crop&w=1200&q=80", outputs: ["替代路线时效对比", "滞留附加费估算", "多式联运切换方案"] },
  { title: "汇率与大宗商品波动", desc: "模拟人民币/美元剧烈波动或铜、锂等关键原材料暴涨，量化对采购成本和利润率的冲击。", icon: markRaw(BarChart3), image: "https://images.unsplash.com/photo-1611974789855-9c2a0a7236a3?auto=format&fit=crop&w=1200&q=80", outputs: ["成本敏感性矩阵", "套期保值策略建议", "替代材料/供应商比价"] }
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
