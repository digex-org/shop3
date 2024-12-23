<template>
  <header>
    <!-- Top Bar -->
    <div class="w-full bg-[#EFEAFF] h-9"></div>

    <!-- Logo Section -->
    <a href="/">
      <div class="container mx-auto flex justify-center items-center py-4 bg-white">
        <img src="/logo.png" alt="logo" class="h-10"> <!-- Adjust height as needed -->
      </div>
    </a>
    <!-- Navigation -->
    <nav class="w-full bg-white shadow-sm flex justify-center py-3 text-sm font-medium"
         @mouseleave="closeMenu"
    >
      <ul class="flex gap-8 text-gray-700 uppercase tracking-wide">
        <!-- Dynamic Menu Items -->
        <li
            v-for="menu in menus"
            :key="menu.id"
            class="relative group"
        >
          <!-- Main Menu Link -->
          <a
              href="#"
              class="px-4 py-2 rounded-t-md bg-white group-hover:bg-[#EFEAFF] group-hover:shadow-md transition-all"
              @mouseover="toggleMenu(menu.name)"
          >
            {{ menu.name }}
          </a>

          <!-- Dropdown Menu -->
          <div
              v-if="activeMenu === menu.name && menu.subMenu && menu.subMenu.length > 0"
              class="absolute left-0 hidden group-hover:block bg-[#EFEAFF] w-[400px] p-6 shadow-lg z-50 top-6 transition-all"
          >
            <div v-for="sub in menu.subMenu" :key="sub.name" class="mb-4 flex items-center">
              <img :src="sub.image" alt="sub.name" class="w-10 h-10 mr-2 hidden md:inline rounded-full border-[#DCD1FF] border-4" />
              <!-- Submenu Section Title -->
              <h4 class="font-semibold text-gray-700">{{ sub.name }}</h4>
            </div>
          </div>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script setup>
import { useMenus } from "@/composables/useMenus"; // Adjust path if necessary

// Fetch menus from the useMenus hook
const { menus } = useMenus();

const activeMenu = ref(null);
let subMenuTimeout = null;


// Toggle main menu visibility
const toggleMenu = (menu) => {
  if (subMenuTimeout) {
    clearTimeout(subMenuTimeout);
    subMenuTimeout = null;
  }
  activeMenu.value = menu;
};

const closeMenu = () => {
  subMenuTimeout = setTimeout(() => {
    activeMenu.value = null;
  }, 300);};
</script>

<style scoped>
/* Additional styles for the active tab */
</style>
