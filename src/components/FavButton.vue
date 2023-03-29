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
.fav-button {
  width: 20 px;
  height: 20px;
  border: 3px solid transparent;
  border-radius: 3px;
  padding: 5px;
  cursor: pointer;
}
.active {
  background-color: salmon;
}
</style>
