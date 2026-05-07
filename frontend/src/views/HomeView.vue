<script setup lang="ts">
import { computed, onMounted, ref } from 'vue'

declare global {
  interface Window {
    webkitAudioContext?: typeof AudioContext
  }
}

const emailHref = 'mailto:sooryamarri@gmail.com'
const linkedInHref = 'https://www.linkedin.com/in/soorya-marri-466086233/'
const leetCodeHref = 'https://leetcode.com/u/sooryamarri/'
const theme = ref<'dark' | 'light'>('dark')
const themeLabel = computed(() => theme.value === 'dark' ? 'Switch to light mode' : 'Switch to dark mode')
const themeSymbol = computed(() => theme.value === 'dark' ? '☀' : '☾')
let hoverAudioContext: AudioContext | null = null
let lastHoverSound = 0

const playHoverSound = () => {
  const now = Date.now()
  if (now - lastHoverSound < 90) return
  lastHoverSound = now

  const AudioContextClass = window.AudioContext || window.webkitAudioContext
  if (!AudioContextClass) return

  hoverAudioContext ||= new AudioContextClass()
  if (hoverAudioContext.state === 'suspended') {
    hoverAudioContext.resume()
  }

  const oscillator = hoverAudioContext.createOscillator()
  const gain = hoverAudioContext.createGain()
  const startTime = hoverAudioContext.currentTime

  oscillator.type = 'sine'
  oscillator.frequency.setValueAtTime(740, startTime)
  oscillator.frequency.exponentialRampToValueAtTime(980, startTime + 0.08)
  gain.gain.setValueAtTime(0.0001, startTime)
  gain.gain.exponentialRampToValueAtTime(0.11, startTime + 0.012)
  gain.gain.exponentialRampToValueAtTime(0.0001, startTime + 0.09)

  oscillator.connect(gain)
  gain.connect(hoverAudioContext.destination)
  oscillator.start(startTime)
  oscillator.stop(startTime + 0.1)
}

const applyTheme = (value: 'dark' | 'light') => {
  theme.value = value
  document.documentElement.dataset.theme = value
  localStorage.setItem('portfolio-theme', value)
}

const toggleTheme = () => {
  applyTheme(theme.value === 'dark' ? 'light' : 'dark')
}

const openResume = () => {
  window.open('/Profile.pdf', '_blank')
}

onMounted(() => {
  const savedTheme = localStorage.getItem('portfolio-theme')
  if (savedTheme === 'dark' || savedTheme === 'light') {
    applyTheme(savedTheme)
    return
  }

  const prefersLight = window.matchMedia('(prefers-color-scheme: light)').matches
  applyTheme(prefersLight ? 'light' : 'dark')
})

const navItems = [
  { label: 'Work', href: '#work' },
  { label: 'Projects', href: '#projects' },
  { label: 'Credentials', href: '#credentials' },
  { label: 'Stack', href: '#stack' },
  { label: 'Contact', href: '#contact' },
]

const stats = [
  { value: '7 mo', label: 'AI/ML engineering experience at AidenAI' },
  { value: '3', label: 'Personal projects across AI, ML, and full-stack development' },
  { value: '3', label: 'Oracle AI, Vector Search, and DevOps certifications' },
]

const capabilities = [
  'Generative AI product engineering',
  'RAG pipelines and vector search',
  'Medical imaging transformers',
  'Full-stack web applications',
]

const projects = [
  {
    title: 'Multi Organ Segmentation Transformer',
    eyebrow: 'Deep Learning / Medical Imaging',
    image: '/assets/most_image.png',
    metric: '85% Dice score',
    description:
      'Implemented a UNETR-2D model using a Vision Transformer encoder and CNN up-sampler decoder to segment organs from CT scan images, with a mobile application prototype for uploading scans and viewing organ-segmented results.',
    tags: ['Python', 'TensorFlow', 'PyTorch', 'OpenCV', 'Flutter', 'Generative AI'],
    links: [
      { label: 'Documentation', href: 'https://drive.google.com/file/d/16oYCTS5EzThjcb5AJXsa6naOEONXX4KH/view' },
      { label: 'Demo', href: 'https://drive.google.com/file/d/1neIdlu4kfy0f37NwsvG-miXZKshvWgfq/view' },
    ],
  },
  {
    title: 'Agentic AI QA Bot',
    eyebrow: 'Agentic AI / RAG',
    image: '/assets/ai-blog-2.png.jpg',
    metric: 'Agentic Q&A',
    description:
      'Built AI-powered chatbots with Streamlit and FastAPI using Groq LLMs, including a ReAct-style search agent with DuckDuckGo, Wikipedia, and Arxiv tools, plus a PDF Q&A RAG pipeline with Chroma and HuggingFace embeddings.',
    tags: ['LangChain', 'FastAPI', 'Streamlit', 'Agent AI', 'RAG', 'Chroma'],
    links: [
      { label: 'GitHub', href: 'https://github.com/M-SAI-SOORYA/Agent-and-QA-Bot' },
      { label: 'Demo', href: 'https://drive.google.com/file/d/1dTo_w5p0ew-69ZuwDE_w50estl4LTltk/view' },
    ],
  },
  {
    title: 'Lost and Found Website',
    eyebrow: 'MERN Product Build',
    image: '/assets/landf.png',
    metric: '500+ users',
    description:
      'Collaborated with a five-member team to build a MERN stack lost-and-found platform for a college environment, including authentication, item search, posting flows, contact/report submission, and API documentation.',
    tags: ['MongoDB', 'Express.js', 'React.js', 'Node.js', 'JavaScript', 'REST APIs'],
    links: [
      { label: 'Documentation', href: 'https://drive.google.com/file/d/1aTZSTlC06-hV_0JbFB3Swtop9yJKMWmB/view' },
      { label: 'Demo', href: 'https://drive.google.com/file/d/1Dqwoiqqmgw7eZ67jpfQDNVx5TTz1oAvg/view' },
    ],
  },
]

