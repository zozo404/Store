<template>
  <div class="container mx-auto px-4 py-8">
    <Return />
    <h1 class="text-3xl font-bold mb-8">Catégories</h1>
    <div
      class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 cursor-pointer"
    >
      <a
        v-for="category in categories"
        :key="category.id"
        :href="'/categories/' + category.slug"
      >
        <div
          class="category-card bg-white rounded-lg shadow-md overflow-hidden transition duration-300 ease-in-out transform hover:-translate-y-1 hover:scale-105"
        >
          <img
            v-if="category.imageUrl"
            class="h-64 bg-gray-300 w-full"
            :src="category.imageUrl"
            alt="Category image"
          />
          <div class="p-4">
            <h2 class="text-xl font-bold mb-2">{{ category.name }}</h2>
            <p class="text-gray-700">{{ category.description }}</p>
          </div>
        </div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $commerce }) {
    const { data: categories } = await $commerce.categories.list()

    // Pour chaque catégorie, récupérez l'URL de l'image s'il y en a une et stockez-la dans la propriété imageUrl.
    categories.forEach((category) => {
      const imageAsset = category.assets.find((asset) => asset.is_image)
      if (imageAsset) {
        category.imageUrl = imageAsset.url
      } else {
        category.imageUrl = null
      }
    })
    return {
      categories,
    }
  },
}
</script>
