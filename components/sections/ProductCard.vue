<template>
    <div class="group relative" :class="viewMode === 'list' ? 'flex w-full' : ''">
<!--      <NuxtLink-->
<!--          :to="{ name: 'product-product', params: { product: product.id } }"-->
<!--          :class="viewMode === 'list' ? 'flex items-center gap-4 p-4 border rounded-lg hover:shadow-md w-full' : ''"-->
<!--      >-->
      <!-- Product Image -->
        <div class="overflow-hidden relative">
          <img
              :src="product.image"
              alt="Product Image"
              :class="[
              'object-cover rounded-lg shadow-md transition-transform duration-300',
              viewMode === 'grid' ? 'w-full h-64 mb-4' : 'mr-5 h-32'
            ]"
              loading="lazy"
          />
        </div>

        <!-- Product Info -->
        <div class="text-start" :class="viewMode === 'list' ? 'flex-1' : ''">
          <h3
              class="mt-4 text-sm font-bold uppercase"
              :class="viewMode === 'list' ? 'mt-0' : ''"
          >
            {{ product.title }}
          </h3>
          <p class="text-sm font-bold">
            <span
                v-if="product.originalPrice"
                class="text-gray-400 ml-2 line-through"
            >
              {{ product.originalPrice }} USD
            </span>
            {{ product.price }} USD
          </p>
<!--        <p-->
<!--            v-if="showDescription"-->
<!--            class="text-sm text-gray-500"-->
<!--            :class="viewMode === 'list' ? 'mt-1' : ''"-->
<!--        >-->
<!--          {{ product.description }}-->
<!--        </p>-->
        </div>
<!--      </NuxtLink>-->

      <!-- Action Buttons -->
      <div
          class="absolute top-2 right-2 flex items-center opacity-0 group-hover:opacity-100 transition-opacity duration-300"
          :class="viewMode === 'list' ? 'flex-row' : 'flex-col'"
      >
        <button
            @click.stop="addToWishlist(product)"
            class="transparent p-2 rounded-full shadow-lg hover-icon"
        >
          <font-awesome-icon :icon="['fas', 'heart']" class="text-black"></font-awesome-icon>
        </button>

        <button
            @click.stop="addToBasket(product)"
            class="transparent p-2 rounded-full shadow-lg hover-icon"
        >
          <font-awesome-icon :icon="['fas', 'shopping-cart']"></font-awesome-icon>
        </button>

        <button
            @click.stop="openQuickView(product)"
            class="transparent p-2 rounded-full shadow-lg hover-icon"
        >
          <font-awesome-icon :icon="['fas', 'eye']"></font-awesome-icon>
        </button>

        <button
            @click.stop="addToComparison(product)"
            class="transparent p-2 rounded-full shadow-lg hover-icon"
        >
          <font-awesome-icon :icon="['fas', 'arrow-right-arrow-left']" />
        </button>
      </div>
    </div>

    <!-- Quick View Modal -->
<!--    <QuickViewModal-->
<!--        v-if="showQuickView"-->
<!--        :item="selectedItem"-->
<!--        @close="closeQuickView"-->
<!--    />-->
</template>

<script setup>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { useCart } from "~/composables/useCart.js";

defineProps({
  product: {
    type: Object,
    required: true,
  },
  showDescription: {
    type: Boolean,
    default: true,
  },
  viewMode: {
    type: String,
    default: "grid",
  },
});

let showQuickView = ref(false);
let selectedItem = ref(null);

const openQuickView = (product) => {
  if (product) {
    selectedItem.value = product;
    showQuickView.value = true;
  } else {
    console.error("Attempted to open Quick View with an undefined product.");
  }
};


const closeQuickView = () => {
  showQuickView.value = false;
  selectedItem.value = null;
};

// Wishlist and Basket Functions
const addToWishlist = (product) => {
  console.log("Added to wishlist:", product);
};
const addToComparison = (product) => {
  console.log("Added to comparison list:", product);
};

const { addItem } = useCart();
const addToBasket = (product) => {
  addItem({ ...product, image: product.image });
};
</script>

<style scoped>
.group:hover .group-hover {
  opacity: 1;
  z-index: 9;
}

.hover-icon:hover i.fa-heart {
  color: red;
}

.hover-icon:hover i.fa-shopping-cart {
  color: #226dfb;
}

.hover-icon:hover i.fa-eye {
  color: gray;
}

/* Zoom Effect */
.group img {
  transform: scale(1);
}

.group:hover img {
  transform: scale(1.1);
}
</style>
