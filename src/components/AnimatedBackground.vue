<template>
  <div class="animated-bg" aria-hidden="true">
    <div class="scene">
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
    <div class="particle particle--one"></div>
    <div class="particle particle--two"></div>
    <div class="particle particle--three"></div>
    <div class="particle particle--four"></div>
  </div>
</template>

<script>
export default {
  name: 'AnimatedBackground'
}
</script>

<style scoped>
.animated-bg {
  position: absolute;
  inset: 0;
  overflow: hidden;
  pointer-events: none;
  z-index: 0;
  background: radial-gradient(circle at top left, rgba(78, 164, 255, 0.15), transparent 25%),
    radial-gradient(circle at bottom right, rgba(255, 194, 76, 0.12), transparent 28%),
    radial-gradient(circle at 30% 35%, rgba(115, 239, 255, 0.08), transparent 22%);
}

.scene {
  position: absolute;
  inset: 0;
  perspective: 1200px;
}

.cube {
  position: absolute;
  width: 120px;
  height: 120px;
  transform-style: preserve-3d;
  animation: rotateCube 12s linear infinite;
}

.cube--one {
  top: 10%;
  left: 12%;
  animation-duration: 14s;
}

.cube--two {
  top: 40%;
  right: 10%;
  width: 100px;
  height: 100px;
  animation-duration: 10s;
}

.cube--three {
  bottom: 8%;
  left: 45%;
  width: 140px;
  height: 140px;
  animation-duration: 16s;
}

.face {
  position: absolute;
  width: 100%;
  height: 100%;
  border: 1px solid rgba(255, 255, 255, 0.18);
  background: rgba(16, 185, 129, 0.08);
  backdrop-filter: blur(8px);
  box-shadow: 0 0 60px rgba(56, 189, 248, 0.17);
}

.face--front  { transform: translateZ(60px); }
.face--back   { transform: rotateY(180deg) translateZ(60px); }
.face--right  { transform: rotateY(90deg) translateZ(60px); }
.face--left   { transform: rotateY(-90deg) translateZ(60px); }
.face--top    { transform: rotateX(90deg) translateZ(60px); }
.face--bottom { transform: rotateX(-90deg) translateZ(60px); }

@keyframes rotateCube {
  0%   { transform: rotateX(0deg) rotateY(0deg) translateZ(0); }
  25%  { transform: rotateX(25deg) rotateY(45deg) translateZ(0); }
  50%  { transform: rotateX(45deg) rotateY(90deg) translateZ(0); }
  75%  { transform: rotateX(25deg) rotateY(135deg) translateZ(0); }
  100% { transform: rotateX(0deg) rotateY(180deg) translateZ(0); }
}

.particle {
  position: absolute;
  border-radius: 999px;
  background: rgba(59, 130, 246, 0.14);
  box-shadow: 0 0 40px rgba(56, 189, 248, 0.25);
  animation: float 8s ease-in-out infinite alternate;
}

.particle--one {
  width: 80px;
  height: 80px;
  top: 18%;
  right: 16%;
}

.particle--two {
  width: 56px;
  height: 56px;
  top: 60%;
  left: 14%;
  animation-duration: 10s;
}

.particle--three {
  width: 12px;
  height: 12px;
  bottom: 28%;
  right: 32%;
  background: rgba(249, 115, 22, 0.6);
  box-shadow: 0 0 20px rgba(249, 115, 22, 0.4);
  animation-duration: 6s;
}

.particle--four {
  width: 20px;
  height: 20px;
  bottom: 18%;
  left: 46%;
  background: rgba(34, 197, 94, 0.7);
  box-shadow: 0 0 24px rgba(34, 197, 94, 0.35);
  animation-duration: 7s;
}

@keyframes float {
  from { transform: translate3d(0, 0, 0) scale(1); }
  to { transform: translate3d(-12px, 22px, 0) scale(1.08); }
}
</style>
