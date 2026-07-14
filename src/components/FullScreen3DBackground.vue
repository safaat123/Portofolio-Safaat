<template>
  <div class="full-screen-bg" aria-hidden="true">
    <div class="bg-grid"></div>
    <div class="scene">
      <div class="wireframe wireframe--one"></div>
      <div class="wireframe wireframe--two"></div>
      <div class="cube cube--one">
        <div class="face face--front"></div>
        <div class="face face--back"></div>
        <div class="face face--right"></div>
        <div class="face face--left"></div>
        <div class="face face--top"></div>
        <div class="face face--bottom"></div>
      </div>
      <div class="cube cube--two">
        <div class="face face--front"></div>
        <div class="face face--back"></div>
        <div class="face face--right"></div>
        <div class="face face--left"></div>
        <div class="face face--top"></div>
        <div class="face face--bottom"></div>
      </div>
      <div class="cube cube--three">
        <div class="face face--front"></div>
        <div class="face face--back"></div>
        <div class="face face--right"></div>
        <div class="face face--left"></div>
        <div class="face face--top"></div>
        <div class="face face--bottom"></div>
      </div>
    </div>
    <div class="glow glow--one"></div>
    <div class="glow glow--two"></div>
    <div class="spark spark--one"></div>
    <div class="spark spark--two"></div>
  </div>
</template>

<script>
export default {
  name: 'FullScreen3DBackground'
}
</script>

<style scoped>
.full-screen-bg {
  position: fixed;
  inset: 0;
  z-index: -1;
  overflow: hidden;
  background: radial-gradient(circle at top left, rgba(59, 130, 246, 0.18), transparent 18%),
    radial-gradient(circle at bottom right, rgba(16, 185, 129, 0.16), transparent 22%),
    linear-gradient(180deg, rgba(10, 14, 35, 0.96), rgba(8, 18, 46, 0.98));
}

.bg-grid {
  position: absolute;
  inset: 0;
  background-image: linear-gradient(rgba(255,255,255,0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,0.03) 1px, transparent 1px);
  background-size: 70px 70px;
  opacity: 0.12;
}

.scene {
  position: absolute;
  inset: 0;
  perspective: 1400px;
}

.wireframe {
  position: absolute;
  border: 1px solid rgba(96, 165, 250, 0.22);
  box-shadow: 0 0 80px rgba(56, 189, 248, 0.14);
  opacity: 0.75;
  transform-style: preserve-3d;
}

.wireframe--one {
  width: 420px;
  height: 420px;
  left: 10%;
  top: 12%;
  transform: rotate(18deg);
  animation: pulseFrame 20s ease-in-out infinite;
}

.wireframe--two {
  width: 360px;
  height: 360px;
  right: 8%;
  bottom: 10%;
  transform: rotate(-24deg);
  animation: pulseFrame 25s ease-in-out infinite reverse;
}

.cube {
  position: absolute;
  width: 110px;
  height: 110px;
  transform-style: preserve-3d;
  animation: rotateCube 14s ease-in-out infinite;
}

.cube--one {
  left: 16%;
  top: 18%;
  animation-duration: 15s;
}

.cube--two {
  right: 16%;
  top: 32%;
  width: 90px;
  height: 90px;
  animation-duration: 10s;
  animation-delay: 1.2s;
}

.cube--three {
  left: 32%;
  bottom: 14%;
  width: 130px;
  height: 130px;
  animation-duration: 18s;
  animation-delay: 0.8s;
}

.face {
  position: absolute;
  width: 100%;
  height: 100%;
  border: 1px solid rgba(255, 255, 255, 0.12);
  background: rgba(14, 165, 233, 0.09);
  backdrop-filter: blur(8px);
  box-shadow: inset 0 0 28px rgba(56, 189, 248, 0.12);
}

.face--front { transform: translateZ(55px); }
.face--back { transform: rotateY(180deg) translateZ(55px); }
.face--right { transform: rotateY(90deg) translateZ(55px); }
.face--left { transform: rotateY(-90deg) translateZ(55px); }
.face--top { transform: rotateX(90deg) translateZ(55px); }
.face--bottom { transform: rotateX(-90deg) translateZ(55px); }

.glow {
  position: absolute;
  border-radius: 50%;
  filter: blur(34px);
  opacity: 0.8;
}

.glow--one {
  width: 320px;
  height: 320px;
  top: 6%;
  left: 8%;
  background: rgba(56, 189, 248, 0.16);
  animation: driftGlow 24s ease-in-out infinite;
}

.glow--two {
  width: 240px;
  height: 240px;
  bottom: 6%;
  right: 12%;
  background: rgba(34, 197, 94, 0.12);
  animation: driftGlow 21s ease-in-out infinite reverse;
}

.spark {
  position: absolute;
  border-radius: 999px;
  background: rgba(248, 113, 113, 0.7);
  box-shadow: 0 0 32px rgba(248, 113, 113, 0.35);
  animation: floatSpark 10s ease-in-out infinite;
}

.spark--one {
  width: 18px;
  height: 18px;
  top: 22%;
  right: 24%;
  animation-duration: 8s;
}

.spark--two {
  width: 12px;
  height: 12px;
  bottom: 20%;
  left: 26%;
  background: rgba(16, 185, 129, 0.75);
  box-shadow: 0 0 28px rgba(16, 185, 129, 0.35);
  animation-duration: 6.5s;
}

@keyframes rotateCube {
  0% { transform: rotateX(0deg) rotateY(0deg) translateZ(0); }
  25% { transform: rotateX(24deg) rotateY(90deg) translateZ(0); }
  50% { transform: rotateX(42deg) rotateY(180deg) translateZ(0); }
  75% { transform: rotateX(24deg) rotateY(270deg) translateZ(0); }
  100% { transform: rotateX(0deg) rotateY(360deg) translateZ(0); }
}

@keyframes pulseFrame {
  0%, 100% { opacity: 0.78; transform: translate3d(0, 0, 0) rotate(0deg); }
  50% { opacity: 0.38; transform: translate3d(12px, -14px, 0) rotate(4deg); }
}

@keyframes driftGlow {
  0%, 100% { transform: translate3d(0, 0, 0); }
  50% { transform: translate3d(12px, -18px, 0); }
}

@keyframes floatSpark {
  0%, 100% { transform: translate3d(0, 0, 0) scale(1); opacity: 0.9; }
  50% { transform: translate3d(-10px, 14px, 0) scale(1.1); opacity: 0.6; }
}
</style>
