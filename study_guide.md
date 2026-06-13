# Vue.js 초심자를 위한 학습 가이드 & 로드맵 🚀

## 📌 로드맵 개요 (Roadmap Overview)
Vue.js는 학습 곡선이 낮고 직관적인 UI 프레임워크입니다. 이 가이드는 CDN 방식의 기초적인 Hello World부터 시작하여, 현대적인 Vite + Composition API 기반의 Single File Component(SFC), 그리고 Vue Router와 Pinia를 활용한 본격적인 애플리케이션 개발까지의 5단계 로드맵을 제공합니다.

### 🗺️ 전체 학습 로드맵 (5단계)
1. **1단계: Vue Foundations (기초 - CDN 방식)**
   - **목표**: 빌드 도구 없이 HTML 파일 하나로 Vue 작동 원리 이해하기
   - **키워드**: Declarative Rendering, Directives (`v-if`, `v-for`, `v-model`, `v-bind`), Event Handling (`@click`), Computed Properties
2. **2단계: Modern Tooling & SFC (현대적 빌드 도구와 SFC)**
   - **목표**: Node.js 환경에서 Vite를 사용해 Vue 개발 환경 구축하기
   - **키워드**: Node.js, Vite, Single File Component (SFC: `.vue`), `<script setup>` (Composition API)
3. **3단계: Component Deep Dive (컴포넌트 심화)**
   - **목표**: 컴포넌트 간 데이터 흐름과 라이프사이클 마스터하기
   - **키워드**: Props & Emits, Provide / Inject, Lifecycle Hooks, Template Refs
4. **4단계: Routing & State Management (라우팅과 전역 상태 관리)**
   - **목표**: 다중 페이지 애플리케이션(SPA) 구축 및 데이터 관리
   - **키워드**: Vue Router, Pinia, API 데이터 통신 (Axios / Fetch)
5. **5단계: Advanced & Production (실전 애플리케이션 & 배포)**
   - **목표**: 성능 최적화, 커스텀 컴포저블(Composables), 빌드 및 GitHub Pages 배포
   - **키워드**: Composables, Vue DevTools, GitHub Actions/Pages 배포

---

## 📂 학습 가이드 (Study Guide)

### 1단계: Vue Foundations (기초 - CDN 방식)
빌드 도구(npm, Vite 등)를 사용하지 않고 간단하게 HTML 파일 하나로 Vue를 체험합니다.

#### 📄 첫 번째 예제: HelloWorld.html
다음 코드를 작성하여 브라우저에서 직접 실행해 보세요.
```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Vue Hello World</title>
  <!-- Vue 3 CDN 가져오기 -->
  <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: #1a1a2e;
      color: #e2e8f0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
    .card {
      background: #162447;
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
      text-align: center;
    }
    input {
      padding: 8px 12px;
      border-radius: 6px;
      border: 1px solid #1f4068;
      background: #1f4068;
      color: white;
      margin-top: 10px;
      width: 80%;
      outline: none;
    }
    input:focus {
      border-color: #42b883;
    }
  </style>
</head>
<body>

  <div id="app">
    <div class="card">
      <!-- 이중 중괄호(Mustache)를 사용한 데이터 렌더링 -->
      <h1>{{ message }}</h1>
      <p>실시간 타이핑 반영:</p>
      <!-- 양방향 데이터 바인딩 (v-model) -->
      <input type="text" v-model="message" placeholder="메시지를 입력해보세요">
    </div>
  </div>

  <script>
    const { createApp, ref } = Vue;

    // Vue 애플리케이션 인스턴스 생성
    createApp({
      setup() {
        // 반응형 데이터 정의
        const message = ref('Hello, Vue 3!');

        return {
          message
        }
      }
    }).mount('#app'); // #app 요소에 마운트
  </script>
</body>
</html>
```

#### ✍️ 실습 미션 1: 카운터 앱 만들기
- 버튼을 누르면 숫자가 증가/감소하는 카운터 앱을 CDN 방식을 이용해 만드세요.
- 키워드: `v-on:click` 또는 `@click`, `ref`