const experiences = [
  {
    company: 'AidenAI',
    role: 'AI/ML Engineer',
    period: 'Feb 2026 - Present',
    location: 'Hyderabad, Telangana, India',
    logo: '/assets/aidenai-logo.svg',
    points: [
      'Working on AI/ML engineering initiatives across generative AI, RAG, and system design.',
      'Building production-minded AI workflows that connect LLM capability with practical application behavior.',
      'Focused on prompt quality, retrieval reliability, and scalable AI backend patterns.',
    ],
    tags: ['AI/ML', 'Generative AI', 'RAG', 'System Design', 'Prompt Engineering'],
  },
  {
    company: 'AidenAI',
    role: 'AI/ML Engineer',
    period: 'Nov 2025 - Jan 2026',
    location: 'Hyderabad, Telangana, India',
    logo: '/assets/aidenai-logo.svg',
    points: [
      'Contributed to AI/ML development before moving into the current engineering role.',
      'Worked with model-backed product workflows and applied AI implementation patterns.',
      'Strengthened hands-on experience across LLM systems, retrieval, and backend integration.',
    ],
    tags: ['LLMs', 'AI Engineering', 'Python', 'Model Workflows'],
  },
  {
    company: 'Electronics Corporation of India Limited',
    role: 'Web Developer Intern',
    period: 'May 2024 - Jun 2024',
    location: 'Hyderabad, Telangana, India',
    logo: '/assets/ecil-logo.svg',
    points: [
      'Developed the interactive web interface for a Classroom Warfare Simulator used for training workflows.',
      'Built the frontend with React and integrated backend REST APIs.',
      'Used Spring Boot, Spring Web MVC, Spring JPA, and PostgreSQL for server-side data workflows.',
    ],
    tags: ['React', 'Spring Boot', 'PostgreSQL', 'REST APIs', 'Spring JPA'],
  },
]

const credentials = [
  'Oracle Generative AI Professional 2025',
  'Oracle AI Vector Search Certified Professional 2025',
  'Oracle Certified DevOps Professional Cloud Infrastructure 2025',
  'Internship on Data Science',
]

const education = [
  {
    school: 'Keshav Memorial Institute of Technology',
    program: 'BTech, Computer Science and Engineering',
    period: 'Dec 2021 - Jul 2025',
  },
  {
    school: 'FIITJEE',
    program: 'Intermediate / +2, MPC',
    period: '2019 - 2021',
  },
  {
    school: 'FIITJEE World School - India',
    program: '10th Grade, SSC Board',
    period: '2018 - 2019',
  },
]

const stackGroups = [
  {
    title: 'Languages',
    items: [
      { name: 'Python', icon: '/assets/python-logo-only.svg' },
      { name: 'JavaScript', icon: '/assets/javascript.svg' },
      { name: 'TypeScript', icon: '/assets/typescript.svg' },
      { name: 'Java', icon: '/assets/java.svg' },
      { name: 'C++', icon: '/assets/cpp.svg' },
      { name: 'SQL', icon: '/assets/sql.svg' },
    ],
  },
  {
    title: 'AI / Backend',
    items: [
      { name: 'LangChain', icon: '/assets/Langchain.png' },
      { name: 'LangGraph', icon: '/assets/langgraph.svg' },
      { name: 'RAG', icon: '/assets/rag.jpg' },
      { name: 'FastAPI', icon: '/assets/fastapi.svg' },
      { name: 'HuggingFace', icon: '/assets/huggingface.svg' },
      { name: 'Vector Search', icon: '/assets/system_design.png' },
    ],
  },
  {
    title: 'Frontend / Cloud',
    items: [
      { name: 'React', icon: '/assets/react.svg' },
      { name: 'Spring Boot', icon: '/assets/java.svg' },
      { name: 'PostgreSQL', icon: '/assets/sql.svg' },
      { name: 'AWS', icon: '/assets/aws.svg' },
      { name: 'Docker', icon: '/assets/docker.svg' },
      { name: 'Git', icon: '/assets/git.svg' },
    ],
  },
]
</script>

