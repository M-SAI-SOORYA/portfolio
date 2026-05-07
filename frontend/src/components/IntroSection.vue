<script setup lang="ts">
import { useRouter } from 'vue-router'
import { onMounted } from 'vue'
import AOS from 'aos'

const router = useRouter()

const openResume = () => {
  window.open('/soorya_marri_resume_2025.pdf', '_blank');
}

const goToBlog = () => {
  router.push('/blog')
}

onMounted(() => {
  AOS.init()
})
</script>

<template>
  <section class="intro-section">
    <div class="content-wrapper">
      <div class="text-content">
        <div class="header-group">

          <h1 class="name">Sai Soorya Marri</h1>
          <h2 class="title">Software Engineer</h2>
        </div>

        <p class="description">
          I'm a Computer Science Graduate from Keshav Memorial Institute of Technology, passionate about building real-world use case projects that solve meaningful problems. My expertise lies in AI and software development, demonstrated through projects like a Multi-Organ Segmentation Transformer, achieving an 85% Dice score for medical imaging, and a MERN stack Lost and Found website that served 500+ users, reducing item recovery time by 30%. 
          With hands-on experience from an ECIL internship and open-source contributions, I’m driven to create impactful solutions and am eager to bring my skills to innovative companies.          
          Adios!
        </p>
        <p class="description">
          In my spare time when I'm not coding,
          you'll mostly find me  following Geopolitics and about the world...
        </p>

        <div class="action-buttons">
          <button @click="openResume" class="resume-button">
            View Resume
            <span class="button-icon">→</span>
          </button>
        </div>
      </div>

      <div class="avatar-container">
        <div cflass="avatar-frame">
          <img src="/assets/me2.jpg" alt="Sai Soorya Marri" class="avatar-image" />
          <div class="avatar-overlay"></div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.intro-section {
  padding: 6rem 0;
  background: radial-gradient(#0a0a0a 0%, #090909 100%);
  position: relative;
  overflow-x: hidden;
}

.content-wrapper {
  max-width: calc(100% - 24rem);
  margin: 0 auto;
  padding: 0 2rem;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
}

.text-content {
  position: relative;
  z-index: 2;
}

.header-group {
  margin-bottom: 2.5rem;
}

.name {
  font-size: 4rem;
  color: #eaecef;
  margin: 0;
  line-height: 1;
  font-family: 'Gilroy Bold', serif;
  position: relative;
  display: inline-block;
}

.name::after {
  content: '';
  position: absolute;
  bottom: -10px;
  left: 0;
  width: 60%;
  height: 3px;
  background: #4ECDC4;
}

.title {
  font-size: 1.8rem;
  color: #eaecef;
  margin: 1rem 0 0;
  font-family: 'Gilroy Medium', serif;
}

.description {
  font-size: 1.2rem;
  line-height: 1.7;
  color: #bcc6d1;
  max-width: 600px;
  margin-bottom: 2rem;
  font-family: 'Gilroy Regular', serif;
}

.action-buttons {
  display: flex;
  gap: 1.5rem;
}

.resume-button {
  background: #4ECDC4;
  color: #0a0a0a;
  border: none;
  padding: 1rem 2rem;
  border-radius: 50px;
  font-size: 1.1rem;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  gap: 0.75rem;
  font-family: 'Gilroy Medium', serif;
}

.resume-button:hover {
  transform: translateY(-3px);
  box-shadow: 0 4px 15px rgba(78, 205, 196, 0.3);
}

.button-icon {
  font-size: 1.25rem;
  transition: transform 0.3s ease;
}

.resume-button:hover .button-icon {
  transform: translateX(3px);
}

.avatar-container {
  position: relative;
  display: flex;
  justify-content: center;
}

.avatar-frame {
  width: 400px;
  height: 400px;
  border-radius: 25px;
  overflow: hidden;
  position: relative;
  transition: transform 0.3s ease;
  max-width: 100%;
}

.avatar-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.avatar-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(45deg, rgba(78, 205, 196, 0.1) 0%, rgba(78, 205, 196, 0) 100%);
  pointer-events: none;
}

.avatar-frame:hover {
  transform: translateY(-5px);
}

@media (max-width: 1200px) {
  .content-wrapper {
    grid-template-columns: 1fr;
    gap: 3rem;
    text-align: center;
    padding: 0 1rem; /* Reduce side padding */
    max-width: 100%;
  }

  .header-group {
    text-align: center;
  }

  .name {
    word-break: keep-all; /* Prevent long text overflow */
  }

  .name::after {
    left: 50%;
    transform: translateX(-50%);
  }

  .tech-highlights {
    justify-content: center;
  }

  .action-buttons {
    justify-content: center;
  }

  .avatar-container {
    order: -1;
  }

  .avatar-frame {
    width: 300px;
    height: 300px;
    margin: 0 auto;
  }
}

@media (max-width: 768px) {
  .intro-section {
    padding: 4rem 1rem;
  }

  .name {
    font-size: 2.5rem;
  }

  .title {
    font-size: 1.25rem;
  }

  .description {
    font-size: 1rem;
  }

  .avatar-frame {
    width: 250px;
    height: 250px;
  }

  .resume-button {
    font-size: 1rem;
    padding: 0.75rem 1.5rem;
  }
}
</style>
