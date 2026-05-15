<script setup lang="ts">
import { ref, onMounted } from 'vue'

// Skills data
const skills = [
  { name: 'Vue.js', level: 92, category: 'Frontend' },
  { name: 'TypeScript', level: 85, category: 'Frontend' },
  { name: 'Tailwind CSS', level: 88, category: 'Frontend' },
  { name: 'React', level: 78, category: 'Frontend' },
  { name: 'Flask', level: 90, category: 'Backend' },
  { name: 'Python', level: 92, category: 'Backend' },
  { name: 'Node.js', level: 80, category: 'Backend' },
  { name: 'PostgreSQL', level: 82, category: 'Backend' },
  { name: 'Docker', level: 88, category: 'DevOps' },
  { name: 'Linux', level: 85, category: 'DevOps' },
  { name: 'Nginx', level: 80, category: 'DevOps' },
  { name: 'Git', level: 90, category: 'DevOps' },
]

// Projects data
const projects = [
  {
    name: 'Driz-Web-Server',
    desc: 'Real-time server monitoring dashboard built with Vue 3, Flask-SocketIO, and Chart.js. Features live CPU, RAM, and network stats.',
    tech: ['Vue 3', 'Flask', 'SocketIO', 'Chart.js', 'Docker'],
    link: 'https://github.com/andrizpray/Driz-Web-Server',
    stars: 12,
  },
  {
    name: 'Trading-Monitor',
    desc: 'Cryptocurrency portfolio tracker with real-time price alerts and automated trading bot integration.',
    tech: ['Vue 3', 'Flask', 'PostgreSQL', 'WebSocket'],
    link: 'https://github.com/andrizpray/Trading-Monitor',
    stars: 8,
  },
  {
    name: 'Cloud-Mail',
    desc: 'Self-hosted email marketing platform with template builder and campaign analytics.',
    tech: ['Vue 3', 'Flask', 'Redis', 'Docker'],
    link: 'https://github.com/andrizpray/Cloud-Mail',
    stars: 5,
  },
  {
    name: 'HerPanel',
    desc: 'Admin panel for managing cloud infrastructure with user management and billing integration.',
    tech: ['Vue 3', 'Flask', 'MySQL', 'Nginx'],
    link: 'https://github.com/andrizpray/HerPanel',
    stars: 6,
  },
]

// Server stats for hero (simulated)
const serverStats = ref([
  { label: 'CPU', value: 23, color: 'bg-emerald-500' },
  { label: 'RAM', value: 47, color: 'bg-cyan-500' },
  { label: 'DISK', value: 62, color: 'bg-blue-500' },
])

onMounted(() => {
  // Simulate live stats
  setInterval(() => {
    serverStats.value = serverStats.value.map(stat => ({
      ...stat,
      value: Math.max(5, Math.min(95, stat.value + (Math.random() - 0.5) * 10))
    }))
  }, 2000)
})
</script>

