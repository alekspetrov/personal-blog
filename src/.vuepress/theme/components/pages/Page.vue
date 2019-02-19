<template>
  <div class="page-layout page">
    <div class="wrapper">
      <div class="page">
        <div class="page__header">
          <h1>{{ $page.frontmatter.title }}</h1>
          <div class="page__info post-data">
            <time :datetime="$page.frontmatter.date">{{ date($page.frontmatter.date) }}</time>
            <span>&nbsp;•&nbsp;</span>
            <span>{{ $page.frontmatter.category }}</span>
          </div>
        </div>
        <div v-if="$page.frontmatter.template==='article'" class="article-template">
          <Content/>
        </div>
        <div class="follow-link">
          <p>
            Don't miss the next post, follow my
            <a href="https://twitter.com/alekspetrovlive">Twitter</a>
          </p>
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
    padding-top: var(--space-2xl);
    margin-bottom: var(--space-2xl);

    h1 {
      margin-bottom: 12px;
    }
  }

  &__info {
    font-size: 18px;
  }
}

.follow-link {
  background-color: var(--color-gray-10);
  color: var(--color-white);
  padding: var(--space-xl);
  text-align: center;
}

//TODO: Rework this when implement other templates
.article-template {
  // h2 {
  //   margin-top: 48px;
  //   margin-bottom: 24px;
  // }

  p {
    // font-size: 18px;
    // line-height: 28px;

    code {
      background: var(--color-red-97);
      color: var(--color-red);
    }
  }
}
</style>
