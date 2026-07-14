<template>
  <div class="relative min-h-screen overflow-hidden text-amber-50">
    <FullScreen3DBackground />
    <div class="relative z-10 px-5 py-10 md:px-12">
      <article class="bg-[#111827]/[0.92] border border-[#009dff]/30 rounded-3xl p-8 shadow-[0_0_80px_rgba(0,0,0,0.35)] mx-auto max-w-4xl backdrop-blur-xl">
        <header class="mb-8">
        <h1 class="text-3xl font-bold text-white mb-3">Resume / CV</h1>
        <p class="text-sm text-slate-300">Download or view my resume directly from Google Drive.</p>
      </header>

      <section class="space-y-6">
        <div class="rounded-3xl border border-amber-200/20 bg-[#151515] p-6">
          <h2 class="text-xl font-semibold text-amber-200 mb-3">Google Drive Resume</h2>
          <p class="text-sm text-slate-300 mb-4">
            Klik tombol di bawah untuk membuka resume saya di Google Drive. Anda dapat melihat atau mengunduhnya dari sana.
          </p>
          <div class="flex flex-col gap-4 sm:flex-row sm:items-center">
            <a
              href="https://drive.google.com/drive/folders/1cAkW_xERw6Y0hM1xBthedvELrCgGfbfE?usp=sharing"
              target="_blank"
              rel="noreferrer noopener"
              class="inline-flex items-center justify-center rounded-full bg-amber-200 px-6 py-3 text-sm font-semibold text-[#101010] transition hover:bg-amber-300"
            >
              Buka Resume di Google Drive
            </a>
            <a
              href="https://drive.google.com/drive/folders/1cAkW_xERw6Y0hM1xBthedvELrCgGfbfE?usp=sharing"
              target="_blank"
              rel="noreferrer noopener"
              class="inline-flex items-center justify-center rounded-full border border-amber-200 bg-transparent px-6 py-3 text-sm font-semibold text-amber-200 transition hover:bg-amber-200 hover:text-[#101010]"
            >
              Unduh Resume
            </a>
          </div>
        </div>
      </section>
    </article>
  </div>
</div>
</template>

<script>
import FullScreen3DBackground from '@/components/FullScreen3DBackground.vue'

export default {
  name: 'ResumeView',
  components: {
    FullScreen3DBackground
  }
}
</script>

<style scoped>
</style>
