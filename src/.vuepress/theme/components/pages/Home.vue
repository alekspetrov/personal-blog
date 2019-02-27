<template>
  <div>
    <div class="wrapper">
      <Content slot-key="banner"/>
      <section class="posts">
        <article class="post" v-for="post in posts" :key="post.key">
          <h3>
            <router-link :to="post.path">{{ post.title }}</router-link>
          </h3>
          <p>{{ post.frontmatter.description }}</p>
          <div class="post__info post-data">
            <time :datetime="post.frontmatter.date">{{ date(post.frontmatter.date) }}</time>
            <span>&nbsp;•&nbsp;</span>
            <span>{{ post.frontmatter.category }}</span>
          </div>
        </article>
      </section>
    </div>
  </div>
</template>

<script>
import dateFormat from "../../utils/dateFormat.js";

export default {
  name: "Home",
  props: ["page"],
  methods: {
    date(date) {
      return dateFormat(date);
    }
  },
  computed: {
    posts() {
      const posts = this.$site.pages.filter(page => page.path !== "/");
      return posts;
    }
  }
};
</script>

<style lang="scss">
@import "../../styles/breakpoints";

.banner {
  margin-bottom: var(--space-xl);
  padding-top: var(--space-xl);
  padding-bottom: var(--space-xl);
  border-bottom: 2px solid var(--color-black);

  h1 {
    margin: 0;
    margin-bottom: var(--space-md);
    font-weight: 900;
  }

  p {
    font-size: var(--text-lg);
  }
}

.post {
  margin-bottom: var(--space-lg);
  padding-bottom: var(--space-lg);

  &:not(:last-child) {
    border-bottom: 1px solid var(--color-gray-80);
  }

  &__info {
    margin-bottom: var(--space-lg);
    font-size: var(--text-xs);
  }

  p {
    font-size: var(--text-sm);
    line-height: var(--leading-lg);
    margin-bottom: var(--space-md);
  }
}
</style>
