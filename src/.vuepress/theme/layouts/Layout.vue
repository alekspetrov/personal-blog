<template>
  <div class="container">
    <!-- Header -->
    <header class="site-header">
      <div class="wrapper">
        <router-link to="/" class="logo">
          <span class="logo__sign">A</span>
          <span class="logo__text">Aleks Petrov</span>
        </router-link>
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
  components: { Home, Article }
};
</script>


<style lang="scss">
@import "../styles/index";

.site-header {
  padding: var(--space-md) 0;
  margin-bottom: var(--space-md);
}

.logo {
  &__sign {
    display: inline-block;
    width: 40px;
    border-radius: 50%;
    text-align: center;
    line-height: 40px;
    font-weight: 800;
    font-size: 18px;
    background: var(--color-secondary);
    color: var(--color-primary);
    margin-right: var(--space-xs);
  }

  &__text {
    font-family: var(--font-accident);
    font-weight: 700;
    font-size: 20px;
  }
}

.site-footer {
  padding-top: calc(var(--space-lg) * 3);
  padding-bottom: var(--space-xl);

  a {
    margin-right: var(--space-md);
  }
}
</style>