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
.page {
  margin-bottom: var(--space-3xl);

  &__header {
    padding-top: var(--space-2xl);
    margin-bottom: var(--space-2xl);

    h1 {
      margin-bottom: 8px;
    }
  }

  p {
    font-size: 18px;
    line-height: 28px;
  }
}
</style>
