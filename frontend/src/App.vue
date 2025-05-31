<script setup lang="ts">
import { RouterView } from 'vue-router'
import NavBar from "@/components/NavBar.vue"
import FooterSection from "@/components/FooterSection.vue"
</script>

<template>
  <div>
    <Transition name="slide-fade" appear>
      <RouterView />
    </Transition>
  </div>
</template>

<style>
:root {
  --primary-bg: #020202;
  --secondary-bg: #1a1a1a;
  --accent: #4ECDC4;
  --accent-secondary: #FF6B6B;
  --text-primary: #F4F4F4;
  --text-secondary: #888;
  --card-bg: rgba(255, 255, 255, 0.05);
}

html {
  box-sizing: border-box;
  overflow-x: hidden;
}

*, *:before, *:after {
  box-sizing: inherit;
}

body {
  position: relative;
  max-width: 100vw;
  overflow-x: hidden;
}

body {
  margin: 0; /* Add this line */
  padding: 0; /* Add this line */
  background: var(--primary-bg);
  color: var(--text-primary);
  font-family: 'Inter', sans-serif;
}

::-webkit-scrollbar {
  width: 6px;
  background: var(--primary-bg);
}

::-webkit-scrollbar-track {
    background: rgb(14, 15, 17);
}

::-webkit-scrollbar-thumb {
  background: var(--accent);
  border-radius: 4px;
}

::-webkit-scrollbar-track-piece:end {
    background: transparent;
}

::-webkit-scrollbar-track-piece:start {
    background: transparent;
}

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}

.float {
  animation: float 3s ease-in-out infinite;
}
</style>