<template>
  <main class="portfolio-shell" :class="{ 'light-mode': theme === 'light' }">
    <header class="site-nav">
      <a class="brand" href="#top" aria-label="Sai Soorya Marri home">
        <span class="brand-mark">SS</span>
        <span class="brand-copy">Sai Soorya Marri</span>
      </a>

      <nav class="nav-links" aria-label="Primary navigation">
        <a v-for="item in navItems" :key="item.href" :href="item.href">{{ item.label }}</a>
      </nav>

      <div class="nav-actions">
        <a class="icon-button" :href="emailHref" title="Email Sai Soorya Marri" aria-label="Email Sai Soorya Marri" @mouseenter="playHoverSound" @focus="playHoverSound">
          <span class="mail-symbol">@</span>
        </a>
        <a class="icon-button github-button" href="https://github.com/M-SAI-SOORYA" target="_blank" rel="noopener noreferrer" aria-label="GitHub" @mouseenter="playHoverSound" @focus="playHoverSound">
          <img src="/assets/github.svg" alt="" />
        </a>
        <a class="icon-button" :href="linkedInHref" target="_blank" rel="noopener noreferrer" aria-label="LinkedIn" @mouseenter="playHoverSound" @focus="playHoverSound">
          <img src="/assets/linkedin.svg" alt="" />
        </a>
        <a class="icon-button leetcode-button" :href="leetCodeHref" target="_blank" rel="noopener noreferrer" aria-label="LeetCode" @mouseenter="playHoverSound" @focus="playHoverSound">
          <img src="/assets/leetcode.png" alt="" />
        </a>
        <button class="resume-pill" @mouseenter="playHoverSound" @focus="playHoverSound" @click="openResume">Resume</button>
      </div>
    </header>

        <button class="theme-float" type="button" @mouseenter="playHoverSound" @focus="playHoverSound" @click="toggleTheme" :aria-label="themeLabel" :title="themeLabel">
      {{ themeSymbol }}
    </button>

    <section id="top" class="hero-section">
      <div class="hero-grid">
        <div class="hero-copy" data-aos="fade-up">
          <p class="section-kicker">AI/ML Engineer at AidenAI / System Design</p>
          <h1>Building AI products grounded in retrieval, reasoning, and reliable backend systems.</h1>
          <p class="hero-text">
            Hyderabad-based Computer Science graduate focused on generative AI, RAG, prompt engineering,
            vector search, and full-stack systems that turn LLM capability into usable production workflows.
          </p>

          <div class="hero-actions">
            <a class="primary-cta" href="#projects" @mouseenter="playHoverSound" @focus="playHoverSound">View Projects</a>
            <a class="secondary-cta" :href="linkedInHref" target="_blank" rel="noopener noreferrer" @mouseenter="playHoverSound" @focus="playHoverSound">
              Start a Conversation
            </a>
          </div>

          <div class="capability-row" aria-label="Core capabilities">
            <span v-for="capability in capabilities" :key="capability">{{ capability }}</span>
          </div>
        </div>

        <aside class="hero-visual" data-aos="fade-left">
          <div class="portrait-panel">
            <img src="/assets/me2.jpg" alt="Sai Soorya Marri" />
            <div class="portrait-caption">
              <span>Hyderabad, Telangana, India</span>
              <strong>AI/ML engineering, RAG, system design</strong>
            </div>
          </div>
        </aside>
      </div>

      <div class="stats-grid" data-aos="fade-up">
        <article v-for="stat in stats" :key="stat.label" class="stat-card">
          <strong>{{ stat.value }}</strong>
          <span>{{ stat.label }}</span>
        </article>
      </div>
    </section>

    <section id="work" class="work-section section-wrap">
      <div class="section-heading" data-aos="fade-up">
        <p class="section-kicker">Experience</p>
        <h2>AI and software engineering experience across ML systems, backend work, and simulation interfaces.</h2>
      </div>

      <div class="timeline-list">
        <article v-for="job in experiences" :key="`${job.company}-${job.period}`" class="experience-card" data-aos="fade-up">
          <div class="company-logo">
            <img :src="job.logo" :alt="job.company" />
          </div>
          <div class="experience-content">
            <div class="experience-topline">
              <div>
                <h3>{{ job.company }}</h3>
                <p>{{ job.role }}</p>
              </div>
              <span>{{ job.period }}</span>
            </div>
            <p class="location">{{ job.location }}</p>
            <ul>
              <li v-for="point in job.points" :key="point">{{ point }}</li>
            </ul>
            <div class="tag-row">
              <span v-for="tag in job.tags" :key="tag">{{ tag }}</span>
            </div>
          </div>
        </article>
      </div>
    </section>

    <section id="projects" class="projects-section section-wrap">
      <div class="section-heading wide" data-aos="fade-up">
        <p class="section-kicker">Selected Builds</p>
        <h2>Personal projects across medical imaging AI, agentic Q&A, and full-stack web products.</h2>
      </div>

      <div class="project-grid">
        <article v-for="project in projects" :key="project.title" class="project-card" data-aos="fade-up">
          <div class="project-media">
            <img :src="project.image" :alt="project.title" />
            <span>{{ project.metric }}</span>
          </div>
          <div class="project-body">
            <p>{{ project.eyebrow }}</p>
            <h3>{{ project.title }}</h3>
            <span class="project-description">{{ project.description }}</span>
            <div class="tag-row">
              <span v-for="tag in project.tags" :key="tag">{{ tag }}</span>
            </div>
            <div v-if="project.links.length" class="project-links">
              <a v-for="link in project.links" :key="link.href" :href="link.href" target="_blank" @mouseenter="playHoverSound" @focus="playHoverSound">
                {{ link.label }}
              </a>
            </div>
          </div>
        </article>
      </div>
    </section>

    <section id="credentials" class="credentials-section section-wrap">
      <div class="section-heading" data-aos="fade-up">
        <p class="section-kicker">Credentials</p>
        <h2>Certifications and education that support AI engineering depth.</h2>
      </div>

      <div class="credentials-grid">
        <article class="credential-card" data-aos="fade-up">
          <h3>Certifications</h3>
          <ul>
            <li v-for="credential in credentials" :key="credential">{{ credential }}</li>
          </ul>
        </article>

        <article class="credential-card" data-aos="fade-up">
          <h3>Education</h3>
          <div class="education-list">
            <div v-for="item in education" :key="item.school" class="education-item">
              <strong>{{ item.school }}</strong>
              <span>{{ item.program }}</span>
              <small>{{ item.period }}</small>
            </div>
          </div>
        </article>
      </div>
    </section>

    <section id="stack" class="stack-section section-wrap">
      <div class="section-heading" data-aos="fade-up">
        <p class="section-kicker">Stack</p>
        <h2>A profile-aligned toolkit for RAG systems, AI APIs, and full-stack engineering.</h2>
      </div>

      <div class="stack-grid">
        <article v-for="group in stackGroups" :key="group.title" class="stack-card" data-aos="fade-up">
          <h3>{{ group.title }}</h3>
          <div class="stack-items">
            <div v-for="item in group.items" :key="item.name" class="stack-item">
              <img :src="item.icon" :alt="item.name" />
              <span>{{ item.name }}</span>
            </div>
          </div>
        </article>
      </div>
    </section>

    <section id="contact" class="contact-section">
      <div class="contact-panel" data-aos="zoom-in">
        <p class="section-kicker">Contact</p>
        <h2>Let's build something intelligent, useful, and polished.</h2>
        <p>
          I'm interested in AI/ML engineering, generative AI products, RAG systems, and backend roles where
          product thinking matters as much as implementation quality.
        </p>
        <div class="contact-actions">
          <a class="primary-cta" :href="emailHref" @mouseenter="playHoverSound" @focus="playHoverSound">Email Me</a>
          <a class="secondary-cta" :href="linkedInHref" target="_blank" rel="noopener noreferrer" @mouseenter="playHoverSound" @focus="playHoverSound">
            LinkedIn
          </a>
        </div>
      </div>
    </section>
  </main>
