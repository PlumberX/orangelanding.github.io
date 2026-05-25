<template>
  <div class="min-h-screen bg-[#f8fafc] font-['Onest',sans-serif]">
    <div class="flex flex-col items-center gap-[10px] px-8 py-8">

      <!-- HEADER -->
      <header class="sticky top-4 z-50 w-full max-w-[1256px] backdrop-blur-[15px] bg-white/90 flex items-center justify-between overflow-hidden px-5 py-4 rounded-3xl shadow-sm">
        <a href="/" class="shrink-0">
          <img :src="assets.logo" alt="orangedata" class="h-[22px] w-[130px]" />
        </a>
        <div class="flex gap-4 items-center">
          <span class="font-semibold text-[16px] text-black whitespace-nowrap">+7 (495) 445-90-51</span>
          <button class="flex items-center gap-2 bg-[#fa7415] text-white text-[14px] font-medium px-4 py-2 rounded-lg min-h-[36px] whitespace-nowrap hover:bg-[#e8680a] transition-colors">
            <img :src="assets.iconBuy" alt="" class="w-4 h-4" />
            Купить
          </button>
          <button class="flex items-center gap-2 bg-[#f1f5f9] text-[#1e293b] text-[14px] font-medium px-4 py-2 rounded-lg min-h-[36px] whitespace-nowrap hover:bg-[#e2e8f0] transition-colors">
            <img :src="assets.iconLogin" alt="" class="w-4 h-4" />
            Вход в кабинет
          </button>
        </div>
      </header>

      <!-- MAIN CONTENT -->
      <main class="w-full max-w-[1256px] flex flex-col gap-[10px]">

        <!-- HERO -->
        <section
          class="relative flex flex-col gap-6 md:gap-10 justify-center overflow-hidden p-6 md:p-10 rounded-[36px] min-h-[320px] md:min-h-[462px]"
          :style="heroStyle"
        >
          <!-- Hero background image -->
          <div class="absolute inset-0 pointer-events-none overflow-hidden rounded-[36px]">
            <img :src="assets.heroBg" alt="" class="absolute right-0 top-0 h-full w-auto object-cover" />
          </div>
          <div class="relative z-10 flex flex-col gap-3 text-white max-w-[660px]">
            <h1 class="text-[32px] md:text-[48px] font-semibold leading-[1.1] tracking-[-1.5px]">
              Облачные кассы для любого бизнеса
            </h1>
            <p class="text-[16px] md:text-[24px] font-normal leading-[1.4]">
              Поможем вашему бизнесу пробивать чеки быстро и без лишних сложностей
            </p>
          </div>
          <div class="relative z-10 flex flex-col md:flex-row gap-3 md:gap-4 md:items-center">
            <button class="flex items-center justify-center gap-2 bg-[#fa7415] text-white text-[16px] font-medium px-5 h-12 rounded-2xl hover:bg-[#e8680a] transition-colors w-full md:w-auto">
              <img :src="assets.iconBuy" alt="" class="w-6 h-6" />
              Купить
            </button>
            <button @click="openModal" class="flex items-center justify-center gap-2 bg-[#f1f5f9] text-[#1e293b] text-[16px] font-medium px-4 h-12 rounded-2xl hover:bg-[#e2e8f0] transition-colors w-full md:w-auto">
              Задать вопрос
            </button>
          </div>
        </section>

        <!-- STATS BENTO -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-[10px]">
          <!-- 20 000+ -->
          <div class="bg-white rounded-[36px] p-6 md:p-10 overflow-hidden relative h-[160px] md:h-[375px] flex flex-col justify-end">
            <div class="absolute inset-0 pointer-events-none overflow-hidden">
              <img :src="assets.stat1Bg" alt="" class="absolute inset-0 w-full h-full object-cover pointer-events-none" />
            </div>
            <div class="relative z-10">
              <div class="text-[40px] md:text-[64px] font-semibold text-[#4c1d96] leading-[1] tracking-[-1.5px]">20 000+</div>
              <div class="text-[16px] md:text-[20px] font-normal text-black leading-[1.4] mt-1">Клиентов по всей России</div>
            </div>
          </div>
          <!-- 10 лет -->
          <div class="bg-white rounded-[36px] p-6 md:p-10 overflow-hidden relative h-[160px] md:h-[375px] flex flex-col justify-start">
            <div class="absolute inset-0 pointer-events-none overflow-hidden">
              <img :src="assets.stat2Bg" alt="" class="absolute inset-0 w-full h-full object-cover pointer-events-none" />
            </div>
            <div class="relative z-10">
              <div class="text-[40px] md:text-[64px] font-semibold text-[#4c1d96] leading-[1] tracking-[-1.5px]">10 лет</div>
              <div class="text-[16px] md:text-[20px] font-normal text-black leading-[1.4] mt-1">На рынке облачной<br/>фискализации</div>
            </div>
            <div class="absolute top-16 right-8 flex flex-col gap-3 pointer-events-none">
              <span v-for="d in [20,13,20,14]" :key="d+'_2'" class="bg-[#7979ef] rounded-full shadow-md block" :style="{width:d+'px',height:d+'px'}" />
            </div>
          </div>
          <!-- 25 млн. -->
          <div class="bg-white rounded-[36px] p-6 md:p-10 overflow-hidden relative h-[160px] md:h-[375px] flex flex-col justify-center">
            <div class="absolute inset-0 pointer-events-none overflow-hidden">
              <img :src="assets.stat3Bg" alt="" class="absolute inset-0 w-full h-full object-cover pointer-events-none" />
            </div>
            <div class="relative z-10">
              <div class="text-[40px] md:text-[64px] font-semibold text-[#4c1d96] leading-[1] tracking-[-1.5px]">25 млн.</div>
              <div class="text-[16px] md:text-[20px] font-normal text-black leading-[1.4] mt-1">Транзакций в сутки</div>
            </div>
          </div>
        </div>

        <!-- FOR WHO -->
        <section class="py-10 flex flex-col gap-16">
          <h2 class="text-[64px] font-semibold text-[#020617] leading-[1] tracking-[-1.5px]">
            Подходит для<br />
            <span class="relative inline-block text-[#4c1d96]">
              любого
              <img :src="assets.vectorUnderline" alt="" class="absolute left-0 w-full pointer-events-none" style="bottom: -6px; height: 12px;" />
            </span> бизнеса
          </h2>

          <div class="flex flex-col gap-4">
            <!-- Row 1 -->
            <div class="grid grid-cols-12 gap-4">
              <div class="col-span-7 bg-white rounded-[36px] p-10 overflow-hidden relative min-h-[238px]">
                <h3 class="text-[32px] font-semibold text-[#020617] tracking-[-1.5px] relative z-10">Интернет-магазины</h3>
                <img :src="assets.rectShops" alt="" class="absolute right-0 top-0 h-full w-auto object-cover pointer-events-none" />
              </div>
              <div class="col-span-5 bg-white rounded-[36px] p-10 overflow-hidden relative min-h-[238px]">
                <h3 class="text-[32px] font-semibold text-[#020617] tracking-[-1.5px] relative z-10">Вендинг</h3>
                <img :src="assets.rectVending" alt="" class="absolute right-0 top-0 h-full w-auto object-cover pointer-events-none scale-y-[-1] scale-x-[-1]" />
              </div>
            </div>

            <!-- Row 2 -->
            <div class="grid grid-cols-12 gap-4">
              <!-- Transport (spans 2 rows) -->
              <div class="col-span-6 row-span-2 bg-white rounded-[36px] p-10 overflow-hidden relative flex flex-col gap-6 min-h-[365px]">
                <div class="relative z-10 flex flex-col gap-2">
                  <h3 class="text-[32px] font-semibold text-[#020617] tracking-[-1.5px] whitespace-nowrap">Транспорт и логистика</h3>
                  <p class="text-[16px] font-normal text-[#020617] leading-[1.5] max-w-[350px]">
                    Используйте кассу для приема платежей курьеру или безналичных платежей в собственном приложении такси
                  </p>
                </div>
                <button class="relative z-10 flex items-center gap-2 bg-[#fa7415] text-white text-[16px] font-medium px-5 h-11 rounded-2xl w-fit hover:bg-[#e8680a] transition-colors">
                  <img :src="assets.iconBuy" alt="" class="w-6 h-6" />
                  Купить
                </button>
                <img :src="assets.rectTransport" alt="" class="absolute right-0 top-0 h-full w-auto object-cover pointer-events-none" />
              </div>
              <!-- Apps -->
              <div class="col-span-6 bg-white rounded-[36px] p-10 overflow-hidden relative min-h-[174px]">
                <h3 class="text-[32px] font-semibold text-[#020617] tracking-[-1.5px] relative z-10">Приложения и сервисы</h3>
                <img :src="assets.rectApps" alt="" class="absolute right-0 top-0 h-[110%] w-auto object-cover pointer-events-none" />
              </div>
              <!-- Pharmacy -->
              <div class="col-span-6 bg-white rounded-[36px] p-10 overflow-hidden relative min-h-[174px]">
                <h3 class="text-[32px] font-semibold text-[#020617] tracking-[-1.5px] relative z-10">Онлайн-аптеки</h3>
                <img :src="assets.rectPharmacy" alt="" class="absolute right-0 top-8 h-[90%] w-auto object-cover pointer-events-none scale-x-[-1] scale-y-[-1]" />
              </div>
            </div>
          </div>

          <!-- "Not Sure" Banner -->
          <div
            class="relative flex flex-col gap-9 items-center justify-center p-10 rounded-[36px] overflow-hidden min-h-[290px] text-center"
            :style="bannerStyle"
          >
            <div class="absolute inset-0 pointer-events-none">
              <img :src="assets.bannerBg" alt="" class="absolute inset-0 w-full h-full object-cover" />
              <div class="absolute inset-0 bg-[rgba(22,22,22,0.48)]" />
            </div>
            <div class="relative z-10 text-white flex flex-col gap-3 items-center">
              <h2 class="text-[48px] font-semibold leading-[1.1] tracking-[-1.5px] whitespace-nowrap">Не знаете что выбрать?</h2>
              <p class="text-[20px] font-normal leading-[1.5] max-w-[580px]">
                Оставьте заявку на бесплатную консультацию. Наши специалисты подробно расскажут что именно подойдет для вашего бизнеса
              </p>
            </div>
            <button class="relative z-10 bg-[#fa7415] text-white text-[16px] font-medium px-6 h-11 rounded-2xl hover:bg-[#e8680a] transition-colors">
              Задать вопрос
            </button>
          </div>
        </section>

        <!-- PRICING -->
        <section class="py-10 flex flex-col gap-16">
          <h2 class="text-[64px] font-semibold text-[#020617] leading-[1] tracking-[-1.5px] max-w-[660px]">
            Выберите подходящий тариф
          </h2>
          <div class="flex flex-col gap-6">
            <!-- Tabs -->
            <div class="bg-[#f1f5f9] border border-[#cbd5e1] flex gap-[10px] h-[60px] items-center p-2 rounded-full w-fit">
              <button
                v-for="tab in pricingTabs"
                :key="tab.id"
                @click="activeTab = tab.id"
                class="h-full px-4 rounded-full text-[16px] font-normal transition-colors whitespace-nowrap"
                :class="activeTab === tab.id
                  ? 'bg-[#fa7415] text-white'
                  : 'text-[#020617] hover:bg-white/60'"
              >
                {{ tab.label }}
              </button>
            </div>

            <!-- Tariff content -->
            <div class="flex gap-[10px] items-center">
              <div class="flex-1 flex flex-col gap-3">
                <h3 class="text-[32px] font-semibold text-[#020617] tracking-[-1.5px] whitespace-nowrap">Все просто — один тариф</h3>
                <p class="text-[16px] font-normal text-[#020617] leading-[1.5] max-w-[350px]">
                  Один тариф — без лишнего выбора и сложностей. Подключились и сразу начали работать. Всё просто и уже настроено.
                </p>
              </div>
              <!-- Rate card -->
              <div class="flex-1 bg-white rounded-[36px] p-10 flex flex-col gap-6 shadow-[0px_11px_30px_0px_rgba(0,0,0,0.09),0px_2px_8.5px_0px_rgba(0,0,0,0.11)]">
                <div class="flex flex-col gap-2">
                  <span class="text-[12px] font-semibold text-[#64748b] tracking-wide uppercase">Тариф</span>
                  <div class="flex items-baseline justify-between">
                    <span class="text-[30px] font-bold text-[#020617] tracking-[-1px]">«Все просто»</span>
                    <span class="text-[24px] font-semibold text-[#5b5bd6] tracking-[-1.5px]">2400 ₽/месяц.</span>
                  </div>
                </div>
                <div class="flex flex-col gap-2">
                  <div v-for="feature in tariffFeatures" :key="feature" class="flex items-center gap-4">
                    <span class="text-[14px] text-[#64748b] font-normal whitespace-nowrap">{{ feature }}</span>
                    <div class="flex-1 border-t border-dashed border-[#e2e8f0]" />
                    <img :src="assets.iconCheck" alt="✓" class="w-6 h-6 shrink-0" />
                  </div>
                </div>
                <button class="w-full bg-[#fa7415] text-white text-[16px] font-normal h-11 rounded-2xl hover:bg-[#e8680a] transition-colors">
                  Выбрать тариф
                </button>
              </div>
            </div>
          </div>
        </section>

        <!-- TRUSTED -->
        <section class="py-10 flex flex-col gap-16">
          <h2 class="text-[64px] font-semibold text-[#020617] leading-[1] tracking-[-1.5px]">Нам доверяют</h2>
          <div class="grid grid-cols-7 gap-x-10 gap-y-10">
            <div v-for="logo in clientLogos" :key="logo" class="flex items-center justify-center">
              <img :src="logo" alt="client" class="max-h-[50px] w-full object-contain grayscale hover:grayscale-0 transition-all" />
            </div>
          </div>
        </section>

        <!-- FAQ -->
        <section class="py-10 flex flex-col gap-16">
          <h2 class="text-[64px] font-semibold text-[#020617] leading-[1] tracking-[-1.5px]">Частые вопросы</h2>
          <div class="bg-white rounded-[36px] p-10 flex flex-col gap-6">
            <template v-for="(item, idx) in faqItems" :key="idx">
              <div
                class="flex items-start justify-between gap-8 cursor-pointer"
                @click="openFaq = openFaq === idx ? null : idx"
              >
                <div class="flex-1 flex flex-col gap-2">
                  <h3 class="text-[24px] font-semibold text-[#020617] tracking-[-1.5px] leading-[1.4]">{{ item.q }}</h3>
                  <p v-if="openFaq === idx && item.a" class="text-[16px] font-normal text-[#020617] leading-[1.5]">{{ item.a }}</p>
                </div>
                <div
                  class="shrink-0 w-9 h-9 rounded-full border-2 border-[#94a3b8] flex items-center justify-center transition-transform"
                  :class="openFaq === idx ? 'rotate-0' : 'rotate-45'"
                >
                  <img :src="assets.iconClose" alt="" class="w-5 h-5" />
                </div>
              </div>
              <div v-if="idx < faqItems.length - 1" class="h-px bg-gradient-to-r from-[#d9e3ee] to-[#d9e3ee]" />
            </template>
          </div>
        </section>

        <!-- FOOTER CTA -->
        <section
          class="flex gap-9 items-center p-10 rounded-[36px] overflow-hidden relative"
          :style="footerCtaStyle"
        >
          <div class="absolute right-48 top-0 bottom-0 w-[560px] pointer-events-none overflow-hidden opacity-6">
            <img :src="assets.rectFooter" alt="" class="w-full h-full object-cover" style="transform:rotate(14.72deg)" />
          </div>
          <div class="relative z-10 text-white flex flex-col gap-3 flex-1">
            <h2 class="text-[48px] font-semibold leading-[1.1] tracking-[-1.5px]">Все еще остались вопросы?</h2>
            <p class="text-[24px] font-normal leading-[1.4]">Оставьте заявку на бесплатную консультацию</p>
          </div>
          <div class="relative z-10 bg-white border border-[#dde8f4] rounded-3xl p-6 flex flex-col gap-3 flex-1 shadow-md">
            <input
              type="text"
              placeholder="Ваше имя"
              class="bg-white border border-[#e2e8f0] rounded-[10px] h-11 px-3 text-[14px] text-[#64748b] w-full focus:outline-none focus:border-[#fa7415] transition-colors"
            />
            <input
              type="tel"
              placeholder="Номер телефона"
              class="bg-white border border-[#e2e8f0] rounded-[10px] h-11 px-3 text-[14px] text-[#64748b] w-full focus:outline-none focus:border-[#fa7415] transition-colors"
            />
            <button class="w-full bg-[#fa7415] text-white text-[16px] font-normal h-11 rounded-2xl hover:bg-[#e8680a] transition-colors">
              Оставить заявку
            </button>
          </div>
        </section>

      </main>

      <!-- FOOTER -->
      <footer class="w-full max-w-[1256px] bg-white border border-white rounded-tl-3xl rounded-tr-3xl px-8 pt-8 pb-0">
        <div class="flex items-start justify-between pb-4">
          <a href="/" class="shrink-0">
            <img :src="assets.logo" alt="orangedata" class="h-[22px] w-[130px]" />
          </a>
          <div class="flex gap-2 items-center">
            <div class="bg-[#f1f5f9] p-2 rounded-full">
              <img :src="assets.iconHeadset" alt="" class="w-4 h-4" />
            </div>
            <div class="flex flex-col items-end gap-1 text-[14px]">
              <a href="mailto:help@orangedata.ru" class="text-[#5b5bd6] underline hover:text-[#4a4abf]">help@orangedata.ru</a>
              <span class="text-[#64748b]">+7 (495) 445-90-51</span>
            </div>
          </div>
        </div>
        <div class="flex items-center justify-between border-t border-[#e2e8f0] py-4">
          <nav class="flex gap-6 text-[14px] text-[#64748b] font-normal">
            <a href="#faq" class="hover:text-[#020617] transition-colors">FAQ</a>
            <a href="#" class="hover:text-[#020617] transition-colors">Инструкции</a>
            <a href="https://lk.orangedata.ru/docs/tarify.pdf" target="_blank" class="hover:text-[#020617] transition-colors">Тарифы</a>
            <a href="https://orangedata.ru/docs/oferta.pdf" target="_blank" class="hover:text-[#020617] transition-colors">Скачать оферту</a>
            <a href="#" class="hover:text-[#020617] transition-colors">Условия сотрудничества</a>
          </nav>
          <span class="text-[14px] text-[#64748b]">© 2026 АО "Оранж Дата"</span>
        </div>
      </footer>

    </div>

    <!-- MODAL -->
    <Transition name="modal" :duration="350">
      <div
        v-if="showModal"
        class="fixed inset-0 z-[100] flex items-center justify-center p-4"
        @click.self="showModal = false"
      >
        <!-- Overlay -->
        <div class="modal-overlay absolute inset-0" @click="showModal = false" />

        <!-- Card -->
        <div class="modal-card relative bg-white border border-[#dde8f4] rounded-[24px] shadow-lg p-6 w-full max-w-[465px] flex flex-col gap-[10px]">
          <!-- Header -->
          <div class="flex gap-[10px] items-start justify-between">
            <div class="flex flex-col gap-1">
              <p class="text-[24px] font-semibold text-[#020617] leading-[1.2] tracking-[-1px]">Оставьте заявку</p>
              <p class="text-[16px] font-normal text-[#020617] leading-[1.5]">Мы свяжемся с вами в ближайшее время</p>
            </div>
            <button @click="showModal = false" class="shrink-0 w-6 h-6 flex items-center justify-center hover:opacity-60 transition-opacity">
              <img :src="assets.iconClose" alt="Закрыть" class="w-[14px] h-[14px]" />
            </button>
          </div>

          <!-- Fields -->
          <div class="flex flex-col gap-4">
            <input
              v-model="modalName"
              type="text"
              placeholder="Ваше имя"
              class="w-full h-[44px] px-3 border border-[#e2e8f0] rounded-[10px] text-[14px] text-[#020617] placeholder-[#64748b] outline-none focus:border-[#7979ef] transition-colors"
            />
            <input
              v-model="modalPhone"
              type="tel"
              placeholder="Номер телефона"
              class="w-full h-[44px] px-3 border border-[#e2e8f0] rounded-[10px] text-[14px] text-[#020617] placeholder-[#64748b] outline-none focus:border-[#7979ef] transition-colors"
            />
            <button
              @click="submitModal"
              class="w-full h-[44px] bg-[#fa7415] text-white text-[16px] font-normal rounded-[16px] hover:bg-[#e8680a] transition-colors"
            >
              Оставить заявку
            </button>
          </div>
        </div>
      </div>
    </Transition>

  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const showModal = ref(false)
