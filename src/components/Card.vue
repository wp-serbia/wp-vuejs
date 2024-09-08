<template>
  <li>
    <router-link
      v-if="post.featured_image"
      :to="{ name: 'post', params: { slug: post.slug } }"
    >
      <img :src="post.featured_image" alt="Blog Post Featured Image" />
    </router-link>
    <span>
      <i>&mdash;</i>
      {{ getFormattedDate(post.date) }}
      <i>&mdash;</i>
    </span>
    <h3>
      <router-link
        :to="{
          name: 'post',
          params: {
            slug: post.slug
          }
        }"
        v-html="post.title.rendered"
      >
      </router-link>
    </h3>
  </li>
</template>

<script>
export default {
  name: "Card",

  props: {
    post: {
      type: Object
    }
  }
};
</script>

<style scoped lang="scss">
li {
  display: flex;
  flex-direction: colu mn;
  background: #cccccc;
  border: 2px solid darken(#cccccc, 5%);
  padding: 2rem 1rem;
  text-align: center;

  a {
    display: block;
  }
}

img {
  transition: box-shadow 0.15s ease-in-out;
  box-shadow: 0 0 0 2px #cccccc;

  &:hover {
    box-shadow: 0 0 0 3px #cccccc;
  }
}

span {
  font-size: 1.4em;
  color: #ccc;
  margin: 1rem 0 0.5rem;
}

h3 {
  margin: 0 0.25rem 0 1rem;

  a {
    color: inherit;

    &:hover {
      color: #f1f1f1;
    }

    &:focus {
      outline: none;
    }
  }
}
</style>