</template>

<style scoped>
.portfolio-shell {
  min-height: 100vh;
  color: #f7f7ef;
  background:
    radial-gradient(circle at 18% 12%, rgba(61, 220, 151, 0.16), transparent 28rem),
    radial-gradient(circle at 82% 4%, rgba(255, 183, 77, 0.14), transparent 26rem),
    linear-gradient(135deg, #050607 0%, #0b1114 42%, #11100d 100%);
  overflow: hidden;
}

.portfolio-shell.light-mode {
  color: #101513;
  background:
    radial-gradient(circle at 18% 12%, rgba(31, 186, 116, 0.18), transparent 28rem),
    radial-gradient(circle at 82% 4%, rgba(255, 188, 88, 0.2), transparent 26rem),
    linear-gradient(135deg, #f7faf8 0%, #edf6f2 48%, #fff7e8 100%);
}

.site-nav {
  position: fixed;
  top: 1rem;
  left: 50%;
  z-index: 50;
  width: min(1120px, calc(100% - 2rem));
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
  padding: 0.7rem;
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 8px;
  background: rgba(8, 12, 14, 0.72);
  backdrop-filter: blur(22px);
  box-shadow: 0 24px 80px rgba(0, 0, 0, 0.32);
  transform: translateX(-50%);
}

.brand,
.nav-links a,
.secondary-cta,
.project-links a {
  color: inherit;
  text-decoration: none;
}

.brand {
  display: inline-flex;
  align-items: center;
  gap: 0.7rem;
  min-width: max-content;
}

.brand-mark {
  display: grid;
  place-items: center;
  width: 2.45rem;
  height: 2.45rem;
  border-radius: 6px;
  color: #06110d;
  background: #83f7bd;
  font-family: 'Gilroy Bold', system-ui, sans-serif;
}

.brand-copy,
.nav-links a,
.resume-pill,
.primary-cta,
.secondary-cta {
  font-family: 'Gilroy Medium', system-ui, sans-serif;
}

.brand-copy {
  font-size: 0.95rem;
}

.nav-links {
  display: flex;
  gap: 0.35rem;
  padding: 0.25rem;
  border-radius: 8px;
  background: rgba(255, 255, 255, 0.05);
}

.nav-links a {
  padding: 0.7rem 0.9rem;
  border-radius: 6px;
  color: rgba(247, 247, 239, 0.72);
  font-size: 0.92rem;
  transition: 0.25s ease;
}

.nav-links a:hover {
  color: #ffffff;
  background: rgba(255, 255, 255, 0.08);
}

.nav-actions,
.hero-actions,
.contact-actions,
.tag-row,
.project-links,
.capability-row {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
}

.nav-actions {
  justify-content: flex-end;
  gap: 0.55rem;
}

.icon-button,
.resume-pill,
.theme-float {
  border: 1px solid rgba(255, 255, 255, 0.12);
  background: rgba(255, 255, 255, 0.07);
  color: #f7f7ef;
  cursor: pointer;
}

.icon-button {
  display: grid;
  place-items: center;
  width: 2.45rem;
  height: 2.45rem;
  border-radius: 6px;
  text-decoration: none;
}

.icon-button img {
  width: 1.1rem;
  height: 1.1rem;
}

.mail-symbol {
  color: #ea4335;
  font-family: 'Gilroy Bold', system-ui, sans-serif;
  font-size: 1rem;
}

.github-button {
  background: #181717;
}

.leetcode-button img {
  width: 1.35rem;
  height: 1.35rem;
}

.resume-pill {
  min-height: 2.45rem;
  padding: 0 1rem;
  border-radius: 6px;
  font-size: 0.92rem;
}

.theme-float {
  position: fixed;
  top: 1.55rem;
  right: clamp(1rem, calc((100vw - 1120px) / 2 - 3.75rem), 5rem);
  z-index: 51;
  display: grid;
  place-items: center;
  width: 2.55rem;
  height: 2.55rem;
  border-radius: 999px;
  color: #ffd27d;
  font-family: 'Gilroy Bold', system-ui, sans-serif;
  font-size: 1.35rem;
  backdrop-filter: blur(22px);
  box-shadow: 0 24px 80px rgba(0, 0, 0, 0.24);
  cursor: pointer;
  transition: 0.25s ease;
}

.hero-section {
  width: min(1180px, calc(100% - 2rem));
  margin: 0 auto;
  padding: 9rem 0 4rem;
}

.hero-grid {
  display: grid;
  grid-template-columns: minmax(0, 1.12fr) minmax(320px, 0.88fr);
  gap: clamp(2rem, 5vw, 5rem);
  align-items: center;
  min-height: 660px;
}

.section-kicker {
  margin: 0 0 1rem;
  color: #83f7bd;
  font-family: 'Gilroy Bold', system-ui, sans-serif;
  font-size: 0.78rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
}

.hero-copy h1,
.section-heading h2,
.contact-panel h2 {
  margin: 0;
  color: #fffdf4;
  font-family: 'Gilroy Bold', system-ui, sans-serif;
  letter-spacing: 0;
}

.hero-copy h1 {
  max-width: 820px;
  font-size: clamp(3.1rem, 7vw, 6.8rem);
  line-height: 0.94;
}

.hero-text {
  max-width: 680px;
  margin: 1.7rem 0 0;
  color: rgba(247, 247, 239, 0.76);
  font-family: 'Gilroy Regular', system-ui, sans-serif;
  font-size: clamp(1.05rem, 2vw, 1.25rem);
  line-height: 1.7;
}

.hero-actions,
.contact-actions {
  gap: 0.8rem;
  margin-top: 2rem;
}

.primary-cta,
.secondary-cta {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  min-height: 3.2rem;
  padding: 0 1.2rem;
  border-radius: 7px;
  transition: 0.25s ease;
}

.primary-cta {
  color: #07110e;
  background: #83f7bd;
  text-decoration: none;
  box-shadow: 0 18px 48px rgba(131, 247, 189, 0.18);
}

.secondary-cta {
  border: 1px solid rgba(255, 255, 255, 0.14);
  background: rgba(255, 255, 255, 0.06);
}

.primary-cta:hover,
.secondary-cta:hover,
.resume-pill:hover,
.theme-float:hover,
.icon-button:hover {
  transform: translateY(-2px);
}

.capability-row {
  gap: 0.65rem;
  margin-top: 2rem;
}

.capability-row span,
.tag-row span {
  border: 1px solid rgba(255, 255, 255, 0.12);
  color: rgba(247, 247, 239, 0.78);
  background: rgba(255, 255, 255, 0.055);
  border-radius: 999px;
  font-family: 'Gilroy Medium', system-ui, sans-serif;
}

.capability-row span {
  padding: 0.58rem 0.78rem;
  font-size: 0.9rem;
}

.hero-visual {
  position: relative;
  min-height: 580px;
}

.portrait-panel {
  position: relative;
  height: 540px;
  overflow: hidden;
  border: 1px solid rgba(255, 255, 255, 0.13);
  border-radius: 8px;
  background: linear-gradient(145deg, rgba(255, 255, 255, 0.14), rgba(255, 255, 255, 0.03));
  box-shadow: 0 30px 90px rgba(0, 0, 0, 0.38);
}

.portrait-panel::before {
  position: absolute;
  inset: 1rem;
  z-index: 2;
  border: 1px solid rgba(255, 255, 255, 0.16);
  border-radius: 7px;
  content: '';
  pointer-events: none;
}

.portrait-panel img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  filter: saturate(1.02) contrast(1.03);
}

.portrait-caption {
  position: absolute;
  right: 1.5rem;
  bottom: 1.5rem;
  left: 1.5rem;
  z-index: 3;
  display: grid;
  gap: 0.4rem;
  padding: 1rem;
  border-radius: 8px;
  background: rgba(5, 8, 9, 0.78);
  backdrop-filter: blur(16px);
}

.portrait-caption span,
.location,
.project-body p {
  margin: 0;
  color: rgba(247, 247, 239, 0.62);
}

.portrait-caption strong {
  font-family: 'Gilroy Bold', system-ui, sans-serif;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
  margin-top: 3.5rem;
}

.stat-card,
.experience-card,
.project-card,
.stack-card,
.credential-card,
.contact-panel {
  border: 1px solid rgba(255, 255, 255, 0.11);
  border-radius: 8px;
  background: rgba(255, 255, 255, 0.055);
  box-shadow: 0 22px 70px rgba(0, 0, 0, 0.22);
}

.stat-card {
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 1.15rem;
  min-height: 132px;
  padding: 1.95rem;
}

.stat-card strong {
  display: block;
  margin: 0;
  color: #ffd27d;
  font-family: 'Gilroy Bold', system-ui, sans-serif;
  font-size: 2.2rem;
  line-height: 1;
}

.stat-card span {
  display: block;
  max-width: 22rem;
}

.stat-card span,
.project-description,
.experience-content li,
.contact-panel p {
  color: rgba(247, 247, 239, 0.72);
  line-height: 1.65;
}

.section-wrap {
  width: min(1120px, calc(100% - 2rem));
  margin: 0 auto;
  padding: 5.5rem 0;
}

.section-heading {
  max-width: 740px;
  margin-bottom: 2rem;
}

.section-heading.wide {
  max-width: 860px;
}

.section-heading h2,
.contact-panel h2 {
  font-size: clamp(2rem, 4vw, 4rem);
  line-height: 1.02;
}

.timeline-list {
  display: grid;
  gap: 1rem;
}

.experience-card {
  display: grid;
  grid-template-columns: 82px 1fr;
  gap: 1.1rem;
  padding: 1.1rem;
  transition: 0.25s ease;
}

.experience-card:hover,
.project-card:hover,
.stack-card:hover {
  border-color: rgba(131, 247, 189, 0.34);
  transform: translateY(-3px);
}

.company-logo {
  display: grid;
  place-items: center;
  width: 72px;
  height: 72px;
  border-radius: 8px;
  background: #ffffff;
  padding: 0.75rem;
}

.company-logo img {
  width: 100%;
  height: 100%;
  object-fit: contain;
}

.experience-topline {
  display: flex;
  justify-content: space-between;
  gap: 1rem;
}

.experience-topline h3,
.project-body h3,
.stack-card h3 {
  margin: 0;
  color: #fffdf4;
  font-family: 'Gilroy Bold', system-ui, sans-serif;
}

.experience-topline h3 {
  font-size: 1.45rem;
}

.experience-topline p {
  margin: 0.3rem 0 0;
  color: #83f7bd;
  font-family: 'Gilroy Medium', system-ui, sans-serif;
}

.experience-topline > span {
  flex: 0 0 auto;
  color: rgba(247, 247, 239, 0.58);
  font-family: 'Gilroy Medium', system-ui, sans-serif;
}

.experience-content ul {
  display: grid;
  gap: 0.5rem;
  margin: 1rem 0;
  padding-left: 1.1rem;
}

.tag-row {
  gap: 0.48rem;
}

.tag-row span {
  padding: 0.42rem 0.68rem;
  font-size: 0.82rem;
}

.project-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1rem;
}

