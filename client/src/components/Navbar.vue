<template>
  <nav class="fixed top-0 left-0 w-full bg-black bg-opacity-50 text-white shadow-lg z-50">
    <div class="max-w-7xl mx-auto flex items-center justify-between px-4 py-3">
      <div class="text-2xl font-bold">Badener Cars</div>

      <!-- Hamburger icon (mobile only) -->
      <button
        class="md:hidden flex items-center px-3 py-2 border border-white rounded text-white hover:text-yellow-400"
        @click="isOpen = !isOpen"
      >
        <svg class="fill-current h-4 w-4" viewBox="0 0 20 20">
          <path d="M0 3h20v2H0zM0 9h20v2H0zM0 15h20v2H0z" />
        </svg>
      </button>

      <!-- Main menu -->
      <ul
        class="hidden md:flex gap-6 text-sm uppercase font-medium"
      >
        <li><a href="#home" class="hover:text-yellow-400">Accueil</a></li>
        <li><a href="#about" class="hover:text-yellow-400">À propos de nous</a></li>
        <li><a href="#activité" class="hover:text-yellow-400">Activités</a></li>
        <li><a href="#nos véhicules" class="hover:text-yellow-400">Nos véhicules</a></li>
        <li><a href="#contact" class="hover:text-yellow-400">Contact</a></li>
      </ul>

      <!-- Language selector (desktop only) -->
      <div class="hidden md:block">
        <select class="bg-transparent text-white border border-white px-2 py-1 rounded focus:outline-none">
          <option>FR</option>
          <option>EN</option>
          <option>DE</option>
        </select>
      </div>
    </div>

    <!-- Mobile menu -->
    <div v-if="isOpen" class="md:hidden px-4 pb-4">
      <ul class="flex flex-col gap-2 text-sm uppercase font-medium">
        <li><a href="#home" class="hover:text-yellow-400">Accueil</a></li>
        <li><a href="#about" class="hover:text-yellow-400">À propos de nous</a></li>
        <li><a href="#activité" class="hover:text-yellow-400">Activités</a></li>
        <li><a href="#nos véhicules" class="hover:text-yellow-400">Nos véhicules</a></li>
        <li><a href="#contact" class="hover:text-yellow-400">Contact</a></li>
        <li>
          <select class="w-full bg-transparent text-white border border-white px-2 py-1 rounded focus:outline-none">
            <option>FR</option>
            <option>EN</option>
            <option>DE</option>
          </select>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script setup>
import { ref } from 'vue'
const isOpen = ref(false)
</script>
