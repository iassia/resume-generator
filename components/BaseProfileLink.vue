<template>
  <a class="profile__link" :href="link">
    <i :class="icon"></i>
    {{ value }}
  </a>
</template>

<script>
const CONFIG = {
  phone: {
    prefix: 'tel:',
    icon: 'mobile-phone'
  },
  email: {
    prefix: 'mailto:',
    icon: 'envelope-o'
  },
  github: {
    prefix: 'https://github.com/',
    icon: 'github'
  }
}

export default {
  props: {
    type: {
      type: String,
      required: true
    },
    value: {
      type: [String, Number],
      required: true
    }
  },
  computed: {
    link() {
      return `${CONFIG[this.type].prefix}${this.value}`
    },
    icon() {
      return `fa fa-${CONFIG[this.type].icon}`
    }
  }
}
</script>

<style lang="scss" scoped>
.profile {
  &__link {
    text-decoration: none;
    color: $main-color;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    padding: 1rem 1rem 1rem 0;
    margin-right: 1rem;

    .fa {
      display: inline-block;
      width: 20px;
      height: 20px;
      border-radius: 20px;
      line-height: 20px;
      margin-right: 0.5rem;
      text-align: center;
      background-color: $light-gray;
    }
  }
}
</style>
