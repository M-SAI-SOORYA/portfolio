<!-- ProjectSection.vue -->
<script setup lang="ts">
import { onMounted } from 'vue'
import ProjectComponent from '@/components/ProjectComponent.vue'
</script>

<template>
  <section class="experience-section">
    <h2 class="experience-title">Featured Projects</h2>
    <div class="experience-container">
          <!-- Project 1-->
      <ProjectComponent
        title="Multi-Organ Segmentation"
        :description="[
          'Implemented a model UNETR-2D using Vision Transformer as encoder and CNN up-sampler as decoder to segment the organs from the input CT scan image through Deep Learning. Worked on this project with a team of 6 members.',
          'Developed a mobile application prototype for users’ efficient usage by giving the input CT scan and getting organ-segmented results (Generative Artificial Intelligence).'
        ]"
        :technologies="[
          { name: 'Python' },
          { name: 'TensorFlow' },
          { name: 'PyTorch' },
          { name: 'OpenCV' },
          { name: 'Flutter' },
          {name:'Generative AI'}
        ]"
        gradientStart="rgba(88,94,240,0.7)"
        gradientEnd="rgba(40,47,150,1)"
        imageSrc="/assets/most_image.png"
        imageAlt="Multi-Organ Segmentation"
        DocLink="https://drive.google.com/file/d/16oYCTS5EzThjcb5AJXsa6naOEONXX4KH/view"
        VideoLink="https://drive.google.com/file/d/1neIdlu4kfy0f37NwsvG-miXZKshvWgfq/view"
      />

      <!-- Project 2 -->
      <ProjectComponent
        title="Lost and Found"
        :description="[
          'Our team, consisting of five members, has successfully created a Web Application using the MERN stack. Presenting you the Lost and Found.',
          'Collaborated with a team to design and develop a Lost and Found platform for helping recover lost items within a college environment.',
          'Implemented key features like user authentication, item search, posting items, and contact/report submission to ensure secure and efficient interactions.',
          'Also worked on API development, documenting the process and code.'
        ]"
        :reverse="true"
        :technologies="[
          { name: 'MongoDB' },
          { name: 'Express.js' },
          { name: 'React.js' },
          { name: 'Node.js' },
          { name: 'HTML/CSS' },
          { name: 'JavaScript' }
        
        ]"
        gradientStart="rgb(52,211,153,0.8)"
        gradientEnd="rgba(35,197,94,0.8)"
        imageSrc="/assets/landf.png"
        imageAlt="Lost and Found"
        DocLink="https://drive.google.com/file/d/1aTZSTlC06-hV_0JbFB3Swtop9yJKMWmB/view"
        VideoLink="https://drive.google.com/file/d/1Dqwoiqqmgw7eZ67jpfQDNVx5TTz1oAvg/view"
      />


    <!-- Project 3-->
    <!-- <ProjectComponent
    title="findit."
      :description="[
        'findit. is an intelligent shopping assistant designed to guide users through the decision-making process.',
        'Interacting with the natural language chatbot, users can specify their needs, getting back 3-5 specific product recommendations.'
      ]"
      :technologies="[
        { name: 'Vue.js' },
        { name: 'JavaScript' },
        { name: 'Python' },
        { name: 'FastAPI' },
        { name: 'MongoDB' }
      ]"
      imageSrc="/assets/findit.png"
      imageAlt="findit. project"
      gradientStart="rgb(211,133,209,0.8)"
      gradientEnd="rgba(176,133,226,0.8)"
      githubLink="https://github.com/ZacharyHampton/sunhacks-2024"
      devpostLink="https://devpost.com/software/findit-lhqfgr"
      youtubeLink="https://www.youtube.com/watch?v=18lt6lk4K2E&ab_channel=SBBillusionist"
    /> -->
    </div>
  </section>
</template>

<style scoped>
.experience-section {
  padding: 4rem 24rem;
  max-width: 100%;
  width: 100%;
  box-sizing: border-box;
  margin: 0 auto;
}

.experience-title {
  text-align: center;
  font-family: 'Gilroy Bold', serif;
  font-size: 2.5rem;
  color: #eaecef;
  margin-bottom: 3rem;
}

.experience-container {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  overflow-x: hidden; /* Hide horizontal overflow */
}

@media (max-width: 768px) {
  .experience-section {
    padding: 2rem 1rem;
    width: 100%;
  }

  .experience-title {
    font-size: 2rem;
    margin-bottom: 2rem;
  }

  .experience-container {
    gap: 2rem;
  }
  .project-component {
    flex-direction: column;
    padding: 1rem;
  }
}
</style>hV_0JbFB3Swtop9yJKMWmB/view
