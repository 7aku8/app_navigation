<script setup lang="ts">
import {computed, ref} from 'vue'

const active = ref<string>('home');
const setActive = ({ name }: { name: string}) => active.value = name;

const homeActive = computed<boolean>(() => active.value === 'home');
const profileActive = computed<boolean>(() => active.value === 'profile');
const messagesActive = computed<boolean>(() => active.value === 'messages');
const settingsActive = computed<boolean>(() => active.value === 'settings');
const galleryActive = computed<boolean>(() => active.value === 'gallery');
</script>

<template>
  <div class="navigation">
    <ul class="navigation__list">
      <li
        class="navigation__list__item"
        :class="{ 'navigation__list__item--active': homeActive }"

        @click="setActive({ name: 'home' })"
      >
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
      <li
        class="navigation__list__item"
        :class="{ 'navigation__list__item--active': profileActive }"

        @click="setActive({ name: 'profile' })"
      >
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
      <li
        class="navigation__list__item"
        :class="{ 'navigation__list__item--active': messagesActive }"

        @click="setActive({ name: 'messages' })"
      >
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
      <li
        class="navigation__list__item"
        :class="{ 'navigation__list__item--active': settingsActive }"

        @click="setActive({ name: 'settings' })"
      >
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
      <li
        class="navigation__list__item"
        :class="{ 'navigation__list__item--active': galleryActive }"

        @click="setActive({ name: 'gallery' })"
      >
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
  border-radius: 15px;

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

  &__indicator {
    position: absolute;
    top: -55%;
    width: 70px;
    height: 70px;

    background-color: var(--active-bg);
    border-radius: 50%;
    border: 6px solid var(--active-border);

    transition: .3s;

    &::before {
      content: '';
      position: absolute;
      width: 20px;
      height: 20px;

      top: 55%;
      left: -20px;
      background-color: transparent;
      border-top-right-radius: 20px;

      box-shadow: 0 -10px 0 0 var(--bg-color);
    }
    &::after {
      content: '';
      position: absolute;
      width: 20px;
      height: 20px;

      top: 55%;
      right: -20px;
      background-color: transparent;
      border-top-left-radius: 20px;

      box-shadow: 0 -10px 0 0 var(--bg-color);
    }
  }
}
</style>
