<template>
  <header>
    <h1>
      <PlatformIcon icon="platform-ui"
                    size="2xl"
                    title="Platform Icons"
                    color="hsl(256deg, 46%, 25%)" />
    </h1>
  </header>
  <main>
    <section>
      <h2>Icons</h2>
      <p>
        Icons can be included with the <code>&lt;PlatformIcon /&gt;</code> component and
        passing in the name of the icon through the <code>icon</code> prop, such as:
      </p>
      <pre><code>&lt;PlatformIcon icon="rocket" /&gt;</code></pre>

      <div class="grid">
        <div class="icon-card"
             v-for="icon in iconList"
             :key="icon">
          <PlatformIcon :icon="icon"
                        size="xl" />
          <span>
            <pre>{{ icon }}</pre>
          </span>
        </div>
      </div>
    </section>
    <section>
      <h2>Sizes</h2>
      <p>
        By default, icons will be the size of relative text. Icons can be resized by passing in a size to the <code>size</code> prop:
      </p>
      <pre><code>&lt;PlatformIcon icon="rocket" size="xl" /&gt;</code></pre>
      <div class="grid">
        <div class="icon-card"
             v-for="size in sizes">
          <PlatformIcon icon="platform-ui"
                        :size="size" />
          <span>
            <pre>{{ size }}</pre>
          </span>
        </div>
      </div>
    </section>
    <section>
      <h2>Colors</h2>
      <p>
        By default, icons will be set to the current text color, however colors can be changed by passing colors or CSS
        custom properties into the <code>color</code> prop. CSS classes can also be added to the
        <code>&lt;PlatformIcon /&gt;</code> component.
      </p>
      <pre><code>&lt;PlatformIcon icon="rocket" color="red" /&gt;</code></pre>
      <div class="grid">
        <div class="icon-card">
          <PlatformIcon icon="platform-ui"
                        size="2xl"
                        color="red" />
          <span>
            <pre>red</pre>
          </span>
        </div>
        <div class="icon-card">
          <PlatformIcon icon="platform-ui"
                        size="2xl"
                        color="var(--green)" />
          <span>
            <pre>var(--green)</pre>
          </span>
        </div>
        <div class="icon-card">
          <PlatformIcon icon="platform-ui"
                        size="2xl"
                        color="#0000FF" />
          <span>
            <pre>#0000FF</pre>
          </span>
        </div>

        <div class="icon-card">
          <PlatformIcon icon="platform-ui"
                        size="2xl"
                        class="rebecca-purple" />
          <span>
            <pre>.rebecca-purple</pre>
          </span>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup>
import { computed, ref } from 'vue';
import { icons } from './assets/icons.json';
import PlatformIcon from './components/PlatformIcon.vue';

const iconList = computed(() => icons.map(i => (i.name)));

const sizes = ref(['2xs', 'xs', 'sm', 'base', 'md', 'lg', 'xl', '2xl'])
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Figtree&display=swap');

:root {
  --platformui-purple: hsl(256deg, 46%, 25%);
  --green: green;
  --step--2: clamp(0.78rem, calc(0.77rem + 0.03vw), 0.80rem);
  --step--1: clamp(0.94rem, calc(0.92rem + 0.11vw), 1.00rem);
  --step-0: clamp(1.13rem, calc(1.08rem + 0.22vw), 1.25rem);
  --step-1: clamp(1.35rem, calc(1.28rem + 0.37vw), 1.56rem);
  --step-2: clamp(1.62rem, calc(1.50rem + 0.58vw), 1.95rem);
  --step-3: clamp(1.94rem, calc(1.77rem + 0.87vw), 2.44rem);
  --step-4: clamp(2.33rem, calc(2.08rem + 1.25vw), 3.05rem);
  --step-5: clamp(2.80rem, calc(2.45rem + 1.77vw), 3.82rem);
}


.rebecca-purple {
  color: rebeccapurple;
}

html {
  font-size: 18px;
}

body {
  box-sizing: border-box;
  font-size: var(--step-0);
  background: #f5f4f8;
  font-family: 'Figtree', sans-serif;
  color: #333;
  padding-block: 1.5rem;
}

header {
  display: flex;
  justify-content: center;
  align-items: center;

  h1 {
    font-size: var(--step-3);
    margin: 0;
  }

}

main {
  width: min(100% - 3rem, var(--container-max, 60ch));
  margin-inline: auto;

  >* {
    margin: 0;
  }

  >*+* {
    margin-block-start: 1.5rem;
  }

  h2 {
    color: var(--platformui-purple);
    font-size: var(--step-2);
    margin: 0;
  }

  code {
    background: var(--platformui-purple);
    color: white;
  }

  pre {
    padding-block: 0.5rem;

    code {
      padding: 0.5rem;
    }
  }

  p {
    line-height: 1.6;
  }

  section {
    >* {
      margin: 0;
    }

    >*+* {
      margin-block-start: 1rem;
    }
  }
}

.grid {
  --min: 12ch;
  --gap: 1rem;

  display: grid;
  grid-gap: var(--gap);
  grid-template-columns: repeat(auto-fit, minmax(min(100%, var(--min)), 1fr));

  &:hover {
    &:has(.icon-card) .icon-card:not(:hover) {
      transform: scale(0.90);
    }
  }
}

.icon-card {
  display: grid;
  place-content: center;
  background: white;
  border-radius: 0.5em;
  aspect-ratio: 1;
  gap: 0.5em;
  transition: 0.2s ease;
  overflow: hidden;

  >* {
    margin-inline: auto;
  }

  span {
    font-size: var(--step--1);

    pre {
      margin: 0;
    }
  }
}
</style>