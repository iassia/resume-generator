<template>
  <ul class="tag">
    <li v-for="tag in tags" :key="tag" class="tag__item">{{ tag }}</li>
  </ul>
</template>

<script>
export default {
  props: {
    tags: {
      type: Array,
      default: () => []
    }
  }
}
</script>

<style lang="scss" scoped>
.tag {
  display: inline-block;
  padding: 0;
  list-style: none;

  &__item {
    padding: 4px 10px;
    border-radius: 20px;
    background-color: $light-gray;
    display: inline-block;
    margin: 2px 4px 0 0;
    font-size: 0.8rem;
  }
}
</style>
