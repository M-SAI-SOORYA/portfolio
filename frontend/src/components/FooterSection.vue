<script setup lang="ts">

const openLinkedIN = () => {
  window.location.href = 'https://www.linkedin.com/in/soorya-marri-466086233/'
}
</script>

<template>
  <footer class="footer">
    <div class="content">
      <h2 class="title">Let's Work Together</h2>
      <p class="description">
        Whether you have a project in mind or just want to connect,
        I'm always open to new opportunities and conversations.
      </p>

      <button @click="openLinkedIN" class="contact-button">
        Get in Touch
      </button>

      <div class="bottom">
        <div class="credit">
          <span>2025 Soorya Marri</span>
        </div>

        <!-- <a href="https://github.com/Hololm/portfolio" target="_blank" class="source">
          <img src="/assets/github.svg" alt="GitHub" />
          Source Code
        </a> -->
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background: radial-gradient(#0a0a0a 0%, #090909 100%);
  backdrop-filter: blur(10px);
  padding: 4rem 2rem;
  margin-top: 4rem;
}

.content {
  max-width: 1200px;
  margin: 0 auto;
  text-align: center;
}

.title {
  font-size: 2.5rem;
  color: #fff;
  margin-bottom: 1.5rem;
  font-family: 'Gilroy Bold';
}

.description {
  color: rgba(255, 255, 255, 0.8);
  max-width: 600px;
  margin: 0 auto 2rem;
  line-height: 1.6;
}

.contact-button {
  font-family: "Gilroy Bold", serif;
  padding: 1rem 2.5rem;
  border-radius: 50px;
  font-size: 1.1rem;
  cursor: pointer;
  margin-bottom: 3rem;
  background: rgba(78, 205, 196, 0.1);
  color: #4ECDC4;
  border: 1px solid rgba(78, 205, 196, 0.3);
  transition: all 0.3s ease;
}

.contact-button:hover {
  background: rgba(78, 205, 196, 0.2);
  transform: translateY(-2px);
}

.bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 2rem;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
}

.credit {
  display: flex;
  gap: 1.5rem;
  color: rgba(255, 255, 255, 0.6);
  font-size: 0.9rem;
}

.source {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: rgba(255, 255, 255, 0.6);
  text-decoration: none;
  transition: color 0.3s ease;
}

.source:hover {
  color: #4ECDC4;
}

.source img {
  width: 20px;
  height: 20px;
}

@media (max-width: 768px) {
  .footer {
    padding: 3rem 1rem;
  }

  .title {
    font-size: 2rem;
  }

  .bottom {
    flex-direction: column;
    gap: 1rem;
  }

  .credit {
    flex-direction: column;
    gap: 0.5rem;
  }
}
</style>
