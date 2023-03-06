<template>
  <div>
    <!-- add product's image -->
    <p>{{ product.name }}: {{ product.price.formatted_with_symbol }}</p>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/require-prop-types
  props: ['product'],
}
</script>