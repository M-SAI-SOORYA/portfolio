<script setup lang="ts">
import { ref } from 'vue'

defineProps<{
  logo: string
  company: string
  role: string
  startDate: string
  endDate: string
  location: string
  bulletPoints: string[]
  websiteUrl: string
  technologies?: string[]
}>()

const openWork = (website: string, event: Event) => {
  event.stopPropagation()
  window.open(website, '_blank')
}
</script>

<template>
  <div class="job-card">
    <div class="timeline">
      <div class="date">{{ startDate }} - {{ endDate }}</div>
      <div class="logo-container" @click.stop="openWork(websiteUrl, $event)">
        <img :src="logo" :alt="company" class="company-logo"/>
      </div>
    </div>

    <div class="content">
      <h3 class="company">{{ company }}</h3>
      <div class="role-location">
        <span class="role">{{ role }}</span>
        <span class="location">{{ location }}</span>
      </div>

      <div class="details">
        <div v-for="(point, index) in bulletPoints" :key="index" class="bullet">
          <div class="bullet-icon"></div>
          <p class="bullet-text">{{ point }}</p>
        </div>
      </div>

      <div v-if="technologies" class="tech-stack">
        <span v-for="tech in technologies" :key="tech" class="tech-tag">
          {{ tech }}
        </span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.job-card {
  display: grid;
  grid-template-columns: 180px 1fr;
  gap: 2rem;
  padding: 1rem;
  margin: 2rem auto; /* Center align */
  max-width: 100%; /* Ensure cards take up the full width of their container */
  width: calc(100% - 20rem); /* Add padding for responsiveness */
  background: rgba(30, 30, 30, 0.6);
  border-radius: 16px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.job-card:hover {
  transform: translateY(-5px);
  border-color: #4ECDC4;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
}

.timeline {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}

.date {
  color: #bdc3cb;
  font-family: 'Gilroy Medium';
  font-size: 1rem;
  text-align: center;
  white-space: nowrap;
}

.logo-container {
  width: 80px;
  height: 80px;
  background: white;
  border-radius: 12px;
  padding: 12px;
  display: grid;
  place-items: center;
  cursor: pointer;
  transition: transform 0.3s ease;
}

.logo-container:hover {
  transform: scale(1.05);
}

.company-logo {
  width: 100%;
  height: 100%;
  object-fit: contain;
  max-width: 100%;
  max-height: 100%;
}

.content {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.company {
  font-size: 1.5rem;
  color: #eaecef;
  margin: 0;
  font-family: 'Gilroy Bold';
}

.role-location {
  display: flex;
  gap: 1rem;
  align-items: center;
  margin-bottom: 1rem;
}

.role {
  color: #4ECDC4;
  font-family: 'Gilroy Medium';
  font-size: 1rem;
}

.location {
  color: #8b949e;
  font-size: 0.9rem;
}

.details {
  margin-top: 0.5rem;
}

.bullet {
  display: flex;
  gap: 1rem;
  margin-bottom: 1rem;
  padding-left: 1rem;
  position: relative;
}

.bullet-icon {
  flex-shrink: 0;
  width: 8px;
  height: 8px;
  background: #4ECDC4;
  transform: rotate(45deg);
  margin-top: 0.5rem;
}

.bullet-text {
  margin: 0;
  line-height: 1.6;
  color: #bcc6d1;
}

.tech-stack {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-top: 1.5rem;
}

.tech-tag {
  background: rgba(78, 205, 196, 0.1);
  color: #4ECDC4;
  padding: 0.4rem 1rem;
  border-radius: 20px;
  font-size: 0.85rem;
  border: 1px solid rgba(78, 205, 196, 0.3);
  transition: all 0.3s ease;
}

.tech-tag:hover {
  background: rgba(78, 205, 196, 0.2);
  transform: translateY(-2px);
}

@media (max-width: 768px) {
  .job-card {
    grid-template-columns: auto; /* Single-column layout */
    width: calc(100% - 2rem); /* Adjust width for padding */
    padding: 1.5rem;
    gap: 1.5rem;
    max-width: unset; /* Remove width constraints for responsiveness */
    margin-left: auto;
    margin-right: auto; /* Center align on small screens */
  }

  .timeline {
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
  }

  .logo-container {
    width: 60px;
    height: 60px;
    padding: 8px;
  }

  .role-location {
    flex-direction: column;
    align-items: flex-start;
    gap: 0.25rem;
  }
}
</style>
