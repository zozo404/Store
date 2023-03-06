<template>
  <div>
    <h1>{{ product.name }}</h1>
    <img class="w-2/5" :src="product.image.url" :alt="'img '+ product.name">
    <p>{{ product.price.formatted }} €</p>
  </div>
</template>

<script>


export default {
  async asyncData({ params,$commerce }) {
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