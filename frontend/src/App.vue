<script setup lang="ts">
import { RouterView } from 'vue-router'
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
  --primary-bg: #050607;
  --accent: #83f7bd;
  --text-primary: #f7f7ef;
}

html {
  box-sizing: border-box;
  overflow-x: hidden;
  scroll-behavior: smooth;
  background: var(--primary-bg);
}

*, *:before, *:after {
  box-sizing: inherit;
}

body {
  position: relative;
  max-width: 100vw;
  margin: 0;
  padding: 0;
  overflow-x: hidden;
  background: var(--primary-bg);
  color: var(--text-primary);
  font-family: 'Gilroy Regular', system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  text-rendering: geometricPrecision;
}

button,
input,
textarea,
select {
  font: inherit;
}

::-webkit-scrollbar {
  width: 6px;
  background: var(--primary-bg);
}

::-webkit-scrollbar-track {
  background: #050607;
}

::-webkit-scrollbar-thumb {
  background: var(--accent);
  border-radius: 4px;
}
</style>
