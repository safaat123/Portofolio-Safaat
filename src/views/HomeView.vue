<template>
  <div class="relative min-h-screen overflow-hidden">
    <FullScreen3DBackground />
    <main
      class="relative z-10 mt-10 md:mt-1 flex flex-col-reverse gap-8 items-center md:flex-row md:gap-16 md:justify-center min-h-[65vh] md:min-h-[80vh]">
      <div class="space-y-2 text-center md:text-left px-10">
      <p class="text-amber-200">Hello, I'm</p>
      <h1 class="text-4xl font-bold md:text-5xl text-white fadein-up">Safa'at Ihwatul Afdal</h1>
      <div class="py-2">
        <h1
          class="typewrite text-xl font-semibold text-transparent bg-clip-text bg-gradient-to-r from-slate-100 bg-green-400 md:text-2xl fadein-up"
          ref="typewriter">
          <span class="wrap">{{ txt }}</span>
        </h1>
      </div>
      <p class="text-white pr-4 fade-in-from-left">Welcome to My personal website. <span class="wave">👋🏼</span></p>
      <router-link
        :to="{ path: '/', hash: '#certificates-heading' }"
        class="fadein-bot fade-500 mt-4 inline-flex items-center rounded-lg border border-amber-200 px-4 py-2.5 text-sm font-medium text-amber-200 transition duration-300 hover:bg-amber-200/10 focus:outline-none focus:ring-2 focus:ring-amber-200"
      >
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="mr-2 h-4 w-4" aria-hidden="true">
          <path d="M5 3.75A1.75 1.75 0 0 1 6.75 2h10.5A1.75 1.75 0 0 1 19 3.75v11.086a1.75 1.75 0 0 1-.513 1.237l-4.7 4.7a1.75 1.75 0 0 1-1.237.513H6.75A1.75 1.75 0 0 1 5 19.536V3.75Zm3.75 2a.75.75 0 0 0 0 1.5h6.5a.75.75 0 0 0 0-1.5h-6.5Zm0 4a.75.75 0 0 0 0 1.5h6.5a.75.75 0 0 0 0-1.5h-6.5Zm0 4a.75.75 0 0 0 0 1.5h3.5a.75.75 0 0 0 0-1.5h-3.5Z" />
        </svg>
        Lihat Sertifikat
      </router-link>
      <!-- <button
        class="fadein-bot fade-500 flex items-center py-2 px-4 mx-auto text-sm font-medium rounded-lg border transition duration-300 md:py-2.5 md:px-5 md:mx-0 text-amber-200 border-amber-200 hover:bg-amber-200 hover:bg-opacity-10 bg-transparent focus:outline-none w-fit"><svg
          xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="mr-2 w-4 h-4">
          <path fill-rule="evenodd"
            d="M5.625 1.5H9a3.75 3.75 0 013.75 3.75v1.875c0 1.036.84 1.875 1.875 1.875H16.5a3.75 3.75 0 013.75 3.75v7.875c0 1.035-.84 1.875-1.875 1.875H5.625a1.875 1.875 0 01-1.875-1.875V3.375c0-1.036.84-1.875 1.875-1.875zm5.845 17.03a.75.75 0 001.06 0l3-3a.75.75 0 10-1.06-1.06l-1.72 1.72V12a.75.75 0 00-1.5 0v4.19l-1.72-1.72a.75.75 0 00-1.06 1.06l3 3z"
            clip-rule="evenodd"></path>
          <path
            d="M14.25 5.25a5.23 5.23 0 00-1.279-3.434 9.768 9.768 0 016.963 6.963A5.23 5.23 0 0016.5 7.5h-1.875a.375.375 0 01-.375-.375V5.25z">
          </path>
        </svg>Download Resume</button> -->
    </div>
    <div class="flex justify-center md:justify-start fadein-right">
      <img alt="avatar" fetchpriority="high" width="300" height="300" decoding="async" data-nimg="1"
        class="w-7/8 md:h-auto rounded-full border-4 border-green-300 pict" src="https://i.imgur.com/fYLrA7b.jpeg">
    </div>
  </main>
  </div>
  <section id="certificates-heading" class="relative z-10 container mx-auto px-5 pb-24 pt-10 md:px-12 md:pt-4" aria-labelledby="certificates-title">
    <div class="mb-6 text-left">
      <p class="mb-2 text-xs font-semibold uppercase tracking-[0.3em] text-amber-600">Pencapaian</p>
      <h2 id="certificates-title" class="text-2xl font-bold text-white md:text-3xl">Sertifikat Saya</h2>
      <p class="mt-2 max-w-2xl text-sm leading-6 text-slate-400">
        Beberapa sertifikat sebagai bukti proses belajar dan pengembangan kemampuan saya.
      </p>
    </div>
    <div class="grid grid-cols-1 gap-4 sm:grid-cols-2 lg:grid-cols-3">
      <button
        v-for="certificate in certificates"
        :key="certificate.filename"
        type="button"
        class="group overflow-hidden rounded-2xl border border-white/10 bg-[#1e1e1f] text-left text-white shadow-lg transition duration-300 hover:-translate-y-1 hover:border-amber-200/60 hover:bg-[#242425] focus:outline-none focus:ring-2 focus:ring-amber-200"
        @click="openCertificate(certificate)"
      >
        <div class="relative flex aspect-[4/3] items-center justify-center overflow-hidden bg-gradient-to-br from-[#292922] via-[#1e1e1f] to-[#17251f] p-4">
          <img
            v-if="!unavailableCertificateImages[certificate.filename]"
            :src="certificate.image"
            :alt="certificate.title"
            loading="lazy"
            class="h-full w-full rounded-lg object-contain transition duration-300 group-hover:scale-[1.03]"
            @error="markCertificateUnavailable(certificate)"
          >
          <div v-else class="flex flex-col items-center text-center">
            <div class="mb-3 flex h-14 w-14 items-center justify-center rounded-2xl border border-amber-200/30 bg-amber-200/10 text-amber-200">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" class="h-7 w-7" aria-hidden="true">
                <path stroke-linecap="round" stroke-linejoin="round" d="M12 3.75 14.5 5l2.75-.25.5 2.75L20 9.5l-1.25 2.5L20 14.5l-2.25 2-.5 2.75-2.75-.25L12 20.25 9.5 19l-2.75.25-.5-2.75L4 14.5l1.25-2.5L4 9.5l2.25-2 .5-2.75L9.5 5 12 3.75Z" />
                <path stroke-linecap="round" stroke-linejoin="round" d="m9.5 12 1.75 1.75L14.75 10" />
              </svg>
            </div>
            <span class="text-sm font-semibold text-slate-200">{{ certificate.title }}</span>
            <span class="mt-1 text-xs text-slate-400">Tambahkan gambar sertifikat</span>
          </div>
          <span class="absolute right-3 top-3 rounded-full border border-white/10 bg-black/50 px-3 py-1 text-xs font-medium text-amber-100">
            {{ certificate.year || 'Sertifikat' }}
          </span>
        </div>
        <div class="flex items-center justify-between gap-3 px-4 py-4">
          
          <span class="shrink-0 text-sm font-medium text-amber-200 transition group-hover:translate-x-1" aria-hidden="true">Lihat ↗</span>
        </div>
      </button>
    </div>
    <p class="mt-4 text-left text-xs leading-5 text-slate-500">
      Ganti placeholder dengan gambar sertifikat bernama
      <span class="text-slate-300">sertifikat-1.jpg</span> sampai
      <span class="text-slate-300">sertifikat-6.jpg</span> di folder
      <span class="text-slate-300">public/img</span>.
    </p>
  </section>

  <div
    v-if="selectedCertificate"
    class="fixed inset-0 z-50 flex items-center justify-center bg-black/80 p-4"
    role="dialog"
    aria-modal="true"
    :aria-label="selectedCertificate.title"
    @click.self="closeCertificate"
    @keydown.esc="closeCertificate"
  >
    <div class="relative max-h-full w-full max-w-4xl rounded-xl border border-white/10 bg-[#1e1e1f] p-4 text-white shadow-2xl">
      <button
        type="button"
        class="absolute right-3 top-3 z-10 rounded-md bg-black/70 px-3 py-2 text-sm text-white hover:bg-black focus:outline-none focus:ring-2 focus:ring-amber-200"
        aria-label="Tutup pratinjau sertifikat"
        @click="closeCertificate"
      >
        Tutup
      </button>
      <h3 class="mb-4 pr-20 text-lg font-semibold text-amber-200">{{ selectedCertificate.title }}</h3>
      <img
        v-if="!unavailableCertificateImages[selectedCertificate.filename]"
        :src="selectedCertificate.image"
        :alt="selectedCertificate.title"
        class="mx-auto max-h-[75vh] w-full rounded-lg object-contain"
        @error="markCertificateUnavailable(selectedCertificate)"
      >
      <p v-else class="py-12 text-center text-sm text-slate-300">
        Gambar belum tersedia. Tambahkan file <span class="text-amber-200">{{ selectedCertificate.filename }}</span> ke folder public/img.
      </p>
    </div>
  </div>
