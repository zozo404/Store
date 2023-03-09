<template>
  <p>{{ category.name }}</p>
</template>

<script>
export default {
  // eslint-disable-next-line vue/require-prop-types
  props: ["category"],
};
</script>