const modalName = ref('')
const modalPhone = ref('')

function openModal() {
  showModal.value = true
}

function submitModal() {
  // TODO: send form
  showModal.value = false
  modalName.value = ''
  modalPhone.value = ''
}

const BASE = import.meta.env.BASE_URL + 'assets'

const assets = {
  logo:          `${BASE}/orangelogo.svg`,
  heroBg:        `${BASE}/a1d428284cd705a0b94fe0519ff1236c1dacdace.png`,
  stat1Bg:       `${BASE}/2fd7a312420f259e1d7f49a145432d8ba1fa9f73.png`,
  stat2Bg:       `${BASE}/001023813554b585ae32d0350927434765b11e83.png`,
  stat3Bg:       `${BASE}/348887504032cfefbb117bed3dc28e21c48f1959.png`,
  rectShops:     `${BASE}/b51fc9e27d38fdd87abc5b7f9c638f4411f9a154.png`,
  rectVending:   `${BASE}/9dceff1b8100e3d3e8bdc45103b43b8bd22a78ee.png`,
  rectApps:      `${BASE}/da4189cdebf338c29102af8ecc0297d581a5dfb6.png`,
  rectPharmacy:  `${BASE}/b91098b92ec1a0f42fa5392b30f8b1360484fa8f.png`,
  rectTransport: `${BASE}/14521d72effb9e180ad3d41343f1cbcb2e7172da.png`,
  bannerBg:      `${BASE}/7212252ad5a6ead7b32f8e5d529c55b889688bff.png`,
  rectFooter:    `${BASE}/96670fa4c35535b95dc8007c099610f3757be185.png`,
  vectorDecor:   `${BASE}/22fb24a233e712f59251851cf8260344b8a7338b.svg`,
  vectorUnderline:`${BASE}/60f4212735fa0a4e2d5f5e12537d0dd477e76d1c.svg`,
  iconBuy:       `${BASE}/bf615ecf291607d41a951885d7ac23e0b403354a.svg`,
  iconLogin:     `${BASE}/3308768e0887c7ddbf2a8c29be77ae1dd5d2caa8.svg`,
  iconCheck:     `${BASE}/9e52ad10f71d44759f293fc82a292dd5bfd3e526.svg`,
  iconClose:     `${BASE}/cc24ee3d9f89cdc1c321d5d59c72bdf466acc700.svg`,
  iconHeadset:   `${BASE}/92247860be3932e7d4d321caa13ccce7589e6ca2.svg`,
}

