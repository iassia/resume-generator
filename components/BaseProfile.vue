<template>
  <div class="profile">
    <h1 class="profile__title">{{ name }}</h1>
    <p class="profile__role">{{ title }}</p>
    <base-profile-link :value="email" type="email" />
    <base-profile-link :value="phone" type="phone" />
    <base-profile-link :value="github" type="github" />
  </div>
</template>

<script>
import BaseProfileLink from '@/components/BaseProfileLink'

export default {
  components: {
    BaseProfileLink
  },
  props: {
    name: {
      type: String,
      required: true
    },
    title: {
      type: String,
      default: ''
    },
    phone: {
      type: Number,
      default: 0
    },
    email: {
      type: String,
      required: true,
      validator(email) {
        const isEmail = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
        return isEmail.test(String(email).toLowerCase())
      }
    },
    github: {
      type: String,
      default: ''
    }
  }
}
</script>

<style lang="scss" scoped>
.profile {
  &__role {
    text-transform: uppercase;
  }
}
</style>
