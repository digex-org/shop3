<template>
  <section class="py-8 px-4">
    <div class="grid grid-cols-4 gap-4">
      <!-- Large image -->
      <div class="col-span-4 md:col-span-2 row-span-2 relative group">
        <a :href="images[0].link" target="_blank" class="block h-full">
          <img
              :src="images[0].src"
              :alt="images[0].alt"
              class="w-full md:h-full h-[350px] object-cover rounded-lg"
          />
          <div
              class="absolute inset-0 bg-black bg-opacity-30 opacity-0 group-hover:opacity-100 transition duration-300 flex items-center justify-center"
          >
            <span
                class="text-white font-bold bg-pink-500 px-4 py-2 rounded shadow-md"
            >{{ images[0].caption }}</span
            >
          </div>
        </a>
      </div>

      <!-- Small images -->
      <div
          v-for="(image, index) in images.slice(1)"
          :key="index"
          class="relative group col-span-4 md:col-span-1"
      >
        <a :href="image.link" target="_blank" class="block">
          <img
              :src="image.src"
              :alt="image.alt"
              class="md:w-[309px] md:h-[309px] w-full h-[350px] object-cover rounded-lg"
          />
          <div
              class="absolute inset-0 bg-black bg-opacity-30 opacity-0 group-hover:opacity-100 transition duration-300 flex items-center justify-center"
          >
            <span
                class="text-white font-bold bg-pink-500 px-4 py-2 rounded shadow-md"
            >{{ image.caption }}</span
            >
          </div>
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const images = ref([
  {
    src: '/images/categories/category-1.png',
    alt: 'Girl with a phone holder',
    link: 'https://www.instagram.com/example1',
    caption: 'See Product',
  },
  {
    src: '/images/categories/category-2.png',
    alt: 'Friends smiling together',
    link: 'https://www.instagram.com/example2',
    caption: 'See Product',
  },
  {
    src: '/images/products/prod3.png',
    alt: 'Stylish hair scrunchies',
    link: 'https://www.instagram.com/example3',
    caption: 'See Product',
  },
  {
    src: '/images/products/prod1.png',
    alt: 'Cute graphic tees',
    link: 'https://www.instagram.com/example4',
    caption: 'See Product',
  },
  {
    src: '/images/categories/category-2.png',
    alt: 'Friends smiling together',
    link: 'https://www.instagram.com/example2',
    caption: 'See Product',
  },
]);
</script>

<style>
/* Additional spacing customization can go here if needed */
</style>