const heroStyle = {
  backgroundImage: `
    url("data:image/svg+xml;utf8,<svg viewBox='0 0 1216 462' xmlns='http://www.w3.org/2000/svg' preserveAspectRatio='none'><rect x='0' y='0' height='100%' width='100%' fill='url(%23grad)' opacity='1'/><defs><radialGradient id='grad' gradientUnits='userSpaceOnUse' cx='0' cy='0' r='10' gradientTransform='matrix(-73.9 -34.2 34.655 -74.882 1189.5 414.72)'><stop stop-color='rgba(229,179,235,1)' offset='0'/><stop stop-color='rgba(192,144,205,1)' offset='0.25'/><stop stop-color='rgba(154,108,175,1)' offset='0.5'/><stop stop-color='rgba(117,73,144,1)' offset='0.75'/><stop stop-color='rgba(79,37,114,1)' offset='1'/></radialGradient></defs></svg>"),
    linear-gradient(90deg, rgb(250,116,21) 0%, rgb(250,116,21) 100%)
  `,
}

const bannerStyle = {
  backgroundImage: `linear-gradient(90deg, rgb(231,239,247) 0%, rgb(231,239,247) 100%)`,
}

const footerCtaStyle = {
  backgroundImage: `linear-gradient(135deg, #7979ef 0%, #4c1d96 100%)`,
}


