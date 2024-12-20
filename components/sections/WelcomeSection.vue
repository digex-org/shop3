<template>
  <section class="bg-[#EFEAFF] text-gray-800 py-12 mb-10">
    <div class="max-w-7xl mx-auto px-4 md:px-12 text-center">
      <!-- Title -->
      <div class="flex items-center justify-center mb-5">
        <h2 class="text-2xl md:text-3xl font-semibold mr-3">
          Welcome to
        </h2>
        <img src="/logo.png" alt="welcome logo">
      </div>
      <!-- Features -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-32 mt-8">
        <!-- Fan Looks -->
        <div class="flex flex-col items-center">
          <div class="text-gray-700 text-4xl">
            <img src="/images/icons/Star.svg" alt="star icon">
          </div>
          <p class="mt-4 text-sm text-[#5a5a5a]">
            We love seeing our gorgeous fans wearing Angel's Face... browse and shop some of our favorite looks here!
          </p>
          <a
              href="#"
              class="mt-4 font-semibold underline hover:text-gray-600"
          >
            View Fan Looks
          </a>
        </div>

        <!-- Our Story -->
        <div class="flex flex-col items-center">
          <div class="text-gray-700 text-4xl">
            <img src="/images/icons/home.svg" alt="home icon">
          </div>
          <p class="mt-4 text-sm italic text-[#5a5a5a]">
            “I can’t remember a time when I didn’t love fashion.” <br />– Keely Deininger
          </p>
          <a
              href="#"
              class="mt-4 font-semibold underline hover:text-gray-600"
          >
            Read our Story
          </a>
        </div>

        <!-- Blog -->
        <div class="flex flex-col items-center">
          <div class="text-gray-700 text-4xl">
            <img src="/images/icons/doc.svg" alt="doc icon">
          </div>
          <p class="mt-4 text-sm text-[#5a5a5a]">
            Looking for the latest fashion tips or what's happening over at Angel Face HQ?
          </p>
          <a
              href="#"
              class="mt-4 font-semibold underline hover:text-gray-600"
          >
            Read our Blog
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
// Make sure to include Font Awesome for the icons
</script>

<style>
/* Custom handwriting font for the title */
.font-handwriting {
  font-family: "Dancing Script", cursive;
}
</style>
