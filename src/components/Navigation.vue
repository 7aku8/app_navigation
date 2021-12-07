<script setup lang="ts">
import { ref } from 'vue'

// defineProps<{ msg: string }>()

const count = ref(0)
</script>

<template>
  <div class="navigation">
    <ul class="navigation__list">
      <li class="navigation__list__item navigation__list__item--active">
        <a
          href="#"
          class="navigation__list__item__link"
        >
          <span class="navigation__list__item__icon">
            <ion-icon name="home-outline" />
          </span>
          <span class="navigation__list__item__text">Home</span>
        </a>
      </li>
      <li class="navigation__list__item">
        <a
          href="#"
          class="navigation__list__item__link"
        >
          <span class="navigation__list__item__icon">
            <ion-icon name="person-outline" />
          </span>
          <span class="navigation__list__item__text">Profile</span>
        </a>
      </li>
      <li class="navigation__list__item">
        <a
          href="#"
          class="navigation__list__item__link"
        >
          <span class="navigation__list__item__icon">
            <ion-icon name="chatbubble-outline" />
          </span>
          <span class="navigation__list__item__text">Messages</span>
        </a>
      </li>
      <li class="navigation__list__item">
        <a
          href="#"
          class="navigation__list__item__link"
        >
          <span class="navigation__list__item__icon">
            <ion-icon name="settings-outline" />
          </span>
          <span class="navigation__list__item__text">Settings</span>
        </a>
      </li>
      <li class="navigation__list__item">
        <a
          href="#"
          class="navigation__list__item__link"
        >
            <span class="navigation__list__item__icon">
            <ion-icon name="camera-outline" />
          </span>
          <span class="navigation__list__item__text">Gallery</span>
        </a>
      </li>
      <div
        class="navigation__indicator"
      ></div>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
.navigation {
  position: relative;
  width: 100%;
  height: 70px;
  background-color: var(--nav-bg);

  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 10px;

  &__list {
    width: 350px;
    display: flex;

    &__item {
      position: relative;
      list-style: none;
      width: 70px;
      height: 70px;
      z-index: 1;

      &--active &__icon {
        transform: translateY(-35px);
      }

      &--active &__text {
        opacity: 1;
        transform: translateY(10px);
      }

      &__link {
        position: relative;
        display: flex;

        justify-content: center;
        align-items: center;
        flex-direction: column;
        width: 100%;

        text-align: center;
        font-weight: 500;
      }

      &__icon {
        position: relative;
        display: block;
        line-height: 75px;
        font-size: 1.5em;
        text-align: center;
        transition: .3s;
        color: var(--icon-color);
      }

      &__text {
        position: absolute;
        color: var(--text-color);

        font-weight: 400;
        font-size: .75em;
        letter-spacing: 0.05em;

        transition: .3s;

        opacity: 0;
        transform: translateY(20px);
      }
    }
  }
}
</style>