.project-card {
  display: flex;
  flex-direction: column;
  overflow: hidden;
  min-height: 100%;
  transition: 0.25s ease;
}

.project-media {
  position: relative;
  aspect-ratio: 1.2;
  overflow: hidden;
  background: rgba(255, 255, 255, 0.04);
}

.project-media img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.45s ease;
}

.project-card:hover .project-media img {
  transform: scale(1.04);
}

.project-media span {
  position: absolute;
  right: 0.8rem;
  bottom: 0.8rem;
  padding: 0.46rem 0.65rem;
  border-radius: 6px;
  color: #07110e;
  background: #ffd27d;
  font-family: 'Gilroy Bold', system-ui, sans-serif;
  font-size: 0.82rem;
}

.project-body {
  display: flex;
  flex: 1;
  flex-direction: column;
  gap: 0.9rem;
  padding: 1.1rem;
}

.project-body h3 {
  font-size: 1.55rem;
}

.project-body p {
  color: #83f7bd;
  font-family: 'Gilroy Medium', system-ui, sans-serif;
  font-size: 0.85rem;
}

.project-description {
  display: block;
}

.project-links {
  gap: 0.7rem;
  margin-top: auto;
}

.project-links a {
  color: #ffd27d;
  font-family: 'Gilroy Bold', system-ui, sans-serif;
  font-size: 0.92rem;
}

