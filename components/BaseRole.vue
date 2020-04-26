<template>
  <div class="experience__item">
    <div class="experience__info">
      <p>
        <strong>{{ type }}</strong>
        <br />
        {{ period }}
        <br />
        {{ total }}
      </p>
    </div>
    <div class="experience__detail">
      <h4 class="experience__detail-title">{{ title }}</h4>
      <p>{{ description }}</p>
      <base-tags :tags="parseTags" />
    </div>
  </div>
</template>

<script>
import BaseTags from '@/components/BaseTags'

export default {
  components: {
    BaseTags
  },
  props: {
    type: {
      type: String,
      required: true
    },
    period: {
      type: String,
      required: true
    },
    total: {
      type: String,
      default: ''
    },
    title: {
      type: String,
      required: true
    },
    description: {
      type: String,
      required: true
    },
    tags: {
      type: String,
      default: ''
    }
  },
  computed: {
    parseTags() {
      return this.tags.split(',').map((tag) => tag.trim())
    }
  }
}
</script>

<style lang="scss" scoped>
.experience {
  &__item {
    display: flex;
    flex-flow: row nowrap;
    margin-top: 20px;
  }

  &__info {
    width: 180px;
    padding-right: 60px;
    position: relative;

    &::before {
      content: '';
      width: 10px;
      height: 10px;
      position: absolute;
      background-color: white;
      border: $light-gray 2px solid;
      border-radius: 10px;
      left: 146px;
    }
  }

  &__detail {
    width: calc(100% - 180px);

    &-title {
      margin-bottom: 0.5rem;
      font-size: 1.2rem;
    }
  }
}
</style>
