<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <button class="pl-2 py-3 flex gap-1" @click="goBack">
    <svg class="w-5" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512">
      <path d="M9.4 233.4c-12.5 12.5-12.5 32.8 0 45.3l160 160c12.5 12.5 32.8 12.5 45.3 0s12.5-32.8 0-45.3L109.2 288 416 288c17.7 0 32-14.3 32-32s-14.3-32-32-32l-306.7 0L214.6 118.6c12.5-12.5 12.5-32.8 0-45.3s-32.8-12.5-45.3 0l-160 160z"/>
    </svg>
    Retour
  </button>
</template>

<script>
export default {
  methods: {
    goBack() {
      this.$router.go(-1);
    }
  }
};
</script>