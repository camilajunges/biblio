<template>
  <div class="min-h-screen bg-gradient-to-br from-slate-50 to-blue-50 flex items-center justify-center p-4">
    <div class="w-full max-w-6xl bg-white rounded-3xl shadow-2xl overflow-hidden">
      <div class="flex flex-col lg:flex-row min-h-[600px]">
        <!-- Hero Section -->
        <HeroSection 
          :app-name="appData.name"
          :subtitle="appData.subtitle" 
          :tagline="appData.tagline"
          :cta-text="appData.ctaText"
          @cta-click="handleCtaClick"
        />
        
        <!-- Features Section -->
        <FeaturesSection :features="features" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

// Application data - centralized and reactive
const appData = reactive({
  name: 'Biblio',
  subtitle: 'Your Library Management System',
  tagline: 'Efficiently manage your entire book collection with modern tools and intuitive design.',
  ctaText: 'Get Started'
})

// Features data - structured and maintainable
const features = ref([
  { 
    id: 1,
    name: 'CRUD Operations', 
    description: 'Create, read, update and delete book and author records effortlessly with our streamlined interface.',
    icon: 'database'
  },
  { 
    id: 2,
    name: 'Intuitive Interface', 
    description: 'Clean and modern user interface designed for fast navigation and optimal user experience.',
    icon: 'interface'
  },
  { 
    id: 3,
    name: 'Smart Search', 
    description: 'Find books instantly with powerful search algorithms and advanced filtering options.',
    icon: 'search'
  },
  { 
    id: 4,
    name: 'Responsive Design', 
    description: 'Access your library system seamlessly from any device - desktop, tablet, or mobile.',
    icon: 'responsive'
  }
])

// Event handlers - clean and focused
const handleCtaClick = () => {
  console.log('Starting library management journey!')
  // Add your navigation logic here
}
</script>

<!-- Hero Section Component -->
<template id="hero-section">
  <div class="flex-1 bg-gradient-to-br from-indigo-600 to-purple-700 text-white p-8 sm:p-12 lg:p-16 flex flex-col justify-center">
    <div class="max-w-lg">
      <h1 class="text-4xl sm:text-5xl lg:text-6xl font-bold mb-4 leading-tight">
        {{ appName }}
      </h1>
      <h2 class="text-xl sm:text-2xl lg:text-3xl font-semibold mb-6 text-indigo-100">
        {{ subtitle }}
      </h2>
      <p class="text-lg sm:text-xl mb-8 text-indigo-100 leading-relaxed">
        {{ tagline }}
      </p>
      <button 
        @click="$emit('cta-click')"
        class="group bg-white text-indigo-600 font-semibold py-4 px-8 rounded-full shadow-lg hover:shadow-xl transition-all duration-300 transform hover:scale-105 focus:outline-none focus:ring-4 focus:ring-white focus:ring-opacity-30"
      >
        <span class="flex items-center">
          {{ ctaText }}
          <svg class="ml-2 w-5 h-5 group-hover:translate-x-1 transition-transform duration-200" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6"></path>
          </svg>
        </span>
      </button>
    </div>
  </div>
</template>

<!-- Features Section Component -->
<template id="features-section">
  <div class="flex-1 bg-slate-50 p-8 sm:p-12 lg:p-16 flex flex-col justify-center">
    <div class="max-w-lg">
      <h2 class="text-3xl sm:text-4xl font-bold text-slate-800 mb-8">
        Key Features
      </h2>
      <div class="space-y-8">
        <FeatureItem 
          v-for="feature in features" 
          :key="feature.id"
          :feature="feature"
        />
      </div>
    </div>
  </div>
</template>

<!-- Feature Item Component -->
<template id="feature-item">
  <div class="flex items-start group">
    <div class="flex-shrink-0 w-12 h-12 bg-gradient-to-br from-indigo-500 to-purple-600 text-white rounded-xl flex items-center justify-center mr-4 group-hover:scale-110 transition-transform duration-200">
      <component :is="getIcon(feature.icon)" class="w-6 h-6" />
    </div>
    <div class="flex-1">
      <h3 class="text-xl font-semibold text-slate-800 mb-2">
        {{ feature.name }}
      </h3>
      <p class="text-slate-600 leading-relaxed">
        {{ feature.description }}
      </p>
    </div>
  </div>
</template>

<script>
// Hero Section Component
const HeroSection = {
  template: '#hero-section',
  props: ['appName', 'subtitle', 'tagline', 'ctaText'],
  emits: ['cta-click']
}

// Features Section Component  
const FeaturesSection = {
  template: '#features-section',
  props: ['features'],
  components: {
    FeatureItem
  }
}

// Feature Item Component
const FeatureItem = {
  template: '#feature-item',
  props: ['feature'],
  methods: {
    getIcon(iconType) {
      const icons = {
        database: {
          template: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 7v10c0 2.21 3.582 4 8 4s8-1.79 8-4V7M4 7c0 2.21 3.582 4 8 4s8-1.79 8-4M4 7c0-2.21 3.582-4 8-4s8 1.79 8 4"></path></svg>`
        },
        interface: {
          template: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path></svg>`
        },
        search: {
          template: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg>`
        },
        responsive: {
          template: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 18h.01M8 21h8a2 2 0 002-2V5a2 2 0 00-2-2H8a2 2 0 00-2 2v14a2 2 0 002 2z"></path></svg>`
        }
      }
      return icons[iconType] || icons.database
    }
  }
}

// Register components globally
const app = Vue.createApp({
  // Main app setup from above
})

app.component('HeroSection', HeroSection)
app.component('FeaturesSection', FeaturesSection) 
app.component('FeatureItem', FeatureItem)
</script>

<style scoped>
/* Custom animations and refinements */
.group:hover .group-hover\:translate-x-1 {
  transform: translateX(0.25rem);
}

.group:hover .group-hover\:scale-110 {
  transform: scale(1.1);
}

/* Smooth transitions for all interactive elements */
* {
  transition-property: transform, box-shadow, background-color;
  transition-duration: 200ms;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
}
</style>