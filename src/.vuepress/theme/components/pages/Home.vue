<template>
  <div>
    <div class="wrapper">
      <Content slot-key="banner"/>
      <section class="posts">
        <article class="post" v-for="post in posts" :key="post.key">
          <h3>
            <router-link :to="post.path">{{ post.title }}</router-link>
          </h3>
          <div class="post__info post-data">
            <time :datetime="post.frontmatter.date">{{ date(post.frontmatter.date) }}</time>
            <span>&nbsp;•&nbsp;</span>
            <span>{{ post.frontmatter.category }}</span>
          </div>
          <p>{{ post.frontmatter.description }}</p>
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
  padding-top: var(--space-2xl);
  padding-bottom: var(--space-2xl);
  border-bottom: 2px solid var(--color-black);
  margin-bottom: 2em;

  h1 {
    font-size: 44px;
    line-height: 44px;

    // font-size: 56px;
    // line-height: 56px;

    // font-size: 5em;
    // line-height: 0.875em;

    margin: 0;
    margin-bottom: 24px;

    @include breakpoint(tablet) {
      font-size: 56px;
      line-height: 56px;
    }
  }

  p {
    font-size: 20px;
    line-height: 28px;
  }
}

.post {
  margin-bottom: 24px;
  padding-bottom: 24px;

  &:not(:last-child) {
    border-bottom: 1px solid var(--color-gray-80);
  }

  &__info {
    margin-bottom: 20px;
  }

  time {
    display: inline-block;
    font-size: 16px;
  }

  p {
    font-size: 18px;
    line-height: 25px;
  }

  a {
    display: inline-block;
  }
}
</style>


