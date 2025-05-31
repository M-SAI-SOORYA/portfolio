<script setup lang="ts">
import JobCard from '@/components/JobCard.vue'
</script>

<template>
  <section class="work-section">
    <h2 class="work-title">Professional Experience</h2>
    <div class="jobs-container">
      <JobCard
      logo="/assets/docusign.svg"
      company="Docusign"
      role="Incoming Software Engineering Intern"
      startDate="Jun. 2025"
      endDate="Aug. 2025"
      location="San Francisco Bay Area, CA"
      :technologies="['Node.js', 'Python', 'Salesforce', 'AWS']"
      :bulletPoints="[
        'Incoming summer 2025 ☀️',
        'Platform team 🚀'
      ]"
      websiteUrl="https://www.docusign.com/"
    />
      <JobCard
      logo="/assets/epics.jpg"
      company="epics@ASU"
      role="Backend Software Engineer"
      startDate="Jan. 2025"
      endDate="Present"
      location="Tempe, AZ"
      :technologies="['React Native', 'FastAPI', 'TypeScript', 'Python', 'PostgreSQL', 'AWS']"
      :bulletPoints="[
        'Documentation lead for the team, contributing to backend infrastructure of campus navigation app',
        'Optimized FastAPI endpoints to deliver 25+ campus amenities data in <80ms via Axios fetch calls',
        'Enforced code docs standards via GitHub PR reviews, accelerating team efficiency and organization'
      ]"
      websiteUrl="https://epics.engineering.asu.edu/"
    />
    <JobCard
      logo="/assets/soda.svg"
      company="The Software Developer's Association"
      role="Software Development Engineering Intern"
      startDate="Oct. 2024"
      endDate="Present"
      location="Tempe, AZ"
      :technologies="['Vue.js', 'JavaScript', 'Node.js', 'Express.js', 'MongoDB']"
      :bulletPoints="[
        'Architected Vue.js chat interface with WebSocket integration for real-time cross-platform message synchronization across Instagram and WhatsApp',
        'DBuilt and deployed REST API endpoints with Express and Node for secure message processing and retrieval',
        'Recognized as top-performing intern, presenting project to 100+ industry professionals at company showcase'
      ]"
      websiteUrl="https://thesoda.io/mentorship"
    />
    <JobCard
      logo="/assets/banner.svg"
      company="Banner Health"
      role="Software Engineer Intern"
      startDate="Mar. 2023"
      endDate="May 2023"
      location="Surprise, AZ"
      :bulletPoints="[
          'Minimized manual data entry errors by 25% by automating healthcare workflows using BluePrism',
          'Cut development time from 3 to 1.5 weeks by creating reusable BluePrism templates and schemas',
          'Built comprehensive RPA documentation enabling seamless operations team handoffs'
      ]"
      :technologies="['BluePrism', 'Python', 'RPA']"
      websiteUrl="https://www.bannerhealth.com/"
    />
    </div>
  </section>
</template>

<style scoped>
.job-card {
  box-sizing: border-box;
  min-width: 0; /* Fix flexbox overflow */
}

.work-section {
  padding: 2rem 1rem;
  max-width: calc(100% - 32rem);
  margin: 0 auto;
}

.work-title {
  text-align: center;
  font-family: 'Gilroy Bold', serif;
  font-size: 2.5rem;
  color: #eaecef;
  margin-bottom: 3rem;
}

.jobs-container {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  overflow-x: hidden;
}

@media (max-width: 768px) {
  .work-section {
    padding: 2rem 1rem;
    max-width: 100%;
  }

  .work-title {
    font-size: 2rem;
    margin-bottom: 2rem;
  }
}
</style>
