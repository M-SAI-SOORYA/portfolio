<script setup lang="ts">
import { useRouter } from 'vue-router'
import IntroSection from '@/components/IntroSection.vue'
import ExperienceSection from '@/components/ProjectSection.vue'
import WorkSection from '@/components/WorkSection.vue'
import TechSection from '@/components/TechSection.vue'
import FooterSection from "@/components/FooterSection.vue";
import NavBar from "@/components/NavBar.vue";

const router = useRouter()

const goToAbout = () => {
  router.push('/about')
}
</script>

<template>
  <NavBar />
  <IntroSection />
  <!-- <WorkSection /> -->
  <ExperienceSection />
  <TechSection />
  <FooterSection />
</template>

<style>
</style>
