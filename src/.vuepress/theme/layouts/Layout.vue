<template>
  <div class="container">
    <!-- Header -->
    <header class="site-header">
      <div class="wrapper">
        <router-link to="/" class="logo">Aleks Petrov</router-link>
      </div>
    </header>
    <!-- Content -->
    <article>
      <Home v-if="$page.path === '/'"/>
      <Page v-else/>
    </article>
    <!-- Footer -->
    <footer class="site-footer">
      <div class="wrapper">
        <span>© Aleks Pertov, 2019</span>
        <a class="link" href="https://twitter.com/alekspetrovlive">Twitter</a>
      </div>
    </footer>
  </div>
</template>

<script>
import Home from "../components/pages/Home";
import Page from "../components/pages/Page";

export default {
  components: { Home, Page }
};
</script>


<style lang="scss">
@import "../styles/index";

.site-header {
  border-bottom: 1px solid var(--color-gray-80);
  padding: var(--space-md) 0;
}

.logo {
  display: inline-block;
  font-weight: 800;
  text-decoration: none;
  font-size: 1.25em;
  letter-spacing: -0.016em;
  vertical-align: baseline;
}

.site-footer {
  padding-top: var(--space-md);
  padding-bottom: var(--space-xl);
  border-top: 1px solid var(--color-gray-80);
  font-size: 14px;

  span {
    display: inline-block;
    color: var(--color-gray-60);
  }

  a {
    display: inline-block;
    text-decoration: none;
    margin-left: 16px;
    vertical-align: baseline;
  }
}
</style>