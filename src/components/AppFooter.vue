<template>
  <footer class="relative bg-[#0a0d16] text-[#8b93a3] pt-20 pb-9 text-[15px] mt-auto">
    <div class="absolute top-0 inset-x-0 h-px bg-gradient-to-r from-transparent via-[rgba(108,178,255,0.45)] to-transparent"></div>

    <div class="max-w-7xl mx-auto px-6 lg:px-8">
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-[1.9fr_1fr_1fr_1fr] gap-x-8 gap-y-12 lg:gap-14 pb-12 border-b border-white/10">

        <div class="flex flex-col">
          <RouterLink to="/" class="text-[19px] font-bold text-white mb-3 flex items-center gap-[9px]" aria-label="Home">
            <ImageWithFallback
              :src="logo2"
              alt="Logo"
              class="h-8 w-auto object-contain"
            />
          </RouterLink>
          <div class="text-[16px] font-semibold text-[#aab6cc] mb-5">让全球供应链，没有断链之忧</div>
          <p class="leading-[1.7] max-w-[340px] mb-6">
            从采购寻源到末端配送，从关税波动到航线中断——帮企业把供应链的不确定性，变成可量化、可管理、可优化的日常运营。
          </p>
          <div class="flex gap-3">
            <a href="#" aria-label="LinkedIn" class="w-[38px] h-[38px] rounded-[10px] flex items-center justify-center text-[15px] text-[#aab6cc] bg-white/5 border border-white/10 transition-all duration-[250ms] ease-out hover:bg-[rgba(46,151,255,0.16)] hover:text-white hover:border-[rgba(46,151,255,0.5)] hover:-translate-y-0.5">
              in
            </a>
            <a href="#" aria-label="X" class="w-[38px] h-[38px] rounded-[10px] flex items-center justify-center text-[15px] font-serif font-bold text-[#aab6cc] bg-white/5 border border-white/10 transition-all duration-[250ms] ease-out hover:bg-[rgba(46,151,255,0.16)] hover:text-white hover:border-[rgba(46,151,255,0.5)] hover:-translate-y-0.5">
              𝕏
            </a>
            <a href="mailto:hello@globalscm.com" aria-label="Email" class="w-[38px] h-[38px] rounded-[10px] flex items-center justify-center text-[#aab6cc] bg-white/5 border border-white/10 transition-all duration-[250ms] ease-out hover:bg-[rgba(46,151,255,0.16)] hover:text-white hover:border-[rgba(46,151,255,0.5)] hover:-translate-y-0.5">
              <svg class="w-[17px] h-[17px]" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
                <rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 4-10 8L2 4"/>
              </svg>
            </a>
            <a href="#" aria-label="Website" class="w-[38px] h-[38px] rounded-[10px] flex items-center justify-center text-[#aab6cc] bg-white/5 border border-white/10 transition-all duration-[250ms] ease-out hover:bg-[rgba(46,151,255,0.16)] hover:text-white hover:border-[rgba(46,151,255,0.5)] hover:-translate-y-0.5">
              <svg class="w-[17px] h-[17px]" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
                <circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/>
              </svg>
            </a>
          </div>
        </div>

        <div>
          <h5 class="text-white text-[18px] mb-5 font-medium">解决方案</h5>
          <ul class="space-y-0">
            <li class="py-[9px]"><RouterLink to="/smart-procurement" class="text-[#8b93a3] hover:text-white transition-colors duration-200">智慧采购</RouterLink></li>
            <li class="py-[9px]"><RouterLink to="/trusted-delivery" class="text-[#8b93a3] hover:text-white transition-colors duration-200">可信交付</RouterLink></li>
            <li class="py-[9px]"><RouterLink to="/decision-center" class="text-[#8b93a3] hover:text-white transition-colors duration-200">决策中枢</RouterLink></li>
          </ul>
        </div>

        <div>
          <h5 class="text-white text-[18px] mb-5 font-medium">平台能力</h5>
          <ul class="space-y-0">
            <li class="py-[9px]"><RouterLink to="/smart-procurement" class="text-[#8b93a3] hover:text-white transition-colors duration-200">智能寻源与采购</RouterLink></li>
            <li class="py-[9px]"><RouterLink to="/trusted-delivery" class="text-[#8b93a3] hover:text-white transition-colors duration-200">全链路追踪交付</RouterLink></li>
            <li class="py-[9px]"><RouterLink to="/decision-center" class="text-[#8b93a3] hover:text-white transition-colors duration-200">数据决策分析</RouterLink></li>
          </ul>
        </div>

        <div>
          <h5 class="text-white text-[18px] mb-5 font-medium">公司</h5>
          <ul class="space-y-0">
            <li class="py-[9px]"><a href="#" class="text-[#8b93a3] hover:text-white transition-colors duration-200">关于我们</a></li>
            <li class="py-[9px]"><a href="#" class="text-[#8b93a3] hover:text-white transition-colors duration-200">联系我们</a></li>
            <li class="py-[9px]"><a href="#" class="text-[#8b93a3] hover:text-white transition-colors duration-200">新闻资讯</a></li>
            <li class="py-[9px]"><a href="#" class="text-[#8b93a3] hover:text-white transition-colors duration-200">加入我们</a></li>
          </ul>
        </div>
      </div>

      <div class="flex flex-col md:flex-row justify-between items-center pt-[30px] text-[14px] text-[#6e6e73] flex-wrap gap-4">
        <span class="text-center md:text-left leading-relaxed">
          © 2026 全球供应链大平台. 保留所有权利.
          <span class="hidden md:inline"> | </span>
          <br class="md:hidden" />
          <a href="#" class="text-[#6e6e73] hover:text-white transition-colors duration-200 inline-block mt-1 md:mt-0">粤公网安备44010602010128号</a>
          <span class="mx-1.5 inline-block">|</span>
          <a href="#" class="text-[#6e6e73] hover:text-white transition-colors duration-200 inline-block mt-1 md:mt-0">粤ICP备17142036号-7</a>
        </span>
        <span class="inline-flex gap-4 flex-wrap justify-center">
          <a href="#" class="text-[#6e6e73] hover:text-white transition-colors duration-200">信息保护政策</a>
          <a href="#" class="text-[#6e6e73] hover:text-white transition-colors duration-200">用户协议</a>
          <a href="#" class="text-[#6e6e73] hover:text-white transition-colors duration-200">用户行为管理规范</a>
        </span>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { RouterLink } from 'vue-router'
import ImageWithFallback from '@/components/ImageWithFallback.vue'
import logo2 from '@/assets/logo-2.png'
</script>