</template>

<script>
import FullScreen3DBackground from '@/components/FullScreen3DBackground.vue'

export default {
  name: 'HomeView',
  components: {
    FullScreen3DBackground
  },
  data() {
    return {
      toRotate: ["Web Developer", "Full-stack Engineer", "Informatics Student", "UI/UX Designer", "Game Developer"],
      period: 2000,
      txt: '',
      loopNum: 0,
      isDeleting: false,
      certificates: [
        { title: 'Sertifikat 1', issuer: '', year: '', filename: 'data science.jpg', image: '/img/data science.jpg' },
        { title: 'Sertifikat 2', issuer: '', year: '', filename: 'high impact web.jpg', image: '/img/high impact web.jpg' },
        { title: 'Sertifikat 3', issuer: '', year: '', filename: 'One Vulnerability.jpg', image: '/img/One Vulnerability.jpg' },
        { title: 'Sertifikat 4', issuer: '', year: '', filename: 'Penetration Testing.jpg', image: '/img/Penetration Testing.jpg' },
        { title: 'Sertifikat 5', issuer: '', year: '', filename: 'RTIK KOMINFO.jpg', image: '/img/RTIK KOMINFO.JPG' },
        { title: 'Sertifikat 6', issuer: '', year: '', filename: 'UI Design.jpg', image: '/img/UI Design.jpg' },
      ],
      selectedCertificate: null,
      unavailableCertificateImages: {}
    };
  },
  mounted() {
    this.$nextTick(() => {
      this.tick();
    });
  },
  methods: {
    openCertificate(certificate) {
      this.selectedCertificate = certificate;
    },
    closeCertificate() {
      this.selectedCertificate = null;
    },
    markCertificateUnavailable(certificate) {
      this.unavailableCertificateImages[certificate.filename] = true;
    },
    tick() {
      let typewriter = this.$refs.typewriter;

      if (!typewriter) {
        return;
      }

      let i = this.loopNum % this.toRotate.length;
      let fullTxt = this.toRotate[i];

      this.txt = this.isDeleting ? fullTxt.substring(0, this.txt.length - 1) : fullTxt.substring(0, this.txt.length + 1);
      typewriter.innerHTML = `<span class="wrap">${this.txt}</span>`;

      let that = this;
      let delta = 200 - Math.random() * 100;

      if (this.isDeleting) {
        delta /= 2;
      }

      if (!this.isDeleting && this.txt === fullTxt) {
        delta = this.period;
        this.isDeleting = true;
      } else if (this.isDeleting && this.txt === '') {
        this.isDeleting = false;
        this.loopNum++;
        delta = 500;
      }

      setTimeout(() => {
        that.tick();
      }, delta);
    },
  }
}
</script>

