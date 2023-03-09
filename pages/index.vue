<template>
  <div class="container mx-auto px-4 py-8">
    <h1 class="text-3xl font-bold mb-8">
      Boutique de <span class="capitalize">{{ merchant.data[0].name }}</span>
    </h1>

    <nav class="mb-8">
      <h3 class="text-lg font-bold mb-4">
        <n-link to="/categories">Catégories</n-link>
      </h3>
      <category-list :categories="categories"></category-list>

      <h3 class="text-lg font-bold mb-4">
        <n-link to="/products">Products</n-link>
      </h3>
      <product-list :products="products"></product-list>
    </nav>
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