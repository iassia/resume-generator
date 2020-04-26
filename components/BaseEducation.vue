<template>
  <div>
    <h3>{{ name }}</h3>
    <p>
      <strong>{{ course }}</strong>
    </p>
    <p>{{ period }}</p>
  </div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true
    },
    course: {
      type: String,
      default: ''
    },
    period: {
      type: String,
      default: ''
    }
  }
}
</script>
