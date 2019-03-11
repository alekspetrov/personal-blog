<template>
  <div>
    <div class="wrapper">
      <Content slot-key="banner"/>
      <section class="posts">
        <article class="post" v-for="post in posts" :key="post.key">
          <h3>
            <router-link :to="post.path">{{ post.title }}</router-link>
          </h3>
          <!-- <p>{{ post.frontmatter.description }}</p> -->
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
  padding-bottom: var(--space-md);

  h1 {
    margin: 0;
    margin-bottom: var(--space-md);
    font-weight: 900;
  }

  p {
    font-size: var(--text-lg);
    color: var(--color-gray-50);
    line-height: var(--leading-lg);
  }

  @include breakpoint(mobile) {
    padding-top: var(--space-xl);
    padding-bottom: var(--space-xl);
    margin-bottom: calc(var(--space-md) * 3);
  }
}

.post {
  margin-bottom: calc(var(--space-sm) * 3);
}
</style>
