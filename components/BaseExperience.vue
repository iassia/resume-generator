<template>
  <div class="experience">
    <h3 class="experience_title">{{ company }}</h3>

    <div class="experience__group">
      <base-role v-for="role in roles" :key="role.title" v-bind="role" />
    </div>
  </div>
</template>

<script>
import BaseRole from '@/components/BaseRole'

export default {
  components: {
    BaseRole
  },
  props: {
    company: {
      type: String,
      required: true
    },
    roles: {
      type: Array,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
.experience {
  &__title {
    margin-top: 2rem;
    font-size: 1.4rem;
  }

  &__group {
    position: relative;
    &::before {
      content: '';
      width: 2px;
      height: 100%;
      position: absolute;
      left: 150px;
      top: 0;
      background-color: $light-gray;
    }
  }
}
</style>
