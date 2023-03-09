<!-- eslint-disable vue/no-v-html -->
<template>
  <div class="container mx-auto px-4 py-8">
    <Return />
    <h1>{{ product.name }}</h1>
    <img class="w-2/5" :src="product.image.url" :alt="'img '+ product.name">
    <p>{{ product.price.formatted }} €</p>
    <div v-html="product.description"></div>
    <p>Catégories :
      <span v-for="(category, index) in product.categories" :key="index">
        {{ category.name }}
        <span v-if="index !== product.categories.length - 1">,</span>
      </span>
    </p>
  </div>
</template>

<script>


export default {
  async asyncData({ params, $commerce }) {
    const { permalink } = params

    const product = await $commerce.products.retrieve(permalink, {
      type: 'permalink',
    })

    return {
      product,
    }
  },
}
</script>