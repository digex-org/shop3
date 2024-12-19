<template>
  <header class="relative bg-white shadow-md">
    <!-- Main Navigation -->
    <nav class="container mx-auto flex justify-center space-x-8 py-4 text-gray-700">
      <div
          v-for="menu in menus"
          :key="menu.id"
          class="relative group"
      >
        <!-- Main Menu Item -->
        <a href="#" class="uppercase hover:text-gray-900 flex items-center">
          <img :src="menu.image" :alt="menu.name" class="w-8 h-8 mr-2" />
          {{ menu.name }}
        </a>

        <!-- Submenu -->
        <div
            v-if="menu.subMenu && menu.subMenu.length > 0"
            class="absolute left-0 hidden group-hover:block bg-pink-100 w-[400px] p-6 shadow-lg z-10"
        >
          <div v-for="sub in menu.subMenu" :key="sub.name" class="mb-4">
            <!-- Submenu Section Title -->
            <h4 class="font-semibold text-gray-700">{{ sub.name }}</h4>
            <!-- Submenu Links -->
            <ul class="mt-2 space-y-1">
              <li
                  v-for="item in sub.subMenu"
                  :key="item.name"
                  class="text-gray-600 hover:text-gray-900"
              >
                <a href="#">{{ item.name }}</a>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </nav>
  </header>
</template>

<script setup>
import { useMenus } from "@/composables/useMenus"; // Adjust path if necessary

// Fetch menus from the useMenus hook
const { menus } = useMenus();
</script>

<style scoped>
/* Optional: Additional styling */
</style>
