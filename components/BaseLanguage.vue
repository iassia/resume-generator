<template>
  <p>
    <strong>{{ name }}</strong>
    - {{ level }}
  </p>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true
    },
    level: {
      type: String,
      default: ''
    }
  }
}
</script>
