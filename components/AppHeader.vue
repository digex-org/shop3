<template>
  <header>
    <!-- Top Bar -->
    <div class="w-full bg-[#EFEAFF] h-9"></div>

    <!-- Logo Section -->
    <div class="bg-white">
      <div class="container mx-auto flex justify-between items-center py-4 md:justify-center px-2">
        <!-- Logo -->
        <a href="/">
          <img src="/logo.png" alt="logo" class="h-10">
        </a>
        <!-- Mobile Menu Button -->
        <button
            class="block md:hidden text-gray-700 text-2xl"
            @click="toggleMobileMenu"
        >
          <font-awesome-icon :icon="['fas', isMobileMenuOpen ? 'times' : 'bars']" />
        </button>
      </div>
    </div>

    <!-- Navigation -->
    <nav
        class="w-full bg-white shadow-sm md:flex justify-center py-3 text-sm font-medium"
        :class="isMobileMenuOpen ? 'block' : 'hidden md:flex'"
    >
      <ul class="flex flex-col md:flex-row gap-4 text-gray-700 uppercase tracking-wide">
        <!-- Dynamic Menu Items -->
        <li
            v-for="menu in menus"
            :key="menu.id"
            class="relative group"
        >
          <!-- Main Menu Link -->
          <a
              href="#"
              class="px-4 py-2 rounded-md bg-white group-hover:bg-[#EFEAFF] group-hover:shadow-md transition-all"
              @mouseover="toggleMenu(menu.name)"
          >
            {{ menu.name }}
          </a>

          <!-- Dropdown Menu -->
          <div
              v-if="activeMenu === menu.name && menu.subMenu && menu.subMenu.length > 0"
              class="absolute left-0 hidden group-hover:block bg-[#EFEAFF] w-[300px] p-4 shadow-lg z-50 top-full transition-all"
          >
            <div
                v-for="sub in menu.subMenu"
                :key="sub.name"
                class="mb-2 flex items-center"
            >
              <img
                  :src="sub.image"
                  alt="sub.name"
                  class="w-8 h-8 mr-2 hidden md:inline rounded-full border-[#DCD1FF] border-2"
              />
              <h4 class="font-semibold text-gray-700">{{ sub.name }}</h4>
            </div>
          </div>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script setup>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { useMenus } from "@/composables/useMenus"; // Adjust path if necessary

// Fetch menus from the useMenus hook
const { menus } = useMenus();

const activeMenu = ref(null);
const isMobileMenuOpen = ref(false);
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
  }, 300);
};

// Mobile Menu Toggle
const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value;
};
</script>

<style scoped>
/* Add transition effect to dropdown menus */
nav {
  transition: max-height 0.3s ease-in-out;
}

/* Ensure dropdowns are smooth and clean */
nav ul li .group-hover > div {
  transition: opacity 0.3s ease, transform 0.3s ease;
}
</style>
