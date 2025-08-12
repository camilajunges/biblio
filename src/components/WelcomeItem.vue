<template>
  <div class="min-h-screen bg-white">
    <!-- Navigation -->
    <nav class="bg-white shadow-sm border-b">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex justify-between items-center h-16">
          <div class="flex items-center">
            <div class="flex-shrink-0">
              <h1 class="text-2xl font-bold text-blue-900">LibraryHub</h1>
            </div>
          </div>
          <div class="hidden md:block">
            <div class="ml-10 flex items-baseline space-x-4">
              <a href="#" class="text-gray-700 hover:text-blue-900 px-3 py-2 text-sm font-medium">Catalog</a>
              <a href="#" class="text-gray-700 hover:text-blue-900 px-3 py-2 text-sm font-medium">Services</a>
              <a href="#" class="text-gray-700 hover:text-blue-900 px-3 py-2 text-sm font-medium">About</a>
              <button class="bg-blue-600 text-white px-4 py-2 rounded-lg text-sm font-medium hover:bg-blue-700 transition-colors">
                Sign In
              </button>
            </div>
          </div>
        </div>
      </div>
    </nav>

    <!-- Hero Section -->
    <section class="bg-gradient-to-br from-blue-50 to-indigo-100 py-20">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center">
          <h1 class="text-4xl md:text-6xl font-bold text-gray-900 mb-6">
            Your Gateway to
            <span class="text-blue-600">Knowledge</span>
          </h1>
          <p class="text-xl text-gray-600 mb-8 max-w-3xl mx-auto">
            Discover millions of books, digital resources, and research materials. 
            Access your library anytime, anywhere with our modern digital platform.
          </p>
          <div class="flex flex-col sm:flex-row gap-4 justify-center">
            <button class="bg-blue-600 text-white px-8 py-3 rounded-lg text-lg font-semibold hover:bg-blue-700 transition-colors">
              Browse Catalog
            </button>
            <button class="border-2 border-blue-600 text-blue-600 px-8 py-3 rounded-lg text-lg font-semibold hover:bg-blue-50 transition-colors">
              Get Library Card
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- Stats Section -->
    <section class="py-16 bg-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-2 md:grid-cols-4 gap-8 text-center">
          <div>
            <div class="text-3xl font-bold text-blue-600 mb-2">{{ stats.books.toLocaleString() }}</div>
            <div class="text-gray-600">Books Available</div>
          </div>
          <div>
            <div class="text-3xl font-bold text-blue-600 mb-2">{{ stats.members.toLocaleString() }}</div>
            <div class="text-gray-600">Active Members</div>
          </div>
          <div>
            <div class="text-3xl font-bold text-blue-600 mb-2">{{ stats.digital.toLocaleString() }}</div>
            <div class="text-gray-600">Digital Resources</div>
          </div>
          <div>
            <div class="text-3xl font-bold text-blue-600 mb-2">{{ stats.locations }}</div>
            <div class="text-gray-600">Locations</div>
          </div>
        </div>
      </div>
    </section>

    <!-- Features Section -->
    <section class="py-20 bg-gray-50">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">
            Everything You Need in One Place
          </h2>
          <p class="text-xl text-gray-600 max-w-2xl mx-auto">
            From physical books to digital resources, we provide comprehensive library services for the modern world.
          </p>
        </div>
        
        <div class="grid md:grid-cols-3 gap-8">
          <div v-for="feature in features" :key="feature.title" class="bg-white p-8 rounded-xl shadow-sm hover:shadow-md transition-shadow">
            <div class="w-12 h-12 bg-blue-100 rounded-lg flex items-center justify-center mb-6">
              <div class="text-blue-600 text-2xl">{{ feature.icon }}</div>
            </div>
            <h3 class="text-xl font-semibold text-gray-900 mb-4">{{ feature.title }}</h3>
            <p class="text-gray-600">{{ feature.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Services Section -->
    <section class="py-20 bg-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid lg:grid-cols-2 gap-12 items-center">
          <div>
            <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-6">
              Modern Library Services
            </h2>
            <p class="text-lg text-gray-600 mb-8">
              Experience the future of library services with our digital-first approach while maintaining the charm of traditional library experiences.
            </p>
            <div class="space-y-4">
              <div v-for="service in services" :key="service" class="flex items-center">
                <div class="w-6 h-6 bg-green-100 rounded-full flex items-center justify-center mr-3">
                  <div class="w-2 h-2 bg-green-600 rounded-full"></div>
                </div>
                <span class="text-gray-700">{{ service }}</span>
              </div>
            </div>
          </div>
          <div class="bg-gradient-to-br from-blue-500 to-purple-600 rounded-2xl p-8 text-white">
            <h3 class="text-2xl font-bold mb-4">Digital Library Access</h3>
            <p class="mb-6 opacity-90">
              Access thousands of e-books, audiobooks, and digital magazines from anywhere. 
              Download our mobile app for offline reading.
            </p>
            <button class="bg-white text-blue-600 px-6 py-3 rounded-lg font-semibold hover:bg-gray-100 transition-colors">
              Download App
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA Section -->
    <section class="py-20 bg-blue-600">
      <div class="max-w-4xl mx-auto text-center px-4 sm:px-6 lg:px-8">
        <h2 class="text-3xl md:text-4xl font-bold text-white mb-6">
          Ready to Start Your Learning Journey?
        </h2>
        <p class="text-xl text-blue-100 mb-8">
          Join thousands of readers and researchers who trust LibraryHub for their knowledge needs.
        </p>
        <div class="flex flex-col sm:flex-row gap-4 justify-center">
          <button class="bg-white text-blue-600 px-8 py-3 rounded-lg text-lg font-semibold hover:bg-gray-100 transition-colors">
            Get Started Today
          </button>
          <button class="border-2 border-white text-white px-8 py-3 rounded-lg text-lg font-semibold hover:bg-blue-700 transition-colors">
            Schedule Tour
          </button>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-900 text-white py-12">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid md:grid-cols-4 gap-8">
          <div>
            <h3 class="text-xl font-bold mb-4">LibraryHub</h3>
            <p class="text-gray-400">
              Connecting communities through knowledge and learning opportunities.
            </p>
          </div>
          <div>
            <h4 class="font-semibold mb-4">Services</h4>
            <ul class="space-y-2 text-gray-400">
              <li><a href="#" class="hover:text-white transition-colors">Book Catalog</a></li>
              <li><a href="#" class="hover:text-white transition-colors">Digital Resources</a></li>
              <li><a href="#" class="hover:text-white transition-colors">Research Help</a></li>
              <li><a href="#" class="hover:text-white transition-colors">Study Spaces</a></li>
            </ul>
          </div>
          <div>
            <h4 class="font-semibold mb-4">Support</h4>
            <ul class="space-y-2 text-gray-400">
              <li><a href="#" class="hover:text-white transition-colors">Help Center</a></li>
              <li><a href="#" class="hover:text-white transition-colors">Contact Us</a></li>
              <li><a href="#" class="hover:text-white transition-colors">Library Hours</a></li>
              <li><a href="#" class="hover:text-white transition-colors">Locations</a></li>
            </ul>
          </div>
          <div>
            <h4 class="font-semibold mb-4">Connect</h4>
            <ul class="space-y-2 text-gray-400">
              <li><a href="#" class="hover:text-white transition-colors">Newsletter</a></li>
              <li><a href="#" class="hover:text-white transition-colors">Events</a></li>
              <li><a href="#" class="hover:text-white transition-colors">Community</a></li>
              <li><a href="#" class="hover:text-white transition-colors">Blog</a></li>
            </ul>
          </div>
        </div>
        <div class="border-t border-gray-800 mt-8 pt-8 text-center text-gray-400">
          <p>&copy; 2025 LibraryHub. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const stats = ref({
  books: 250000,
  members: 45000,
  digital: 15000,
  locations: 12
})

const features = ref([
  {
    icon: '📚',
    title: 'Vast Collection',
    description: 'Access millions of books, journals, and digital resources across all subjects and genres.'
  },
  {
    icon: '💻',
    title: 'Digital Access',
    description: 'Browse and borrow e-books, audiobooks, and digital magazines from any device.'
  },
  {
    icon: '🔍',
    title: 'Research Tools',
    description: 'Advanced search capabilities and research assistance from professional librarians.'
  },
  {
    icon: '📱',
    title: 'Mobile App',
    description: 'Take your library with you. Read offline and manage your account on the go.'
  },
  {
    icon: '🏢',
    title: 'Study Spaces',
    description: 'Reserve quiet study rooms and collaborative spaces for individual or group work.'
  },
  {
    icon: '🎓',
    title: 'Learning Programs',
    description: 'Join workshops, book clubs, and educational programs for all ages.'
  }
])

const services = ref([
  'Online catalog with real-time availability',
  'Digital book and audiobook lending',
  'Research database access',
  'Inter-library loan services',
  'Computer and internet access',
  'Printing and scanning facilities',
  'Children and teen programs',
  'Adult education classes'
])
</script>