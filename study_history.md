# 📝 Vue.js 학습 기록 (Study History)

이 파일은 매일 학습한 내용을 기록하고 발전 상황을 추적하는 공간입니다. 학습한 내용, 마주한 문제와 해결법, 소감 등을 편하게 남겨보세요!

## 💡 기록 템플릿
```markdown
### 📅 [날짜 / Day N]
- **오늘의 학습 목표**: 
- **학습한 내용 / 키워드**:
- **작성한 예제 / 프로젝트**:
- **어려웠던 점 & 해결 과정**:
- **내일의 계획**:
```

---

## 📈 학습 일지 (History Logs)

### 📅 Day 1 (2026-06-13)
- **오늘의 학습 목표**: Vue.js 학습 로드맵 설정, HelloWorld 예제 생성, 카운터 앱 만들기
- **학습한 내용 / 키워드**:
  - Vue 3 CDN 가져오기 (`<script src="...">`)
  - Vue 인스턴스 생성 및 HTML 마운트 (`createApp`, `mount`)
  - 반응성 데이터 선언 (`ref`), 스크립트 내에서 `.value` 수정
  - 이벤트 처리 (`@click`) 및 동적 클래스 바인딩 (`:class`)
- **작성한 예제 / 프로젝트**:
  - [HelloWorld.html](file:///d:/my-vue-study/HelloWorld.html): 이중 중괄호(`{{ message }}`)와 `v-model` 양방향 바인딩
  - [Counter.html](file:///d:/my-vue-study/Counter.html): `ref`와 `@click`을 사용한 실시간 카운터 앱
- **어려웠던 점 & 해결 과정**:
  - 스크립트 영역에서 `ref` 변수를 조작할 때는 꼭 `.value`를 붙여야 하지만, HTML 영역(`template`)에서는 자동으로 풀려서(unwrapping) `{{ count }}`처럼 변수명만 쓰면 된다는 점을 배움.
- **내일의 계획**:
  - 2단계로 넘어가 Vite를 활용해 로컬 Vue 개발 환경 구축해보기

### 📅 Day 2 (2026-06-14)
- **오늘의 학습 목표**: Vite를 활용한 Vue 3 개발 환경 구축 및 싱글 파일 컴포넌트(SFC)와 Composition API 기초 학습
- **학습한 내용 / 키워드**:
  - Vite 프로젝트 초기화 (`create-vite`) 및 기존 파일 보호를 위한 세팅 정리
  - 싱글 파일 컴포넌트(SFC: `.vue`) 구조 (`<script setup>`, `<template>`, `<style scoped>`) 이해
  - Google Fonts(Outfit, Inter)와 Glassmorphic CSS 레이아웃, 애니메이션을 적용한 인터랙티브 UI 구현
- **작성한 예제 / 프로젝트**:
  - [App.vue](file:///d:/my-vue-study/src/App.vue): 현대적이고 반응성이 높은 카운터 SFC 예제
- **어려웠던 점 & 해결 과정**:
  - 기존의 소중한 파일들(`study_guide.md`, `Counter.html` 등)이 유실되는 것을 방지하기 위해, 임시 폴더에서 Vite 프로젝트를 스캐폴딩한 후 루트 디렉토리로 안전하게 설정과 코드를 이관 및 정비하는 방식으로 문제를 해결함.
- **내일의 계획**:
  - 3단계: Component Deep Dive (컴포넌트 심화) 진입 및 부모-자식 컴포넌트 간 Props & Emits 기반의 Todo List 컴포넌트 설계 및 구현
