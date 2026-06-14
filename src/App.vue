<script setup>
import { ref } from 'vue'

const count = ref(0)
const increment = () => {
  count.value++
}
</script>

<template>
  <div class="app-wrapper">
    <!-- Background glowing blobs -->
    <div class="blob blob-green"></div>
    <div class="blob blob-purple"></div>

    <div class="container">
      <div class="glass-card">
        <!-- Logo or icon wrapper -->
        <div class="logo-wrapper">
          <svg class="vue-logo" viewBox="0 0 128 128" width="80" height="80">
            <path fill="#42b883" d="M78.8,10L64,35.4L49.2,10H0l64,110l64-110H78.8z"/>
            <path fill="#35495e" d="M78.8,10L64,35.4L49.2,10H25.6L64,76.5l38.4-66.5H78.8z"/>
          </svg>
        </div>

        <h1 class="title">Vue SFC & Composition API 🌟</h1>
        <p class="subtitle">2단계: 싱글 파일 컴포넌트와 현대적인 빌드 환경</p>
        
        <div class="counter-display">
          <span class="count-value" :key="count">{{ count }}</span>
        </div>

        <button class="interactive-btn" @click="increment">
          <span>카운트 증가하기</span>
          <div class="badge">{{ count }}</div>
        </button>

        <div class="info-footer">
          <p class="feature-tag">📁 <code>src/App.vue</code></p>
          <p class="feature-tag">⚡ Vite + ESBuild</p>
          <p class="feature-tag">♻️ Composition API</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Reset and layout */
.app-wrapper {
  position: relative;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: radial-gradient(circle at 50% 50%, #111827 0%, #030712 100%);
  font-family: 'Inter', var(--sans);
  overflow: hidden;
  width: 100%;
}

/* Floating background blobs */
.blob {
  position: absolute;
  border-radius: 50%;
  filter: blur(120px);
  opacity: 0.15;
  z-index: 0;
  animation: float 20s infinite alternate ease-in-out;
}
.blob-green {
  width: 450px;
  height: 450px;
  background: #42b883;
  top: -10%;
  left: 10%;
}
.blob-purple {
  width: 500px;
  height: 500px;
  background: #aa3bff;
  bottom: -10%;
  right: 10%;
  animation-delay: -5s;
}

@keyframes float {
  0% {
    transform: translate(0, 0) scale(1);
  }
  50% {
    transform: translate(50px, 30px) scale(1.1);
  }
  100% {
    transform: translate(-30px, -50px) scale(0.9);
  }
}

/* Glassmorphism Card Container */
.container {
  position: relative;
  z-index: 1;
  width: 100%;
  max-width: 520px;
  padding: 20px;
  box-sizing: border-box;
}

.glass-card {
  background: rgba(17, 24, 39, 0.7);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 24px;
  padding: 40px 30px;
  text-align: center;
  box-shadow: 0 20px 50px rgba(0, 0, 0, 0.4);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.glass-card:hover {
  transform: translateY(-4px);
  border-color: rgba(66, 184, 131, 0.2);
  box-shadow: 0 30px 60px rgba(66, 184, 131, 0.1);
}

/* Logo styling */
.logo-wrapper {
  margin-bottom: 24px;
  display: inline-block;
  padding: 16px;
  background: rgba(255, 255, 255, 0.03);
  border-radius: 20px;
  border: 1px solid rgba(255, 255, 255, 0.05);
  animation: pulseLogo 3s infinite ease-in-out;
}

.vue-logo {
  filter: drop-shadow(0 0 10px rgba(66, 184, 131, 0.3));
}

@keyframes pulseLogo {
  0%, 100% {
    transform: scale(1);
    box-shadow: 0 0 0 rgba(66, 184, 131, 0);
  }
  50% {
    transform: scale(1.05);
    box-shadow: 0 10px 30px rgba(66, 184, 131, 0.15);
  }
}

/* Typography */
.title {
  font-family: 'Outfit', sans-serif;
  font-size: 2.2rem;
  font-weight: 800;
  letter-spacing: -0.5px;
  margin: 0 0 10px 0;
  background: linear-gradient(135deg, #ffffff 30%, #a3e635 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.subtitle {
  color: #9ca3af;
  font-size: 1.05rem;
  font-weight: 400;
  margin-bottom: 35px;
  letter-spacing: 0.2px;
}

/* Counter display block */
.counter-display {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 120px;
  margin-bottom: 30px;
}

.count-value {
  font-family: 'Outfit', sans-serif;
  font-size: 5.5rem;
  font-weight: 800;
  color: #ffffff;
  text-shadow: 0 0 20px rgba(66, 184, 131, 0.4);
  animation: countPop 0.2s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

@keyframes countPop {
  0% {
    transform: scale(0.8);
    opacity: 0.5;
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}

/* Interactive Button */
.interactive-btn {
  position: relative;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
  width: 100%;
  padding: 16px 24px;
  background: linear-gradient(135deg, #42b883 0%, #34d399 100%);
  color: #030712;
  font-size: 1.15rem;
  font-weight: 700;
  font-family: 'Inter', sans-serif;
  border: none;
  border-radius: 16px;
  cursor: pointer;
  box-shadow: 0 8px 25px rgba(66, 184, 131, 0.3);
  transition: all 0.25s cubic-bezier(0.25, 0.8, 0.25, 1);
  overflow: hidden;
}

.interactive-btn::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, #ffffff 0%, rgba(255, 255, 255, 0) 50%);
  opacity: 0.2;
  transition: opacity 0.3s;
}

.interactive-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 12px 30px rgba(66, 184, 131, 0.5);
  background: linear-gradient(135deg, #4ed396 0%, #3ce2a5 100%);
}

.interactive-btn:active {
  transform: translateY(1px);
  box-shadow: 0 4px 15px rgba(66, 184, 131, 0.4);
}

.badge {
  display: flex;
  align-items: center;
  justify-content: center;
  background: #030712;
  color: #42b883;
  padding: 4px 10px;
  border-radius: 10px;
  font-size: 0.95rem;
  font-weight: 800;
  border: 1px solid rgba(66, 184, 131, 0.3);
}

/* Info tags at the bottom */
.info-footer {
  margin-top: 40px;
  padding-top: 25px;
  border-top: 1px solid rgba(255, 255, 255, 0.06);
  display: flex;
  justify-content: center;
  gap: 12px;
  flex-wrap: wrap;
}

.feature-tag {
  background: rgba(255, 255, 255, 0.04);
  color: #9ca3af;
  padding: 6px 12px;
  border-radius: 8px;
  font-size: 0.8rem;
  margin: 0;
  border: 1px solid rgba(255, 255, 255, 0.03);
}

code {
  color: #42b883;
  background: none;
  padding: 0;
}
</style>