const pricingTabs = [
  { id: 'retail', label: 'Розничная торговля и услуги' },
  { id: 'transport', label: 'Транспорт и логистика' },
  { id: 'vending', label: 'Вендинг' },
]
const activeTab = ref('retail')

const tariffFeatures = ['Отправка чеков в ОФД', 'Аренда ККТ', 'Личный кабинет']

const clientLogos = [
  `${BASE}/2baa2cdbd2c3df43f9fc2b69726c4fe3e1330f71.png`,
  `${BASE}/d21c787268fe251f5a3b1ab8cd12c02eed18d671.png`,
  `${BASE}/5bd1772b2b3e4efbf4603fdb7fc4941bbf7e2556.png`,
  `${BASE}/fbd5f8f4200f3f985a4cafcc91959982fdc1abef.png`,
  `${BASE}/a71211b062a7231e5c24c0273e6b9d0e50aad7ee.png`,
  `${BASE}/739e0d9a852f2a70080ae165a0cbe3bc1786a388.png`,
  `${BASE}/af39967139ad798f5175cbb5236ff7b45e09e1ab.png`,
  `${BASE}/dcc6cb1df6c9caf6428732009fe00a7816992a6d.png`,
  `${BASE}/c24c3f1a0d9d868be485e05f84c5adf4e27791ff.png`,
  `${BASE}/e3ca07cba31d3e7dfc4c2bc1d96778245f4210ce.png`,
  `${BASE}/396e6ebb7e7407469dfa18040cdd7cacfa21d6d9.png`,
  `${BASE}/b048f140b6a7ea752800ed6fdc41b1d095c8b396.png`,
  `${BASE}/8786cbf54e5a48c4ff5a1289a76aeef25ea550d6.png`,
  `${BASE}/4fe9c02e521e4afb17df4d0d0991acb5fd4d08e3.png`,
  `${BASE}/65e2e6eeb9dfe541ba4b4749d0123a78abc0d7db.png`,
  `${BASE}/6e6373612bacb226db152cc80e39401378045e19.png`,
  `${BASE}/c5d0468166e7a79f8892dcc096d17c565966ebea.png`,
  `${BASE}/15cedf6920add8f5a02ddd2a3b5c061c709e105a.png`,
  `${BASE}/505a9edb6e2d2e3cf9d0df162450669099e6c79a.png`,
  `${BASE}/3eb4bd74f852869bb14758e8a10541f541b5fd42.png`,
  `${BASE}/85332664564f3e82e1afec2828c0da9642d85026.png`,
  `${BASE}/8b22d113d33a095ec488eeba0c3cd557594c96da.png`,
  `${BASE}/759f894908bb1c4c3fc4eeb8dcfc5fc80d6932c1.png`,
  `${BASE}/a2b171bb3d2c80462ad19f2a779d9584d4d9b2f0.png`,
  `${BASE}/795f2700a4ee1346db655901bfafc321dfb8e347.png`,
  `${BASE}/0beef8a4cf4c5ffdf2ea76600b8ed4dfb411d463.png`,
  `${BASE}/ef05de5d7a56af708b15b513dd4843a793027f35.png`,
  `${BASE}/eccecea6a7865a150aa30773ea90e3e895c5456c.png`,
]

const faqItems = [
  {
    q: 'Как начать работать?',
    a: 'Поможем вашему бизнесу пробивать чеки быстро и без лишних сложностей',
  },
  { q: 'Что такое КЭП?', a: null },
  { q: 'Как работать при двухстадийной схеме оплаты?', a: null },
  { q: 'Что делать при частичном авансе?', a: null },
  { q: 'Направляет ли Orange Data чеки покупателю?', a: null },
  { q: 'Как нам работать с несколькими платежными системами используя одну ККТ?', a: null },
  { q: 'Что такое клиентский ключ? Откуда пользователь получает ключ?', a: null },
]
const openFaq = ref<number | null>(0)
</script>
