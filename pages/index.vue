<template>
  <div>
    <h1>
      Boutique de <span class="capitalize">{{ merchant.data[0].name }}</span>
    </h1>

    <!-- faire style liste de navigation + optimiser faire boucle (voir cv zozoy) -->
    <h3 class="text-lg font-bold">
      <n-link to="/categories">Categories</n-link>
    </h3>
    <category-list :categories="categories"></category-list>

    <h3 class="text-lg font-bold">
      <n-link to="/products">Products</n-link>
    </h3>
    <product-list :products="products"></product-list>
  </div>
</template>

<script>
export default {
  async asyncData({ $commerce }) {
    const merchant = await $commerce.merchants.about()
    const { data: categories } = await $commerce.categories.list()
    const { data: products } = await $commerce.products.list()

    return {
      merchant,
      categories,
      products,
    }
  },
}
</script>