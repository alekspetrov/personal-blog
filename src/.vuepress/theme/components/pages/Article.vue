<template>
  <div class="page-layout page">
    <div class="wrapper">
      <div class="page">
        <div class="page__header">
          <h1>{{ $page.frontmatter.title }}</h1>
          <p>{{ $page.frontmatter.lead }}</p>
          <div class="post-data">
            <time :datetime="$page.frontmatter.date">{{ date($page.frontmatter.date) }}</time>
            <span>&nbsp;•&nbsp;</span>
            <span>{{ $page.frontmatter.category }}</span>
          </div>
        </div>
        <div v-if="$page.frontmatter.template==='article'" class="article-template">
          <Content/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import dateFormat from "../../utils/dateFormat.js";

export default {
  name: "Page",
  methods: {
    date(date) {
      return dateFormat(date);
    }
  }
};
</script>


<style lang="scss">
@import "../../styles/breakpoints";

.page {
  margin-bottom: var(--space-3xl);

  &__header {
    margin-bottom: var(--space-xl);

    @include breakpoint(mobile) {
      margin-bottom: calc(var(--space-xl) * 1.5);
    }

    h1 {
      margin-bottom: var(--space-lg);
      font-size: var(--title-h2);
    }

    p {
      font-size: var(--text-md);
      margin-bottom: var(--space-lg);
      color: var(--color-gray-80);
    }
  }
}

.follow-link {
  margin-top: var(--space-xl);
  margin-bottom: var(--space-xl);
  padding: var(--space-lg);
  background-color: var(--color-gray-10);
  color: var(--color-white);
  text-align: center;
}

//TODO: Rework this when implement other templates

.article-template {
  h2 {
    margin-top: 48px;
    margin-bottom: 24px;
    font-size: var(--title-h3);
  }

  p {
    color: var(--color-gray-80);
    font-size: var(--text-md);
    line-height: var(--leading-lg);
    margin-bottom: var(--space-lg);

    code {
      font-family: var(--font-mono);
      font-size: 0.875rem;
      line-height: inherit;
      background: var(--color-red-97);
      color: var(--color-red);
    }

    a {
      color: var(--color-red);
      text-decoration: none;
    }
  }
}
</style>
