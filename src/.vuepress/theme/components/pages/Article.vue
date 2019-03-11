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
      font-size: var(--text-lg);
      line-height: var(--leading-lg);
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
  color: var(--color-gray-80);

  h3 {
    margin-bottom: var(--space-lg);
    font-size: var(--title-h4);
  }

  p {
    font-size: var(--text-md);
    line-height: 1.7;
    margin-bottom: var(--space-lg);

    code {
      font-family: var(--font-mono);
      font-size: 0.875rem;
      line-height: inherit;
      background: var(--color-secondary);
    }

    a {
      position: relative;

      &::before {
        position: absolute;
        content: '';
        height: 2px;
        width: 100%;
        bottom: 3px;
        left: 0;
        background: var(--color-secondary);
        opacity: 0.4;
        transition: opacity 0.24s ease-out;
      }

      &:hover {
        &::before {
          opacity: 1;
        }
      }
    }
  }

  ul,
  ol {
    margin-bottom: var(--space-xl);
  }

  li {
    margin-bottom: var(--space-md);
  }
}
</style>
