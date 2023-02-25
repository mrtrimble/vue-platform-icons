<template>
  <svg xmlns="http://www.w3.org/2000/svg"
       xml:space="preserve"
       :class="{
         'pi-bold': weight == 'bold',
         'pi-2xs': size == '2xs',
         'pi-xs': size == 'xs',
         'pi-sm': size == 'sm',
         'pi-base': size == 'base',
         'pi-md': size == 'md',
         'pi-lg': size == 'lg',
         'pi-xl': size == 'xl',
         'pi-2xl': size == '2xl',
         'pi-3xl': size == '3xl',
       }"
       :viewBox="selected.viewBox">
    <title v-if="title">{{ title }}</title>
    <title v-else>{{ selected.name }} icon</title>
    <path v-for="(path, index) in selected.paths"
          :d="path"
          :key="index" />
  </svg>
</template>

<script setup>
import { computed } from 'vue';
import { icons } from '../assets/icons.json';

const props = defineProps({
  icon: {
    type: String,
    required: true,
    default: "platform-ui"
  },
  title: {
    type: String
  },
  weight: {
    type: String
  },
  color: {
    type: String,
    default: "currentColor"
  },
  size: {
    type: String
  }
})

const selected = computed(() => icons.filter(i => i.name == props.icon).at(0));
</script>

<style lang="scss" scoped>
:root {
  --step--2: clamp(0.78rem, calc(0.77rem + 0.03vw), 0.80rem);
  --step--1: clamp(0.94rem, calc(0.92rem + 0.11vw), 1.00rem);
  --step-0: clamp(1.13rem, calc(1.08rem + 0.22vw), 1.25rem);
  --step-1: clamp(1.35rem, calc(1.28rem + 0.37vw), 1.56rem);
  --step-2: clamp(1.62rem, calc(1.50rem + 0.58vw), 1.95rem);
  --step-3: clamp(1.94rem, calc(1.77rem + 0.87vw), 2.44rem);
  --step-4: clamp(2.33rem, calc(2.08rem + 1.25vw), 3.05rem);
  --step-5: clamp(2.80rem, calc(2.45rem + 1.77vw), 3.82rem);
}

$sizes: (
  '2xs': var(--size-2xs, var(--step--2)),
  'xs': var(--size-xs, var(--step--1)),
  'sm': var(--size-sm, var(--step-0)),
  'base': var(--size-base, var(--step-1)),
  'md': var(--size-md, var(--step-2)),
  'lg': var(--size-lg, var(--step-3)),
  'xl': var(--size-xl, var(--step-4)),
  '2xl': var(--size-2xl, var(--step-5)),
);

svg {
  display: inline-flex;
  height: var(--step-0);
  aspect-ratio: 1;
  overflow: visible;
  background: transparent;
  path {
    fill: v-bind(color);
  }
}

.pi-bold {
  path {
    stroke-width: 1rem;
    stroke: v-bind(color);
  }
}

@each $sizeName,
$size in $sizes {
  .pi-#{$sizeName} {
    height: $size;
  }
}
</style>