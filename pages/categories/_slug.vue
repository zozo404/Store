<!-- eslint-disable vue/no-v-html -->
<template>
  <div class="container mx-auto px-4 py-8">
    <Return />
    <h1>Tous les jeux de la catégorie {{ category.name }}:</h1>
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
      <div v-for="(product, index) in products" :key="index">
        <nuxt-link :to="`/products/${product.permalink}`">
          <div class="category-card bg-white rounded-lg shadow-md overflow-hidden transition duration-300 ease-in-out transform hover:-translate-y-1 hover:scale-105">
            <img :src="product.image.url" :alt="product.name" class="w-full h-64 object-cover">
            <div class="p-4">
              <h2 class="font-bold text-lg mb-2">{{ product.name }}</h2>
              <p class="text-gray-700 text-base mb-2">{{ product.price.formatted }} €</p>
              <div class="text-gray-700 text-base mb-2" v-html="product.description"></div>
            </div>
          </div>
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  async asyncData({ params, $commerce }) {
    const { slug } = params;

    const category = await $commerce.categories.retrieve(slug, {
      type: "slug",
    });
    const { data: products } = await $commerce.products.list({
      category_slug: slug,
    });

    return {
      category,
      products,
    };
  },
};
</script>
