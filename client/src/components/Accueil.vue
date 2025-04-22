<template>
  <!-- Section 1 : Hero avec slideshow -->
  <section id="home" class="relative h-screen flex items-center justify-center text-center text-white">
    <div class="absolute inset-0">
      <img
        :src="currentImage"
        class="w-full h-full object-cover brightness-50 transition-opacity duration-1000 ease-in-out"
        alt="slideshow"
      />
    </div>

    <div class="relative z-10">
      <h1 class="text-5xl md:text-6xl font-bold mb-4">Bienvenue chez Badener Cars</h1>
      <p class="text-lg md:text-xl mb-6">Vente & location de voitures haut de gamme</p>
      <a
        href="https://wa.me/tonnumero"
        target="_blank"
        class="bg-yellow-400 text-black px-6 py-3 rounded-full text-lg hover:bg-yellow-500 transition"
      >
        Réserver via WhatsApp
      </a>
    </div>
  </section>

  <!-- Section 2 : À propos -->
  <section class="bg-white py-16 px-6 md:px-12 text-gray-800">
    <div class="max-w-7xl mx-auto grid md:grid-cols-2 gap-12 items-center">
      <!-- Texte -->
      <div>
        <h2 class="text-3xl md:text-4xl font-bold mb-6">Qui sommes-nous ?</h2>
        <p class="text-lg mb-4">
          Badener Cars est votre partenaire de confiance pour l’achat et la location de voitures de luxe.
          Nous mettons à votre disposition une flotte soigneusement sélectionnée pour répondre à vos exigences.
        </p>
        <ul class="space-y-3 mt-6">
          <li class="flex items-center">
            <span class="bg-yellow-400 text-black rounded-full w-6 h-6 flex items-center justify-center mr-3 font-bold">✓</span>
            Véhicules récents & bien entretenus
          </li>
          <li class="flex items-center">
            <span class="bg-yellow-400 text-black rounded-full w-6 h-6 flex items-center justify-center mr-3 font-bold">✓</span>
            Service client réactif
          </li>
          <li class="flex items-center">
            <span class="bg-yellow-400 text-black rounded-full w-6 h-6 flex items-center justify-center mr-3 font-bold">✓</span>
            Tarifs transparents & compétitifs
          </li>
        </ul>
      </div>

      <!-- Image illustrative -->
      <div>
        <img src="../assets/images/about.jpg" alt="Présentation Badener Cars" class="rounded-2xl shadow-lg w-full" />
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

import hero1 from '../assets/images/hero1.jpg'
import hero2 from '../assets/images/hero2.jpg'
import hero3 from '../assets/images/hero3.jpg'

const images = [hero1, hero2, hero3]
const currentImage = ref(images[0])

let index = 0

onMounted(() => {
  setInterval(() => {
    index = (index + 1) % images.length
    currentImage.value = images[index]
  }, 5000)
})
</script>

<style scoped>
.animate-fade {
  animation: fadeIn 1.5s ease-in-out;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}
</style>