.credentials-grid {
  display: grid;
  grid-template-columns: 0.92fr 1.08fr;
  gap: 1rem;
}

.credential-card {
  padding: 1.2rem;
}

.credential-card h3 {
  margin: 0 0 1rem;
  color: #fffdf4;
  font-family: 'Gilroy Bold', system-ui, sans-serif;
  font-size: 1.35rem;
}

.credential-card ul {
  display: grid;
  gap: 0.75rem;
  margin: 0;
  padding-left: 1.1rem;
}

.credential-card li,
.education-item span,
.education-item small {
  color: rgba(247, 247, 239, 0.72);
  line-height: 1.55;
}

.education-list {
  display: grid;
  gap: 0.9rem;
}

.education-item {
  display: grid;
  gap: 0.28rem;
  padding: 0.85rem;
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 7px;
  background: rgba(255, 255, 255, 0.045);
}

.education-item strong {
  color: #83f7bd;
  font-family: 'Gilroy Bold', system-ui, sans-serif;
}

.education-item small {
  font-family: 'Gilroy Medium', system-ui, sans-serif;
}

.stack-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
}

.stack-card {
  padding: 1.2rem;
  transition: 0.25s ease;
}

.stack-card h3 {
  margin-bottom: 1rem;
  font-size: 1.3rem;
}

