<template>
  <div class="min-h-screen bg-slate-50 flex flex-col">
    <!-- Hero Section -->
    <div class="relative pt-32 pb-20 lg:pt-48 lg:pb-32 overflow-hidden bg-slate-900 text-white">
      <div class="absolute inset-0 overflow-hidden">
        <ImageWithFallback
          src="https://images.unsplash.com/photo-1639322537228-f710d846310a?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHxnbG9iYWwlMjBidXNpbmVzcyUyMG5ldHdvcmslMjBzdXBwbHklMjBjaGFpbnxlbnwxfHx8fDE3ODIyOTE0NjN8MA&ixlib=rb-4.1.0&q=80&w=1080"
          class="w-full h-full object-cover opacity-30 mix-blend-overlay"
          alt="Background"
        />
        <div class="absolute inset-0 bg-gradient-to-b from-slate-900/50 via-slate-900/80 to-slate-900"></div>

        <div class="absolute -top-40 -right-40 w-96 h-96 bg-blue-600/30 rounded-full blur-[100px]"></div>
        <div class="absolute bottom-0 -left-40 w-96 h-96 bg-indigo-600/20 rounded-full blur-[100px]"></div>
      </div>
      <div class="relative z-10 max-w-7xl mx-auto px-6 md:px-8 text-center">
        <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-blue-500/20 border border-blue-500/30 text-blue-300 text-sm font-medium mb-6">
          <span class="w-2 h-2 rounded-full bg-blue-500 animate-pulse"></span>
          JOIN US
        </div>
        <h1 class="text-4xl md:text-6xl lg:text-7xl font-bold tracking-tight mb-8">
          加入全球供应链<span class="text-transparent bg-clip-text bg-gradient-to-r from-blue-400 to-indigo-400">大平台</span>
        </h1>
        <p class="text-lg md:text-xl text-slate-300 max-w-2xl mx-auto leading-relaxed">
          完成身份预审，让全球合作伙伴发现你。审核通过后即可使用平台全部能力。
        </p>
      </div>
    </div>

    <!-- Main Content -->
    <div class="flex-1 py-12 md:py-20 px-6">
      <div class="max-w-3xl mx-auto">

        <!-- Progress Bar -->
        <div class="flex items-center justify-between mb-12 relative">
          <div class="absolute left-0 top-1/2 -translate-y-1/2 w-full h-0.5 bg-slate-200 -z-10"></div>

          <div :class="['flex flex-col items-center gap-2 bg-slate-50 px-2 transition-colors', currentStep >= 1 ? 'text-blue-600' : 'text-slate-400']">
            <div :class="['w-8 h-8 rounded-full flex items-center justify-center text-sm font-semibold border-2 transition-all', currentStep > 1 ? 'bg-blue-600 border-blue-600 text-white' : currentStep === 1 ? 'border-blue-600 bg-blue-50 text-blue-600' : 'border-slate-300 bg-white text-slate-400']">
              <CheckCircle2 v-if="currentStep > 1" class="w-5 h-5" />
              <span v-else>1</span>
            </div>
            <span class="text-sm font-medium">选择身份</span>
          </div>

          <div :class="['flex flex-col items-center gap-2 bg-slate-50 px-2 transition-colors', currentStep >= 2 ? 'text-blue-600' : 'text-slate-400']">
            <div :class="['w-8 h-8 rounded-full flex items-center justify-center text-sm font-semibold border-2 transition-all', currentStep > 2 ? 'bg-blue-600 border-blue-600 text-white' : currentStep === 2 ? 'border-blue-600 bg-blue-50 text-blue-600' : 'border-slate-300 bg-white text-slate-400']">
              <CheckCircle2 v-if="currentStep > 2" class="w-5 h-5" />
              <span v-else>2</span>
            </div>
            <span class="text-sm font-medium">填写资料</span>
          </div>

          <div :class="['flex flex-col items-center gap-2 bg-slate-50 px-2 transition-colors', currentStep >= 3 ? 'text-blue-600' : 'text-slate-400']">
            <div :class="['w-8 h-8 rounded-full flex items-center justify-center text-sm font-semibold border-2 transition-all', currentStep === 3 ? 'border-blue-600 bg-blue-50 text-blue-600' : 'border-slate-300 bg-white text-slate-400']">
              3
            </div>
            <span class="text-sm font-medium">实名认证</span>
          </div>
        </div>

        <!-- Form Area -->
        <div class="bg-white rounded-3xl shadow-sm border border-slate-200 p-6 md:p-10">

          <!-- Step 1: Select Roles -->
          <div v-if="currentStep === 1" class="animate-in fade-in slide-in-from-bottom-4 duration-500">
            <div class="mb-8 text-center">
              <h3 class="text-2xl font-bold text-slate-900 mb-2">选择您的身份</h3>
              <p class="text-slate-500">很多企业既是采购商也是供应商，您可以根据实际业务勾选一个或多个身份。</p>
            </div>

            <div class="grid md:grid-cols-2 gap-6 mb-8">
              <div
                @click="toggleRole('buyer')"
                :class="['relative p-6 rounded-2xl border-2 cursor-pointer transition-all duration-300', selectedRoles.has('buyer') ? 'border-blue-600 bg-blue-50/50 shadow-md shadow-blue-100' : 'border-slate-200 hover:border-blue-300 hover:bg-slate-50']"
              >
                <div :class="['absolute top-4 right-4 w-6 h-6 rounded-full border-2 flex items-center justify-center transition-colors', selectedRoles.has('buyer') ? 'border-blue-600 bg-blue-600' : 'border-slate-300']">
                  <CheckCircle2 v-if="selectedRoles.has('buyer')" class="w-4 h-4 text-white" />
                </div>
                <div class="w-12 h-12 rounded-xl bg-blue-100 text-blue-600 flex items-center justify-center mb-4">
                  <Briefcase class="w-6 h-6" />
                </div>
                <h4 class="text-lg font-bold text-slate-900 mb-2">我是采购商</h4>
                <p class="text-sm text-slate-600 mb-4 h-10">我需要采购商品，寻找全球优质供应商</p>
                <ul class="text-sm text-slate-500 space-y-2">
                  <li class="flex items-start gap-2"><div class="w-1.5 h-1.5 rounded-full bg-slate-300 mt-1.5"></div> 发布采购需求，智能匹配供应商</li>
                  <li class="flex items-start gap-2"><div class="w-1.5 h-1.5 rounded-full bg-slate-300 mt-1.5"></div> 查看供应商尽调报告与评分</li>
                  <li class="flex items-start gap-2"><div class="w-1.5 h-1.5 rounded-full bg-slate-300 mt-1.5"></div> 全链路采购管理与风险预警</li>
                </ul>
              </div>

              <div
                @click="toggleRole('supplier')"
                :class="['relative p-6 rounded-2xl border-2 cursor-pointer transition-all duration-300', selectedRoles.has('supplier') ? 'border-blue-600 bg-blue-50/50 shadow-md shadow-blue-100' : 'border-slate-200 hover:border-blue-300 hover:bg-slate-50']"
              >
                <div :class="['absolute top-4 right-4 w-6 h-6 rounded-full border-2 flex items-center justify-center transition-colors', selectedRoles.has('supplier') ? 'border-blue-600 bg-blue-600' : 'border-slate-300']">
                  <CheckCircle2 v-if="selectedRoles.has('supplier')" class="w-4 h-4 text-white" />
                </div>
                <div class="w-12 h-12 rounded-xl bg-indigo-100 text-indigo-600 flex items-center justify-center mb-4">
                  <Factory class="w-6 h-6" />
                </div>
                <h4 class="text-lg font-bold text-slate-900 mb-2">我是供应商</h4>
                <p class="text-sm text-slate-600 mb-4 h-10">我要展示产能与资质，被全球采购商发现</p>
                <ul class="text-sm text-slate-500 space-y-2">
                  <li class="flex items-start gap-2"><div class="w-1.5 h-1.5 rounded-full bg-slate-300 mt-1.5"></div> 认证产能与资质，获得平台信任背书</li>
                  <li class="flex items-start gap-2"><div class="w-1.5 h-1.5 rounded-full bg-slate-300 mt-1.5"></div> 接收精准采购邀约与询盘</li>
                  <li class="flex items-start gap-2"><div class="w-1.5 h-1.5 rounded-full bg-slate-300 mt-1.5"></div> 智能履约管理与交付追踪</li>
                </ul>
              </div>
            </div>

            <button
              @click="confirmRoles"
              class="w-full flex items-center justify-center gap-2 py-4 rounded-xl bg-blue-600 text-white font-medium hover:bg-blue-700 transition-colors shadow-lg shadow-blue-600/20"
            >
              确认身份，继续填写资料
              <ArrowRight class="w-4 h-4" />
            </button>
          </div>

          <!-- Step 2: Form -->
          <div v-else-if="currentStep === 2" class="animate-in fade-in slide-in-from-right-8 duration-500">
            <button
              @click="currentStep = 1"
              class="flex items-center gap-1.5 text-sm text-slate-500 hover:text-blue-600 transition-colors mb-6"
            >
              <ChevronLeft class="w-4 h-4" /> 返回重新选择
            </button>

            <div class="mb-8">
              <h3 class="text-2xl font-bold text-slate-900 mb-2">{{ step2Title }}</h3>
              <p class="text-slate-500">带 <span class="text-red-500">*</span> 为必填项，请如实填写以便平台审核。</p>
            </div>

            <form class="space-y-8" @submit.prevent>
              <!-- Company Info -->
              <div>
                <h4 class="text-sm font-semibold uppercase tracking-wider text-slate-400 mb-4 border-b border-slate-100 pb-2">公司信息</h4>
                <div class="grid md:grid-cols-2 gap-6">
                  <div class="space-y-1.5">
                    <label class="text-sm font-medium text-slate-700">公司名称（与营业执照一致）<span class="text-red-500">*</span></label>
                    <input v-model="formData.company" type="text" class="w-full px-4 py-2.5 rounded-xl border border-slate-300 focus:border-blue-500 focus:ring-2 focus:ring-blue-500/20 outline-none transition-all" placeholder="请输入公司全称" />
                  </div>
                  <div class="space-y-1.5">
                    <label class="text-sm font-medium text-slate-700">所在国家 / 地区<span class="text-red-500">*</span></label>
                    <input v-model="formData.country" type="text" class="w-full px-4 py-2.5 rounded-xl border border-slate-300 focus:border-blue-500 focus:ring-2 focus:ring-blue-500/20 outline-none transition-all" placeholder="例如：中国" />
                  </div>
                  <div class="space-y-1.5">
                    <label class="text-sm font-medium text-slate-700">企业注册号<span class="text-red-500">*</span></label>
                    <input v-model="formData.regNumber" type="text" class="w-full px-4 py-2.5 rounded-xl border border-slate-300 focus:border-blue-500 focus:ring-2 focus:ring-blue-500/20 outline-none transition-all" placeholder="营业执照注册号 / 统一代码" />
                  </div>
                  <div class="space-y-1.5">
                    <label class="text-sm font-medium text-slate-700">成立年份<span class="text-red-500">*</span></label>
                    <input v-model="formData.established" type="number" min="1900" max="2026" class="w-full px-4 py-2.5 rounded-xl border border-slate-300 focus:border-blue-500 focus:ring-2 focus:ring-blue-500/20 outline-none transition-all" placeholder="例如：2015" />
                  </div>
                </div>
              </div>

              <!-- Buyer Fields -->
              <div v-if="selectedRoles.has('buyer')" class="animate-in fade-in duration-300">
                <h4 class="text-sm font-semibold uppercase tracking-wider text-slate-400 mb-4 border-b border-slate-100 pb-2">采购需求</h4>
                <div class="grid md:grid-cols-2 gap-6">
                  <div class="space-y-1.5">
                    <label class="text-sm font-medium text-slate-700">主要采购品类<span class="text-red-500">*</span></label>
                    <input v-model="formData.buyCategory" type="text" class="w-full px-4 py-2.5 rounded-xl border border-slate-300 focus:border-blue-500 focus:ring-2 focus:ring-blue-500/20 outline-none transition-all" placeholder="例如：电子元器件、化工原料" />
                  </div>
                  <div class="space-y-1.5">
                    <label class="text-sm font-medium text-slate-700">年采购额范围<span class="text-red-500">*</span></label>
                    <select v-model="formData.buyVolume" class="w-full px-4 py-2.5 rounded-xl border border-slate-300 focus:border-blue-500 focus:ring-2 focus:ring-blue-500/20 outline-none transition-all bg-white">
                      <option value="">请选择</option>
                      <option value="1">100万美元以下</option>
                      <option value="2">100万–500万美元</option>
                      <option value="3">500万–2000万美元</option>
                      <option value="4">2000万–1亿美元</option>
                      <option value="5">1亿美元以上</option>
                    </select>
                  </div>
                  <div class="space-y-1.5 md:col-span-2">
                    <label class="text-sm font-medium text-slate-700">主要采购市场</label>
                    <input v-model="formData.buyMarket" type="text" class="w-full px-4 py-2.5 rounded-xl border border-slate-300 focus:border-blue-500 focus:ring-2 focus:ring-blue-500/20 outline-none transition-all" placeholder="例如：东南亚、欧美、中东" />
                  </div>
                </div>
              </div>

              <!-- Supplier Fields -->
              <div v-if="selectedRoles.has('supplier')" class="animate-in fade-in duration-300">
                <h4 class="text-sm font-semibold uppercase tracking-wider text-slate-400 mb-4 border-b border-slate-100 pb-2">供应能力</h4>
                <div class="grid md:grid-cols-2 gap-6">
                  <div class="space-y-1.5">
                    <label class="text-sm font-medium text-slate-700">主要生产品类<span class="text-red-500">*</span></label>
                    <input v-model="formData.supCategory" type="text" class="w-full px-4 py-2.5 rounded-xl border border-slate-300 focus:border-blue-500 focus:ring-2 focus:ring-blue-500/20 outline-none transition-all" placeholder="例如：精密五金件、纺织面料" />
                  </div>
                  <div class="space-y-1.5">
                    <label class="text-sm font-medium text-slate-700">年产能<span class="text-red-500">*</span></label>
                    <input v-model="formData.supCapacity" type="text" class="w-full px-4 py-2.5 rounded-xl border border-slate-300 focus:border-blue-500 focus:ring-2 focus:ring-blue-500/20 outline-none transition-all" placeholder="例如：500万件/年" />
                  </div>
                  <div class="space-y-1.5">
                    <label class="text-sm font-medium text-slate-700">持有认证资质</label>
                    <input v-model="formData.supCerts" type="text" class="w-full px-4 py-2.5 rounded-xl border border-slate-300 focus:border-blue-500 focus:ring-2 focus:ring-blue-500/20 outline-none transition-all" placeholder="例如：ISO 9001, IATF 16949" />
                  </div>
                  <div class="space-y-1.5">
                    <label class="text-sm font-medium text-slate-700">出口经验</label>
                    <select v-model="formData.supExport" class="w-full px-4 py-2.5 rounded-xl border border-slate-300 focus:border-blue-500 focus:ring-2 focus:ring-blue-500/20 outline-none transition-all bg-white">
                      <option value="">请选择</option>
                      <option value="0">无出口经验</option>
                      <option value="1">1–3年</option>
                      <option value="2">3–10年</option>
                      <option value="3">10年以上</option>
                    </select>
                  </div>
                </div>
              </div>

              <!-- Contact Info -->
              <div>
                <h4 class="text-sm font-semibold uppercase tracking-wider text-slate-400 mb-4 border-b border-slate-100 pb-2">联系人信息</h4>
                <div class="grid md:grid-cols-2 gap-6">
                  <div class="space-y-1.5">
                    <label class="text-sm font-medium text-slate-700">联系人姓名<span class="text-red-500">*</span></label>
                    <input v-model="formData.contactName" type="text" class="w-full px-4 py-2.5 rounded-xl border border-slate-300 focus:border-blue-500 focus:ring-2 focus:ring-blue-500/20 outline-none transition-all" placeholder="请输入姓名" />
                  </div>
                  <div class="space-y-1.5">
                    <label class="text-sm font-medium text-slate-700">职位</label>
                    <input v-model="formData.contactTitle" type="text" class="w-full px-4 py-2.5 rounded-xl border border-slate-300 focus:border-blue-500 focus:ring-2 focus:ring-blue-500/20 outline-none transition-all" placeholder="例如：采购总监" />
                  </div>
                  <div class="space-y-1.5">
                    <label class="text-sm font-medium text-slate-700">工作邮箱<span class="text-red-500">*</span></label>
                    <input v-model="formData.email" type="email" class="w-full px-4 py-2.5 rounded-xl border border-slate-300 focus:border-blue-500 focus:ring-2 focus:ring-blue-500/20 outline-none transition-all" placeholder="name@company.com" />
                  </div>
                  <div class="space-y-1.5">
                    <label class="text-sm font-medium text-slate-700">联系电话<span class="text-red-500">*</span></label>
                    <input v-model="formData.phone" type="tel" class="w-full px-4 py-2.5 rounded-xl border border-slate-300 focus:border-blue-500 focus:ring-2 focus:ring-blue-500/20 outline-none transition-all" placeholder="+86 138-xxxx-xxxx" />
                  </div>
                </div>
              </div>

              <div class="pt-4">
                <button
                  type="button"
                  @click="goToStep3"
                  class="w-full flex items-center justify-center gap-2 py-4 rounded-xl bg-blue-600 text-white font-medium hover:bg-blue-700 transition-colors shadow-lg shadow-blue-600/20"
                >
                  下一步：实名认证
                  <ArrowRight class="w-4 h-4" />
                </button>
              </div>
            </form>
          </div>

          <!-- Step 3: Auth -->
          <div v-else-if="currentStep === 3" class="animate-in fade-in slide-in-from-right-8 duration-500">
            <button
              @click="currentStep = 2"
              class="flex items-center gap-1.5 text-sm text-slate-500 hover:text-blue-600 transition-colors mb-6"
            >
              <ChevronLeft class="w-4 h-4" /> 返回修改资料
            </button>

            <div class="text-center mb-8">
              <div class="w-16 h-16 bg-blue-100 rounded-full flex items-center justify-center mx-auto mb-4">
                <ShieldCheck class="w-8 h-8 text-blue-600" />
              </div>
              <h3 class="text-2xl font-bold text-slate-900 mb-2">完成实名认证</h3>
              <p class="text-slate-500 max-w-lg mx-auto">为保障交易安全，请通过"世界护照"完成企业实名认证。认证通过后，您的资料将自动提交审核。</p>
            </div>

            <div class="bg-slate-50 rounded-2xl p-6 md:p-8 border border-slate-200 mb-8">
              <h4 class="text-lg font-bold text-slate-900 mb-2">世界护照 · 企业实名认证</h4>
              <p class="text-sm text-slate-600 mb-6">上传营业执照与法人身份证，完成企业身份核验。认证信息加密存储，仅用于平台审核。</p>

              <div class="space-y-4 mb-8">
                <div class="flex items-center gap-3 text-sm font-medium text-slate-700 bg-white p-4 rounded-xl border border-slate-200">
                  <FileText class="w-5 h-5 text-blue-600" />
                  营业执照
                </div>
                <div class="flex items-center gap-3 text-sm font-medium text-slate-700 bg-white p-4 rounded-xl border border-slate-200">
                  <BadgeCheck class="w-5 h-5 text-blue-600" />
                  法人代表身份证（正反面）
                </div>
              </div>

              <a
                href="https://cna.gbe.aiplusglobal.cn/"
                target="_blank"
                rel="noopener noreferrer"
                class="flex items-center justify-center gap-2 w-full py-4 rounded-xl bg-slate-900 text-white font-medium hover:bg-slate-800 transition-colors"
              >
                <UploadCloud class="w-5 h-5" />
                前往世界护照完成认证
              </a>
            </div>

            <div class="text-sm text-slate-500 text-center mb-8 bg-blue-50/50 p-4 rounded-xl border border-blue-100">
              <p>认证完成后，我们的审核团队将在 <strong>1–3 个工作日</strong>内完成审核，并通过邮件通知结果。</p>
              <p class="mt-1">如有疑问请联系 <a href="mailto:hello@globalscm.com" class="text-blue-600 hover:underline">hello@globalscm.com</a>。</p>
            </div>

            <button
              @click="submitApplication"
              class="w-full flex items-center justify-center gap-2 py-4 rounded-xl border-2 border-blue-600 text-blue-600 font-medium hover:bg-blue-50 transition-colors"
            >
              提交预审申请
            </button>
          </div>

        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive, computed } from 'vue'
