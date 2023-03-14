<!-- eslint-disable vue/no-v-html -->
<template>
  <div class="container mx-auto px-4 py-8">
    <Return />
    <h1 class="text-3xl font-bold mb-8">Products</h1>
    <div
      class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 cursor-pointer"
    >
      <nuxt-link
        v-for="product in products"
        :key="product.id"
        :to="`/products/${product.permalink}`"
      >
        <div
          class="product-card bg-white rounded-lg shadow-md overflow-hidden transition duration-300 ease-in-out transform hover:-translate-y-1 hover:scale-105"
        >
            <img
              class="w-full h-64 object-cover"
              :src="product.image.url"
              :alt="'image ' + product.name"
            />
          <div class="p-4">
            <h2 class="text-xl font-bold mb-2">{{ product.name }}</h2>
            <div v-html="product.description"></div>
          </div>
        </div>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $commerce }) {
    const { data: products } = await $commerce.products.list()
    return {
      products,
    }
  },
}
</script>