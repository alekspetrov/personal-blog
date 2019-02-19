---
date: 2019-02-19
template: "article"
title: "Static Blog, Part 2: Build static blog with the VuePress"
type: "Article"
category: "Frontend"
series: "Static blog"
description: "This is the first article from Static Blog series. I'm going to explore JAMStack and serverless architecture."
---

In The Design of Everyday Things, Don Norman wrote that irrespective of how designers envision their products (ie. the designers’ conceptual models), end users will always project their own mental models rooted from individual biases and worldviews onto their experiences of products.

```js
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
```

## Lets check the code

In The Design of Everyday Things, Don Norman wrote that irrespective of how designers envision their products (ie. the designers’ conceptual models), end users will always project their own mental models rooted from individual biases and worldviews onto their experiences of products.

```js
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
```

In The Design of `Everyday Things`, Don Norman wrote that irrespective of how designers envision their products (ie. the designers’ conceptual models), end users will always project their own mental models rooted from individual biases and worldviews onto their experiences of products.

> “In The Design of Everyday Things, Don Norman wrote that irrespective of how designers envision their products“
