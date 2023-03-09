<template>
  <div>
    <!-- add product's image -->
    <p>{{ product.name }}: {{ product.price.formatted}} €</p>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/require-prop-types
  props: ['product'],
}
</script>