import {
  CheckCircle2, ArrowRight, Briefcase, Factory,
  ChevronLeft, UploadCloud, ShieldCheck, FileText, BadgeCheck
} from 'lucide-vue-next'
import ImageWithFallback from '@/components/ImageWithFallback.vue'

const currentStep = ref(1)
const selectedRoles = ref(new Set())

const formData = reactive({
  company: "",
  country: "",
  regNumber: "",
  established: "",
  buyCategory: "",
  buyVolume: "",
  buyMarket: "",
  supCategory: "",
  supCapacity: "",
  supCerts: "",
  supExport: "",
  contactName: "",
  contactTitle: "",
  email: "",
  phone: "",
})

function toggleRole(role) {
  const newRoles = new Set(selectedRoles.value)
  if (newRoles.has(role)) {
    newRoles.delete(role)
  } else {
    newRoles.add(role)
  }
  selectedRoles.value = newRoles
}

function confirmRoles() {
  if (selectedRoles.value.size === 0) {
    alert("请至少选择一个身份。")
    return
  }
  currentStep.value = 2
}

const step2Title = computed(() => {
  if (selectedRoles.value.size === 2) return '填写企业资料（采购商 + 供应商）'
  if (selectedRoles.value.has('buyer')) return '填写采购商资料'
  return '填写供应商资料'
})

function validateStep2() {
  const requiredFields = [
    "company", "country", "regNumber", "established",
    "contactName", "email", "phone"
  ]

  if (selectedRoles.value.has("buyer")) {
    requiredFields.push("buyCategory", "buyVolume")
  }
  if (selectedRoles.value.has("supplier")) {
    requiredFields.push("supCategory", "supCapacity")
  }

  const missing = requiredFields.filter(field => !formData[field])

  if (missing.length > 0) {
    alert("请填写所有必填字段（带 * 号的项）。")
    return false
  }
  return true
}

function goToStep3() {
  if (validateStep2()) {
    currentStep.value = 3
  }
}

function submitApplication() {
  alert('预审申请已提交！\n\n我们将在 1-3 个工作日内完成审核，结果将发送至您的邮箱。')
}
</script>