---

### 2단계: Modern Tooling & SFC (Vite & Composition API)
컴포넌트를 별도의 `.vue` 파일로 분리하고, 현대적인 JS 문법과 CSS 모듈성을 제공하는 싱글 파일 컴포넌트(SFC)를 사용해 프로젝트를 구성합니다.

#### 🛠️ 프로젝트 세팅하기
현재 폴더(`my-vue-study`)에 Vite를 사용해 새로운 Vue 프로젝트를 만듭니다.
1. 터미널을 열고 다음 명령어를 실행합니다.
   ```bash
   npm create vue@latest .
   # 또는
   npm init vite@latest . -- --template vue
   ```
2. 프로젝트 설정을 묻는 프롬프트에 답변을 완료한 후 라이브러리를 설치합니다.
   ```bash
   npm install
   ```
3. 개발 서버를 실행합니다.
   ```bash
   npm run dev
   ```

#### 📄 SFC 예제 (App.vue)
`<script setup>` 문법은 Vue 3에서 적극 권장하는 modern Composition API 방식입니다.
```vue
<script setup>
import { ref } from 'vue'

const count = ref(0)
const increment = () => {
  count.value++
}
</script>

<template>
  <div class="container">
    <h1>Vue SFC & Composition API 🌟</h1>
    <button @click="increment">카운트: {{ count }}</button>
  </div>
</template>

<style scoped>
.container {
  max-width: 600px;
  margin: 50px auto;
  text-align: center;
}
button {
  background-color: #42b883;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1.1rem;
}
button:hover {
  background-color: #35495e;
}
</style>
```

---

### 3단계: Component Deep Dive (컴포넌트 심화)
컴포넌트를 쪼개어 재사용하고 서로 통신하는 방법을 배웁니다.

- **Props**: 부모 컴포넌트가 자식 컴포넌트에 데이터를 전달할 때 사용 (`defineProps`)
- **Emits**: 자식 컴포넌트가 부모 컴포넌트에게 이벤트를 알릴 때 사용 (`defineEmits`)
- **Lifecycle Hooks**: 컴포넌트가 생성되고 마운트(화면 표시), 소멸될 때의 시점을 다룹니다 (`onMounted`, `onUnmounted`)

#### ✍️ 실습 미션 2: 투두 리스트(Todo List) 컴포넌트화하기
- 전체 리스트를 관리하는 `TodoList.vue` 부모 컴포넌트를 만드세요.
- 개별 투두 항목을 렌더링하는 `TodoItem.vue` 자식 컴포넌트를 만드세요.
- 자식 컴포넌트에서 삭제 버튼을 누르면 부모 컴포넌트로 삭제 요청(Emit)을 보내 부모의 배열 데이터를 갱신하게 하세요.

---

### 4단계: State Management & Routing
여러 페이지를 가진 앱과, 여러 컴포넌트가 공통으로 공유하는 데이터를 관리하는 전역 상태 관리를 구현합니다.

- **Vue Router**: URL에 따라 화면을 다르게 보여주는 라우팅 도구.
- **Pinia**: Vue 3 공식 상태 관리 라이브러리로, 쇼핑카트나 사용자 로그인 정보처럼 모든 곳에서 접근해야 하는 데이터를 다루는 데 최적입니다.

---

### 5단계: Advanced & Production
- **Composables**: 공통 로직(예: LocalStorage에 데이터 동기화하기, API 요청 처리 등)을 함수로 분리하여 여러 컴포넌트에서 재사용합니다. (`useLocalStorage`, `useFetch` 등)
- **Deployment**: 완성한 Vue 프로젝트를 빌드(`npm run build`)하여 Netlify, Vercel 혹은 GitHub Pages에 배포합니다.

---

## 🔗 학습 추천 공식 리소스
- [Vue.js 공식 문서 (한국어)](https://ko.vuejs.org/)
- [Vue Router 공식 문서](https://router.vuejs.org/)
- [Pinia 공식 문서](https://pinia.vuejs.org/)
- [Vite 공식 가이드](https://ko.vitejs.dev/)
