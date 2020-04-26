<template>
  <div class="container">
    <div>
      <div class="profile">
        <h1 class="profile__title">{{ profile.name }}</h1>
        <p class="profile__role">{{ profile.title }}</p>
        <a class="profile__link" :href="`mailto:${profile.email}`">
          <i class="fa fa-envelope-o"></i>
          {{ profile.email }}
        </a>
        <a class="profile__link" :href="`tel:${profile.phone}`">
          <i class="fa fa-mobile-phone"></i>
          +{{ profile.phone }}
        </a>
        <a
          class="profile__link"
          :href="`https://github.com/${profile.github}`"
          target="_blank"
        >
          <i class="fa fa-github"></i>
          github.com/{{ profile.github }}
        </a>
      </div>

      <div
        v-for="experience in experiences"
        :key="experience.company"
        class="experience"
      >
        <div class="experience__box">
          <h3>{{ experience.company }}</h3>

          <div class="experience__group">
            <div
              v-for="role in experience.roles"
              :key="role.title"
              class="experience__item"
            >
              <div class="experience__info">
                <p>
                  <strong>{{ role.type }}</strong>
                  <br />
                  {{ role.period }}
                  <br />
                  {{ role.total }}
                </p>
              </div>
              <div class="experience__detail">
                <h4>{{ role.title }}</h4>
                <p>{{ role.description }}</p>
                <ul class="tag">
                  <li v-for="tag in role.tags.split(',')" :key="tag">
                    {{ tag.trim() }}
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="extra">
        <div class="extra__box">
          <h2>Education</h2>
          <h3>{{ education.name }}</h3>
          <p>
            <strong>{{ education.course }}</strong>
          </p>
          <p class="period">{{ education.period }}</p>
        </div>
        <div class="extra__box">
          <h2>Languages</h2>
          <p v-for="language in languages" :key="language.name">
            <strong>{{ language.name }}</strong>
            - {{ language.level }}
          </p>
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

export default {
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

<style lang="scss">
@media only screen {
  .container {
    padding: 2%;
  }
}

.tag {
  display: inline-block;
  padding: 0;
  list-style: none;

  li {
    padding: 4px 10px;
    border-radius: 20px;
    background-color: $light-gray;
    display: inline-block;
    margin: 2px 4px 0 0;
    font-size: 0.8rem;
  }
}

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
      border-radius: 10px;
      text-align: center;
      line-height: 20px;
      margin-right: 5px;
      background-color: $light-gray;
    }
  }

  &__role {
    text-transform: uppercase;
  }
}

.extra {
  padding-top: 4rem;
  margin-top: 4rem;
  border-top: $light-gray 1px solid;
  display: flex;
  flex-flow: row nowrap;

  &__box {
    width: 50%;
    padding-right: 60px;
  }

  h2 {
    margin-bottom: 1rem;
  }
}

.experience {
  h3 {
    margin-top: 2rem;
    font-size: 1.4rem;
  }

  p {
    margin-bottom: 0.5rem;
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

    h4 {
      margin-bottom: 0.5rem;
      font-size: 1.2rem;
    }
  }
}
</style>
