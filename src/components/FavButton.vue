<template>
  <button
    class="btn btn-light"
    @click="$emit('clicked')"
    :class="{ active: isActive }"
  >
    👍🏾
  </button>
</template>
<script>
export default {
  props: {
    isActive: Boolean,
  },
};
</script>
<style scoped>
.active {
  background-color: salmon;
}
</style>