.stack-items {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 0.7rem;
}

.stack-item {
  display: flex;
  align-items: center;
  gap: 0.65rem;
  min-height: 3.4rem;
  padding: 0.6rem;
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 7px;
  background: rgba(255, 255, 255, 0.045);
  color: rgba(247, 247, 239, 0.82);
  font-family: 'Gilroy Medium', system-ui, sans-serif;
}

.stack-item img {
  width: 1.55rem;
  height: 1.55rem;
  object-fit: contain;
  border-radius: 4px;
}

.contact-section {
  width: min(1120px, calc(100% - 2rem));
  margin: 0 auto;
  padding: 5rem 0 4rem;
}

.contact-panel {
  padding: clamp(1.5rem, 5vw, 4rem);
  background:
    linear-gradient(135deg, rgba(131, 247, 189, 0.14), rgba(255, 210, 125, 0.09)),
    rgba(255, 255, 255, 0.055);
}

.contact-panel p:not(.section-kicker) {
  max-width: 720px;
  margin: 1.2rem 0 0;
  font-size: 1.05rem;
}

.light-mode .site-nav {
  border-color: rgba(13, 25, 22, 0.12);
  background: rgba(255, 255, 255, 0.78);
  box-shadow: 0 22px 70px rgba(31, 62, 52, 0.16);
}

