<script setup lang="ts">
import {computed, ref} from 'vue'

interface MenuElement {
  name: string;
  key: string;
  icon: string;
}

const elements = ref<MenuElement[]>([
  { name: 'Home', key: 'home', icon: 'home-outline' },
  { name: 'Profile', key: 'profile', icon: 'person-outline' },
  { name: 'Messages', key: 'messages', icon: 'chatbubble-outline' },
  { name: 'Settings', key: 'settings', icon: 'settings-outline' },
  { name: 'Gallery', key: 'gallery', icon: 'camera-outline' },
])

const active = ref<MenuElement>(elements.value[0]);
const activeIndex = computed<number>(() => elements.value.indexOf(active.value));
const setActive = ({ element }: { element: MenuElement }) => active.value = element;
</script>

<template>
  <div class="navigation">
    <ul class="navigation__list">
      <li
        v-for="element in elements"
        :key="element.key"

        class="navigation__list__item"
        :class="{ 'navigation__list__item--active': element.key === active.key }"

        @click="setActive({ element })"
      >
        <a
          href="#"
          class="navigation__list__item__link"
        >
          <span class="navigation__list__item__icon">
            <ion-icon :name='element.icon' />
          </span>
          <span class="navigation__list__item__text">{{ element.name }}</span>
        </a>
      </li>
      <div
        class="navigation__indicator"
        :style="`transform: translateX(calc(70px * ${ activeIndex }))`"
      />
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
  border-radius: 10px 10px 15px 15px;

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
        transition: .65s;
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

      &:nth-child(1) &--active ~.navigation__indicator {
        transform: translateX(calc(70px * 0));
      }
      &:nth-child(2) &--active ~.navigation__indicator {
        transform: translateX(calc(70px * 1));
        background-color: green !important;
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

    transition: .6s;

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
