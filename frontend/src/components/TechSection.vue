<template>
  <div class="tech-section">
    <h2 class="tech-title">My Tech Stack</h2>

    <div class="tech-container">
      <!-- Programming Languages Card -->
      <div class="tech-card">
        <h3 class="tech-header">Programming Languages</h3>
        <div class="tech-content">
          <div class="tech-column">
            <div class="tech-item">
              <img src="/assets/python-logo-only.svg" alt="Python" class="tech-icon"/>
              <span>Python</span>
            </div>
            <div class="tech-item">
              <img src="/assets/javascript.svg" alt="JavaScript" class="tech-icon"/>
              <span>JavaScript</span>
            </div>
            <div class="tech-item">
              <img src="/assets/C.svg" alt="C" class="tech-icon"/>
              <span>C</span>
            </div>
           
           
          </div>
          <div class="tech-column">
            <div class="tech-item">
              <img src="/assets/java.svg" alt="Java" class="tech-icon"/>
              <span>Java</span>
            </div>
            
            <div class="tech-item">
              <img src="/assets/cpp.svg" alt="C++" class="tech-icon"/>
              <span>C++</span>
            </div>
            <div class="tech-item">
              <img src="/assets/sql.svg" alt="SQL" class="tech-icon"/>
              <span>SQL</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Frameworks Card -->
      <div class="tech-card">
        <h3 class="tech-header">Frameworks & Libraries</h3>
        <div class="tech-content">
          <div class="tech-column">
            <div class="tech-item">
              <img src="/assets/vite.svg" alt="Vite" class="tech-icon"/>
              <span>Vite</span>
            </div>
           
            <div class="tech-item">
              <img src="/assets/react.svg" alt="React" class="tech-icon"/>
              <span>React</span>
            </div>
            <div class="tech-item">
              <img src="/assets/fastapi.svg" alt="FastAPI" class="tech-icon"/>
              <span>FastAPI</span>
            </div>
            <div class="tech-item">
              <img src="/assets/Flask.svg" alt="Flask" class="tech-icon"/>
              <span>Flask</span>
            </div>
          </div>
          <div class="tech-column">
            <div class="tech-item">
              <img src="/assets/nodejs.svg" alt="Node.js" class="tech-icon"/>
              <span>Node.js</span>
            </div>
            <div class="tech-item">
              <img src="/assets/express.svg" alt="Express" class="tech-icon"/>
              <span>Express.js</span>
            </div>
            <div class="tech-item">
              <img src="/assets/tailwind.svg" alt="Next" class="tech-icon"/>
              <span>Tailwind</span>
            </div>
            
          </div>
        </div>
      </div>

      <!-- Infrastructure Card -->
      <div class="tech-card">
        <h3 class="tech-header">Cloud & Infrastructure</h3>
        <div class="tech-content">
          <div class="tech-column">
            <div class="tech-item">
              <img src="/assets/mongodb.svg" alt="MongoDB" class="tech-icon"/>
              <span>MongoDB</span>
            </div>
           
           
            <div class="tech-item">
              <img src="/assets/huggingface.svg" alt="huggingface" class="tech-icon"/>
              <span>Transformers</span>
            </div>

            <div class="tech-item">
              <img src="/assets/system_design.png" alt="Jenkins" class="tech-icon"/>
              <span>System Design</span>
            </div>
          </div>

          
          <div class="tech-column">
            
            <div class="tech-item">
              <img src="/assets/git.svg" alt="Git" class="tech-icon"/>
              <span>GIT</span>
            </div>
            <div class="tech-item">
              <img src="/assets/aws.svg" alt="Jenkins" class="tech-icon"/>
              <span>AWS</span>
            </div>
            
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.tech-section {
  padding: 4rem 2rem;
  max-width: 1400px;
  margin: 0 auto;
}

.tech-title {
  text-align: center;
  font-family: 'Gilroy Bold', serif;
  font-size: 2.5rem;
  color: #eaecef;
  margin-bottom: 3rem;
}

.tech-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
  padding: 0 1rem;
}

.tech-card {
  background: rgba(30, 30, 30, 0.6);
  border-radius: 20px;
  padding: 2rem;
  border: 1px solid rgba(255, 255, 255, 0.1);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.tech-card:hover {
  transform: translateY(-5px);
  border-color: #4ECDC4;
  background: rgba(30, 30, 30, 0.8);
}

.tech-header {
  color: #4ECDC4;
  font-family: 'Gilroy Bold', serif;
  font-size: 1.5rem;
  margin: 0 0 2rem 0;
  text-align: center;
}

.tech-content {
  display: flex;
  justify-content: space-around;
  gap: 2rem;
}

.tech-column {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.tech-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 0.5rem;
  border-radius: 8px;
  transition: background 0.2s ease;
}

.tech-item:hover {
  background: rgba(78, 205, 196, 0.1);
}

.tech-icon {
  width: 28px;
  height: 28px;
  object-fit: contain;
}

.tech-item span {
  color: #eaecef;
  font-family: 'Gilroy Medium', serif;
  font-size: 1rem;
}

@media (max-width: 1200px) {
  .tech-container {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 768px) {
  .tech-section {
    padding: 2rem 1rem;
  }

  .tech-container {
    grid-template-columns: 1fr;
  }

  .tech-title {
    font-size: 2rem;
    margin-bottom: 2rem;
  }

  .tech-card {
    padding: 1.5rem;
  }

  .tech-header {
    font-size: 1.25rem;
    margin-bottom: 1.5rem;
  }

  .tech-icon {
    width: 24px;
    height: 24px;
  }

  .tech-item span {
    font-size: 0.9rem;
  }
}
</style>
