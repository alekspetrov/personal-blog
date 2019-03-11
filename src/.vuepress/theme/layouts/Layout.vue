<template>
  <div class="container">
    <!-- Header -->
    <header class="site-header">
      <div class="wrapper">
        <router-link to="/" class="logo">
          <svg width="84" height="38" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path
              d="M5.68299 0v10.8647H17.3585c1.3129 0 2.3773 1.0416 2.3773 2.3265v15.5027h14.3396V14.7347C34.0754 6.59695 27.3344 0 19.0188 0H5.68299zM37.633 0v38h14.1716V0H37.633z"
              fill="#F5F4F4"
            ></path>
            <path
              d="M17.434 21.7143c0 4.7113-3.9028 8.5306-8.71702 8.5306C3.90272 30.2449 0 26.4256 0 21.7143s3.90272-8.5306 8.71698-8.5306c4.81422 0 8.71702 3.8193 8.71702 8.5306zM68.9434 29.4694C77.2589 29.4694 84 22.8724 84 14.7347 84 6.59695 77.2589 0 68.9434 0S53.8868 6.59695 53.8868 14.7347c0 8.1377 6.7411 14.7347 15.0566 14.7347z"
              fill="#F5F4F4"
            ></path>
          </svg>
        </router-link>
        <button
          @click="switchTheme"
          class="switcher"
          :class="theme === 'dark' ? '' : 'switcher--light' "
        >
          <svg width="46" height="31" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path
              fill-rule="evenodd"
              clip-rule="evenodd"
              d="M46 31V5.03089h-1.614v0H23.68L10.2218.25435s-.0004-.000136-.53759 1.5304l.53759-1.5304L9.50512-1e-7-.0000023 5.735-.0000012 31H46zM8.07017 4.6514l-4.8421 2.92153V25.9999l4.8421-3.8953V4.6514zm3.22803 17.2032V4.0788l10.4913 3.72351V26.8193l-10.4913-4.9647zm13.7193 5.8993V8.27703h17.7544V27.7539H25.0175z"
              fill="#F5F4F4"
            ></path>
          </svg>
        </button>
      </div>
    </header>
    <!-- Content -->
    <article>
      <Home v-if="$page.path === '/'"/>
      <Article v-else/>
    </article>
    <!-- Footer -->
    <footer class="site-footer">
      <div class="wrapper">
        <a class="link" href="https://twitter.com/alekspetrovlive">Twitter</a>
        <a class="link" href="https://github.com/alekspetrov">Github</a>
        <a class="link" href="https://linkedin.com/in/alekspetrov/">LinkedIn</a>
      </div>
    </footer>
  </div>
</template>

<script>
import Home from "../components/pages/Home";
import Article from "../components/pages/Article";

export default {
  components: { Home, Article },
  data() {
    return {
      theme: localStorage.currentTheme || "light"
    };
  },
  mounted() {
    if (this.theme === "dark") document.body.dataset.theme = "dark";
  },
  methods: {
    switchTheme() {
      const el = document.body;

      if (this.theme !== "dark") {
        this.theme = "dark";
        el.dataset.theme = "dark";
        localStorage.setItem("currentTheme", "dark");
      } else {
        this.theme = "light";
        el.dataset.theme = "light";
        localStorage.removeItem("currentTheme");
      }
    }
  }
};
</script>


<style lang="scss">
@import "../styles/index";

.site-header {
  padding: var(--space-md) 0;
  margin-bottom: var(--space-md);
  margin-top: var(--space-md);
}

.logo {
  path {
    fill: var(--color-secondary);
  }

  &--light {
    path {
      fill: var(--color-primary);
    }
  }
}

.site-footer {
  padding-top: calc(var(--space-lg) * 3);
  padding-bottom: var(--space-xl);

  a {
    margin-right: var(--space-md);
  }
}

.switcher {
  position: fixed;
  right: 30px;
  top: 30px;

  path {
    fill: var(--color-secondary);
  }

  &--light {
    fill: var(--color-primary);
    transform: scaleX(-1);
  }
}
</style>