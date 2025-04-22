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

      
      <div>
        <img src="../assets/images/about.jpg" alt="Présentation Badener Cars" class="rounded-2xl shadow-lg w-full" />
      </div>
    </div>
  </section>
  <section class="bg-white py-16 px-6 md:px-12 text-gray-800">
    <h2 class="text-3xl md:text-4xl font-bold mb-12 text-center">Nos véhicules en vedette</h2>
    
    <div class="max-w-7xl mx-auto grid md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-8">
      <div
        v-for="(car, index) in cars.slice(0, 10)"
        :key="index"
        class="border rounded-xl shadow hover:shadow-lg transition duration-300 overflow-hidden flex flex-col"
      >
        <!-- Image principale -->
        <img
          :src="car.images[car.selectedImage]"
          :alt="car.name"
          class="w-full h-48 object-cover"
        />

        <!-- Miniatures -->
        <div class="flex justify-center gap-2 mt-2 px-4">
          <img
            v-for="(img, i) in car.images"
            :key="i"
            :src="img"
            class="w-12 h-12 object-cover border rounded cursor-pointer"
            :class="{ 'ring-2 ring-yellow-400': car.selectedImage === i }"
            @click="car.selectedImage = i"
          />
        </div>

        <!-- Détails -->
        <div class="p-4 flex flex-col justify-between flex-grow">
          <div>
            <h3 class="text-lg font-semibold mb-1">{{ car.name }}</h3>
            <p class="text-red-600 text-lg font-bold mb-2">{{ car.price }} €</p>
            <ul class="text-sm space-y-1 text-gray-600">
              <li><span class="font-medium">Kilométrage:</span> {{ car.km }} km</li>
              <li><span class="font-medium">Puissance:</span> {{ car.power }}</li>
              <li><span class="font-medium">Boîte:</span> {{ car.transmission }}</li>
            </ul>
          </div>
          <router-link
            :to="`/voiture/${slugify(car.name)}`"
            class="mt-4 inline-block bg-yellow-400 hover:bg-yellow-500 text-black px-4 py-2 text-sm font-semibold rounded-full text-center"
          >
            Voir plus
          </router-link>
        </div>
      </div>
    </div>

    <div class="flex justify-center mt-12">
      <router-link
        to="/nos-vehicules"
        class="bg-yellow-400 hover:bg-yellow-500 text-black px-8 py-3 text-lg font-semibold rounded-full shadow transition"
      >
        Voir plus de véhicules
      </router-link>
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
const slugify = (str) =>
  str
    .toLowerCase()
    .replace(/[^\w\s-]/g, "")
    .replace(/\s+/g, "-");

const cars = [
  {
    name: "MERCEDES CLASSE A 4 CLASSE A 250",
    images: [
      "https://imgur.com/GoAqekR",
      "https://imgur.com/MyyEYkG",
      "https://imgur.com/4IPOOZA",
     
    ],
    price: "20.500€",
    km: "8.900 KM",
    power: "224 kW",
    transmission: "AUTOMATIQUE",
    selectedImage: 0,
  },
  {
    name: "Smart Fortwo 2017",
    images: [
      "https://i.imgur.com/EXEMPLE3.jpg",
      "https://i.imgur.com/EXEMPLE4.jpg",
      "https://i.imgur.com/EXEMPLE5.jpg",
    ],
    price: "2610",
    km: "55500",
    power: "66 kW (90 CH)",
    transmission: "Automatique",
    selectedImage: 0,
  },
  
];

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
