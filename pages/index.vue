<template>
  <div class="container">
    <div>
      <base-profile v-bind="profile" />
      <base-experience
        v-for="experience in experiences"
        :key="experience.company"
        class="experience"
        v-bind="experience"
      />
      <div class="info">
        <div class="info__box">
          <h2 class="info__title">Education</h2>
          <base-education
            v-for="item in education"
            :key="item.name"
            v-bind="item"
          />
        </div>
        <div class="info__box">
          <h2 class="info__title">Languages</h2>
          <base-language
            v-for="language in languages"
            :key="language.name"
            v-bind="language"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import {
  profile,
  education,
  experiences,
  languages
} from '@/content/resume.yaml'

import BaseProfile from '@/components/BaseProfile'
import BaseExperience from '@/components/BaseExperience'
import BaseEducation from '@/components/BaseEducation'
import BaseLanguage from '@/components/BaseLanguage'

export default {
  components: {
    BaseProfile,
    BaseExperience,
    BaseEducation,
    BaseLanguage
  },
  data() {
    return {
      profile,
      education,
      experiences,
      languages
    }
  }
}
</script>

<style lang="scss" scoped>
@media only screen {
  .container {
    padding: 2%;
  }
}

.info {
  padding-top: 4rem;
  margin-top: 4rem;
  border-top: $light-gray 1px solid;
  display: flex;
  flex-flow: row nowrap;

  &__box {
    width: 50%;
    padding-right: 60px;
  }

  &__title {
    margin-bottom: 1rem;
  }
}
</style>