<template>
  <div class="min-h-screen bg-[#0a0f1a] text-slate-400">
    <!-- Background grid pattern -->
    <div class="fixed inset-0 bg-[linear-gradient(rgba(30,58,95,0.15)_1px,transparent_1px),linear-gradient(90deg,rgba(30,58,95,0.15)_1px,transparent_1px)] bg-[size:60px_60px] pointer-events-none"></div>

    <!-- Navigation -->
    <nav class="fixed top-0 left-0 right-0 z-50 bg-[#0a0f1a]/90 backdrop-blur-md border-b border-[#1e3a5f]">
      <div class="max-w-5xl mx-auto px-6 py-4 flex items-center justify-between">
        <div class="font-mono text-sm text-slate-300">
          <span class="text-cyan-500">~/</span>andriz
        </div>
        <div class="flex gap-6 text-sm">
          <a href="#home" class="hover:text-cyan-400 transition-colors">Home</a>
          <a href="#about" class="hover:text-cyan-400 transition-colors">About</a>
          <a href="#skills" class="hover:text-cyan-400 transition-colors">Skills</a>
          <a href="#projects" class="hover:text-cyan-400 transition-colors">Projects</a>
          <a href="#contact" class="hover:text-cyan-400 transition-colors">Contact</a>
        </div>
      </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="min-h-screen flex items-center justify-center pt-20 px-6">
      <div class="max-w-4xl w-full">
        <div class="flex flex-col lg:flex-row gap-12 items-center">
          <!-- Text -->
          <div class="flex-1 text-center lg:text-left">
            <div class="inline-flex items-center gap-2 px-3 py-1 bg-emerald-500/10 border border-emerald-500/30 rounded-full text-emerald-400 text-xs font-mono mb-6">
              <span class="w-2 h-2 bg-emerald-400 rounded-full animate-pulse"></span>
              Available for projects
            </div>
            <h1 class="text-4xl lg:text-5xl font-bold text-slate-100 mb-4 leading-tight">
              Andriz Pray
            </h1>
            <h2 class="text-xl lg:text-2xl text-cyan-400 font-medium mb-6">
              Full Stack Developer
            </h2>
            <p class="text-slate-400 mb-8 leading-relaxed">
              Building scalable web applications and cloud infrastructure.
              Specializing in Vue.js, Flask, Docker, and real-time systems.
            </p>
            <div class="flex gap-4 justify-center lg:justify-start">
              <a href="#projects" class="px-6 py-3 bg-blue-600 hover:bg-blue-500 text-white rounded-lg font-medium transition-colors">
                View Projects
              </a>
              <a href="#contact" class="px-6 py-3 border border-[#1e3a5f] hover:border-cyan-500/50 text-slate-300 hover:text-cyan-400 rounded-lg font-medium transition-colors">
                Contact Me
              </a>
            </div>
          </div>

          <!-- Server Status Widget -->
          <div class="w-80 bg-[#111827] border border-[#1e3a5f] rounded-xl p-6 shadow-xl shadow-blue-900/10">
            <div class="flex items-center gap-3 mb-6">
              <div class="flex gap-1.5">
                <div class="w-3 h-3 rounded-full bg-red-500"></div>
                <div class="w-3 h-3 rounded-full bg-yellow-500"></div>
                <div class="w-3 h-3 rounded-full bg-emerald-500"></div>
              </div>
              <span class="text-xs font-mono text-slate-500">server.status</span>
            </div>

            <div class="space-y-4">
              <div v-for="stat in serverStats" :key="stat.label" class="space-y-2">
                <div class="flex justify-between text-xs font-mono">
                  <span class="text-slate-500">{{ stat.label }}</span>
                  <span class="text-slate-300">{{ stat.value.toFixed(0) }}%</span>
                </div>
                <div class="h-2 bg-[#1e3a5f] rounded-full overflow-hidden">
                  <div
                    class="h-full rounded-full transition-all duration-500"
                    :class="stat.color"
                    :style="{ width: `${stat.value}%` }"
                  ></div>
                </div>
              </div>
            </div>

            <div class="mt-6 pt-4 border-t border-[#1e3a5f]">
              <div class="flex justify-between text-xs font-mono">
                <span class="text-slate-500">Uptime</span>
                <span class="text-emerald-400">99.9%</span>
              </div>
              <div class="flex justify-between text-xs font-mono mt-2">
                <span class="text-slate-500">Region</span>
                <span class="text-cyan-400">Singapore</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Scroll indicator -->
        <div class="absolute bottom-10 left-1/2 -translate-x-1/2 flex flex-col items-center gap-2 text-slate-500">
          <span class="text-xs font-mono">scroll</span>
          <div class="w-5 h-8 border border-slate-600 rounded-full flex justify-center pt-2">
            <div class="w-1 h-2 bg-slate-500 rounded-full animate-bounce"></div>
          </div>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-24 px-6">
      <div class="max-w-4xl mx-auto">
        <div class="flex items-center gap-3 mb-8">
          <span class="text-cyan-400 font-mono text-sm">01.</span>
          <h2 class="text-2xl font-bold text-slate-100">About Me</h2>
          <div class="flex-1 h-px bg-[#1e3a5f]"></div>
        </div>

        <div class="grid lg:grid-cols-2 gap-12">
          <div class="space-y-4 text-slate-400 leading-relaxed">
            <p>
              Hello! I'm Andriz, a full-stack developer based in Indonesia with a passion for building
              reliable and scalable web applications.
            </p>
            <p>
              I specialize in developing complete web solutions — from responsive frontend interfaces
              built with Vue.js, to robust backend APIs with Flask and Python.
            </p>
            <p>
              My focus is on DevOps practices: containerizing applications with Docker, setting up
              CI/CD pipelines, and maintaining Linux servers for production deployments.
            </p>
            <p>
              When I'm not coding, you'll find me exploring new technologies, contributing to open-source,
              or optimizing my home lab server setup.
            </p>
          </div>

          <div class="space-y-6">
            <div class="bg-[#111827] border border-[#1e3a5f] rounded-xl p-6">
              <h3 class="text-slate-100 font-semibold mb-4">What I Do</h3>
              <ul class="space-y-3">
                <li class="flex items-start gap-3">
                  <span class="text-cyan-400 mt-1">▹</span>
                  <span>Full-stack web development (Vue.js + Flask)</span>
                </li>
                <li class="flex items-start gap-3">
                  <span class="text-cyan-400 mt-1">▹</span>
                  <span>Cloud infrastructure & server management</span>
                </li>
                <li class="flex items-start gap-3">
                  <span class="text-cyan-400 mt-1">▹</span>
                  <span>Docker containerization & deployment</span>
                </li>
                <li class="flex items-start gap-3">
                  <span class="text-cyan-400 mt-1">▹</span>
                  <span>Real-time data visualization dashboards</span>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="py-24 px-6 bg-[#0d1321]">
      <div class="max-w-4xl mx-auto">
        <div class="flex items-center gap-3 mb-12">
          <span class="text-cyan-400 font-mono text-sm">02.</span>
          <h2 class="text-2xl font-bold text-slate-100">Skills & Tech</h2>
          <div class="flex-1 h-px bg-[#1e3a5f]"></div>
        </div>

        <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
          <div
            v-for="skill in skills"
            :key="skill.name"
            class="group bg-[#111827] border border-[#1e3a5f] hover:border-cyan-500/50 rounded-lg p-4 transition-all duration-300 hover:-translate-y-1 hover:shadow-lg hover:shadow-cyan-900/20"
          >
            <div class="flex justify-between items-center mb-3">
              <span class="text-slate-200 text-sm font-medium">{{ skill.name }}</span>
              <span class="text-xs text-slate-500 font-mono">{{ skill.level }}%</span>
            </div>
            <div class="h-1.5 bg-[#1e3a5f] rounded-full overflow-hidden">
              <div
                class="h-full bg-gradient-to-r from-blue-600 to-cyan-500 rounded-full transition-all duration-700 group-hover:shadow-lg group-hover:shadow-cyan-500/30"
                :style="{ width: `${skill.level}%` }"
              ></div>
            </div>
            <span class="text-xs text-slate-500 mt-2 block">{{ skill.category }}</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="py-24 px-6">
      <div class="max-w-4xl mx-auto">
        <div class="flex items-center gap-3 mb-12">
          <span class="text-cyan-400 font-mono text-sm">03.</span>
          <h2 class="text-2xl font-bold text-slate-100">Featured Projects</h2>
          <div class="flex-1 h-px bg-[#1e3a5f]"></div>
        </div>

        <div class="grid md:grid-cols-2 gap-6">
          <a
            v-for="project in projects"
            :key="project.name"
            :href="project.link"
            target="_blank"
            class="group bg-[#111827] border border-[#1e3a5f] hover:border-blue-500/50 rounded-xl p-6 transition-all duration-300 hover:-translate-y-1 hover:shadow-xl hover:shadow-blue-900/20"
          >
            <div class="flex justify-between items-start mb-4">
              <div class="w-12 h-12 bg-[#1e3a5f] group-hover:bg-blue-600/20 rounded-lg flex items-center justify-center transition-colors">
                <svg class="w-6 h-6 text-slate-400 group-hover:text-cyan-400 transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M3 7v10a2 2 0 002 2h14a2 2 0 002-2V9a2 2 0 00-2-2h-6l-2-2H5a2 2 0 00-2 2z" />
                </svg>
              </div>
              <div class="flex items-center gap-2 text-slate-500">
                <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M12 0l3.09 6.26L22 7.27l-5 4.87 1.18 6.88L12 15.77l-6.18 3.25L7 12.14 2 7.27l6.91-1.01L12 0z"/>
                </svg>
                <span class="text-sm">{{ project.stars }}</span>
              </div>
            </div>

            <h3 class="text-lg font-semibold text-slate-100 mb-2 group-hover:text-cyan-400 transition-colors">
              {{ project.name }}
            </h3>
            <p class="text-sm text-slate-400 mb-4 leading-relaxed">
              {{ project.desc }}
            </p>

            <div class="flex flex-wrap gap-2">
              <span
                v-for="tech in project.tech"
                :key="tech"
                class="text-xs font-mono px-2 py-1 bg-[#1e3a5f] text-slate-400 rounded"
              >
                {{ tech }}
              </span>
            </div>
          </a>
        </div>

        <div class="mt-12 text-center">
          <a
            href="https://github.com/andrizpray"
            target="_blank"
            class="inline-flex items-center gap-2 text-cyan-400 hover:text-cyan-300 transition-colors"
          >
            <span>View all projects on GitHub</span>
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
            </svg>
          </a>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-24 px-6 bg-[#0d1321]">
      <div class="max-w-2xl mx-auto text-center">
        <div class="flex items-center justify-center gap-3 mb-8">
          <span class="text-cyan-400 font-mono text-sm">04.</span>
          <h2 class="text-2xl font-bold text-slate-100">Get In Touch</h2>
        </div>

        <p class="text-slate-400 mb-8 leading-relaxed">
          I'm currently open to freelance projects and full-time opportunities.
          Whether you have a question or just want to say hi, feel free to reach out!
        </p>

        <div class="flex flex-col sm:flex-row gap-4 justify-center mb-12">
          <a
            href="mailto:andrizpray@gmail.com"
            class="px-8 py-4 bg-blue-600 hover:bg-blue-500 text-white rounded-lg font-medium transition-colors"
          >
            Send Email
          </a>
          <a
            href="https://github.com/andrizpray"
            target="_blank"
            class="px-8 py-4 border border-[#1e3a5f] hover:border-cyan-500/50 text-slate-300 hover:text-cyan-400 rounded-lg font-medium transition-colors"
          >
            GitHub Profile
          </a>
        </div>

        <!-- Social Links -->
        <div class="flex justify-center gap-6">
          <a href="https://github.com/andrizpray" target="_blank" class="text-slate-500 hover:text-slate-300 transition-colors">
            <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
              <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
            </svg>
          </a>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="py-8 px-6 border-t border-[#1e3a5f]">
      <div class="max-w-4xl mx-auto flex flex-col sm:flex-row justify-between items-center gap-4 text-sm text-slate-500">
        <span class="font-mono">
          <span class="text-cyan-500">$</span> andrizpray — {{ new Date().getFullYear() }}
        </span>
        <span class="font-mono">
          Built with <span class="text-cyan-400">Vue 3</span> + <span class="text-cyan-400">Tailwind</span>
        </span>
      </div>
    </footer>
  </div>
</template>
