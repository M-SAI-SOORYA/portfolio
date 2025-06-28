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
    <ProjectComponent
        title="AI Agent and Q&A Bot"
        :description="[
          'This project comprises two AI-powered chatbots built with Streamlit and FastAPI, leveraging the Groq API and using LLaMA-3.3-70B model',
          ' The AI Agent Search employs a ReAct AI agent to answer general queries using DuckDuckGo, Wikipedia, and Arxiv tools, streaming responses in real-time',
          'The PDF Q and A Chatbot processes uploaded PDFs for context-aware question-answering via a RAG pipeline with Chroma as vector store and HuggingFace embeddings'
        ]"
        :technologies="[
          { name: 'Langchain' },
          { name: 'FastAPI' },
          { name: 'Streamlit' },
          { name: 'Agent AI' },
          { name: 'RAG' }
       
        ]"
        gradientStart="rgba(88,94,240,0.7)"
        gradientEnd="rgba(40,47,150,1)"
        imageSrc="/assets/ai-blog-2.png.jpg"
        imageAlt="AI Agent QA Bot"
        githubLink="https://github.com/M-SAI-SOORYA/Agent-and-QA-Bot"
        VideoLink="https://drive.google.com/file/d/1dTo_w5p0ew-69ZuwDE_w50estl4LTltk/view"
      />

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