.light-mode .nav-links {
  background: rgba(13, 25, 22, 0.055);
}

.light-mode .nav-links a {
  color: rgba(16, 21, 19, 0.68);
}

.light-mode .nav-links a:hover {
  color: #101513;
  background: rgba(13, 25, 22, 0.08);
}

.light-mode .brand-copy,
.light-mode .hero-copy h1,
.light-mode .section-heading h2,
.light-mode .contact-panel h2,
.light-mode .experience-topline h3,
.light-mode .project-body h3,
.light-mode .stack-card h3,
.light-mode .credential-card h3 {
  color: #101513;
}

.light-mode .hero-text,
.light-mode .stat-card span,
.light-mode .project-description,
.light-mode .experience-content li,
.light-mode .contact-panel p,
.light-mode .credential-card li,
.light-mode .education-item span,
.light-mode .education-item small,
.light-mode .stack-item {
  color: rgba(16, 21, 19, 0.72);
}

.light-mode .stat-card,
.light-mode .experience-card,
.light-mode .project-card,
.light-mode .stack-card,
.light-mode .credential-card,
.light-mode .contact-panel,
.light-mode .education-item,
.light-mode .stack-item {
  border-color: rgba(13, 25, 22, 0.1);
  background: rgba(255, 255, 255, 0.66);
  box-shadow: 0 22px 70px rgba(31, 62, 52, 0.12);
}

.light-mode .icon-button,
.light-mode .resume-pill,
.light-mode .theme-float,
.light-mode .secondary-cta {
  border-color: rgba(13, 25, 22, 0.12);
  background: rgba(255, 255, 255, 0.72);
  color: #101513;
}

.light-mode .theme-float {
  color: #26324a;
  box-shadow: 0 22px 70px rgba(31, 62, 52, 0.16);
}

.light-mode .github-button {
  background: #181717;
}

.light-mode .capability-row span,
.light-mode .tag-row span {
  border-color: rgba(13, 25, 22, 0.11);
  color: rgba(16, 21, 19, 0.72);
  background: rgba(255, 255, 255, 0.58);
}

.light-mode .portrait-panel {
  border-color: rgba(13, 25, 22, 0.12);
  box-shadow: 0 30px 90px rgba(31, 62, 52, 0.18);
}

.light-mode .project-media {
  background: rgba(13, 25, 22, 0.05);
}

@media (max-width: 980px) {
  .site-nav {
    align-items: flex-start;
  }

  .brand-copy,
  .nav-links {
    display: none;
  }

  .hero-grid,
  .project-grid,
  .credentials-grid,
  .stack-grid {
    grid-template-columns: 1fr;
  }

  .hero-grid {
    min-height: auto;
  }

  .hero-visual {
    min-height: auto;
  }

  .portrait-panel {
    height: min(620px, 118vw);
  }

  .stats-grid {
    grid-template-columns: 1fr;
  }

  .theme-float {
    top: 4.45rem;
    right: 1rem;
  }
}

@media (max-width: 640px) {
  .site-nav {
    top: 0.65rem;
    width: calc(100% - 1rem);
    justify-content: center;
    padding: 0.55rem;
  }

  .brand {
    display: none;
  }

  .nav-actions {
    justify-content: center;
    gap: 0.25rem;
  }

  .icon-button {
    width: 2rem;
    height: 2rem;
  }

  .icon-button img {
    width: 1rem;
    height: 1rem;
  }

  .leetcode-button img {
    width: 1.18rem;
    height: 1.18rem;
  }

  .resume-pill {
    min-height: 2rem;
    padding: 0 0.55rem;
    font-size: 0.82rem;
  }

  .theme-float {
    top: 3.65rem;
    right: 0.75rem;
    width: 2.25rem;
    height: 2.25rem;
    font-size: 1.05rem;
  }

  .hero-section {
    padding-top: 7.5rem;
  }

  .hero-copy h1 {
    font-size: clamp(2.7rem, 16vw, 4.2rem);
  }

  .hero-actions,
  .contact-actions {
    align-items: stretch;
    flex-direction: column;
  }

  .primary-cta,
  .secondary-cta {
    width: 100%;
  }

  .experience-card,
  .experience-topline {
    grid-template-columns: 1fr;
  }

  .experience-card {
    display: block;
  }

  .company-logo {
    margin-bottom: 1rem;
  }

  .experience-topline {
    display: grid;
  }

  .experience-topline > span {
    order: -1;
  }

  .stack-items {
    grid-template-columns: 1fr;
  }
}
</style>
