<script setup lang="ts">
import { ref } from 'vue';

const sendContact = () => {
  window.location.href = 'mailto:sooryamarri@gmail.com';
}

// const openLeetCode = () => {
//   window.location.href = 'https://leetcode.com/u/sooryamarri/';
// }

const openResume = () => {
  window.open('/sai_soorya_marri_resume_2025.pdf', '_blank');
}

const visible = ref(true)
</script>

<template>
  <nav class="navbar" :class="{ hidden: !visible }">
    <!-- Left Icons -->
    <div class="nav-group left">
      <button @click="sendContact" class="nav-button" title="Contact">
        <i class="icon email-icon"></i>
      </button>
      <button @click="openResume" class="nav-button" title="Resume">
        <i class="icon resume-icon"></i>
      </button>
      <!-- <button @click="openLeetCode" class="nav-button" title="Resume">
        <i class="icon resume-icon"></i>
      </button> -->
    </div>

    <!-- Right Icons -->
    <div class="nav-group right">
      <a href="https://github.com/M-SAI-SOORYA" target="_blank" class="nav-button">
        <i class="icon github-icon"></i>
      </a>
      <a href="https://www.linkedin.com/in/soorya-marri-466086233/" target="_blank" class="nav-button">
        <i class="icon linkedin-icon"></i>
      </a>
    </div>
  </nav>
</template>

<style scoped>


.navbar {
  position: fixed;
  top: 1.5rem;
  left: 0;
  right: 0;
  z-index: 1000;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.navbar.hidden {
  transform: translateY(-150%);
}

.nav-group {
  position: absolute;
  display: flex;
  gap: 1.25rem;
}

.nav-group.left {
  left: 2rem;
}

.nav-group.right {
  right: 2rem;
}

.nav-button {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: rgba(30, 30, 30, 0.95);
  backdrop-filter: blur(12px);
  display: grid;
  place-items: center;
  border: 1px solid rgba(255, 255, 255, 0.15);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: pointer;
}

.nav-button:hover {
  background: #4ECDC4;
  transform: scale(1.1);
  border-color: transparent;
}

.icon {
  width: 24px;
  height: 24px;
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
}

@media (max-width: 768px) {
  .nav-group {
    gap: 1rem;
  }

  .nav-group.left {
    left: 1rem;
  }

  .nav-group.right {
    right: 1rem;
  }

  .nav-button {
    width: 42px;
    height: 42px;
  }

  .icon {
    width: 20px;
    height: 20px;
  }
}

.email-icon {
  background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="%23ffffff" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>');
}

.resume-icon {
  background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="%23ffffff" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/><polyline points="10 9 9 9 8 9"/></svg>');
}

.github-icon {
  background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="%23ffffff" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"/></svg>');
}
.leet-icon{
    background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="%23ffffff" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/><polyline points="10 9 9 9 8 9"/></svg>');

}
.linkedin-icon {
  background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="%23ffffff" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"/><rect x="2" y="9" width="4" height="12"/><circle cx="4" cy="4" r="2"/></svg>');
}
</style>