<style>
body {
  overflow-y: scroll;
  overflow-x: hidden;
}

.typewrite>.wrap {
  border-right: 0.08em solid #fff;
}

.wave {
  animation-name: wave-animation;
  animation-duration: 2.5s;
  animation-iteration-count: infinite;
  transform-origin: 70% 70%;
  display: inline-block
}

@keyframes wave-animation {
  0% {
    transform: rotate(0deg)
  }

  10% {
    transform: rotate(14deg)
  }

  20% {
    transform: rotate(-8deg)
  }

  30% {
    transform: rotate(14deg)
  }

  40% {
    transform: rotate(-4deg)
  }

  50% {
    transform: rotate(10deg)
  }

  60% {
    transform: rotate(0deg)
  }

  to {
    transform: rotate(0deg)
  }
}

.pict {
  box-shadow: 0px 0px 73px -9px rgba(255,219,112,0.44);
-webkit-box-shadow: 0px 0px 73px -9px rgba(255,219,112,0.44);
-moz-box-shadow: 0px 0px 73px -9px rgba(255,219,112,0.44);
}

.fadein-up {
  opacity: 0;
  animation-name: fadeInUp;
  animation-duration: 0.5s;
  animation-fill-mode: forwards;
  animation-delay: 500ms;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translate3d(0, 100%, 0);
  }

  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}

.fade-in-from-left {
  opacity: 0;
  animation: fadeInLeft 0.5s ease-out forwards;
  animation-delay: 500ms;
}

@keyframes fadeInLeft {
  0% {
    opacity: 0;
    transform: translateX(-100%);
  }
  100% {
    opacity: 1;
    transform: translateX(0);
  }
}

.fadein-right {
  opacity: 0;
  animation: fadeInRight 0.5s ease-out forwards;
  animation-delay: 500ms;
}

@keyframes fadeInRight {
  0% {
    opacity: 0;
    transform: translateX(100%);
  }
  100% {
    opacity: 1;
    transform: translateX(0);
  }
}

.fadein-bot {
  opacity: 0;
  animation: fadeInBot 0.5s forwards;
}

@keyframes fadeInBot {
  from {
    opacity: 0;
    transform: translate3d(0, -100%, 0);
  }

  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}

.fadein-1 {
  animation-delay: 200ms;
}
.fadein-2 {
  animation-delay: 400ms;
}
.fadein-3 {
  animation-delay: 600ms;
}
.fade-500 {
  animation-delay: 500ms;
}
</style>
