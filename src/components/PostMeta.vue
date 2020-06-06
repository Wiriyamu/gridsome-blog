<template>
  <div class="post-meta">
    Posted {{ post.date }}.
    <template v-if="post.timeToRead">
      <strong class="post-meta__min">{{ post.timeToRead }} min read.</strong>
    </template>
  </div>
</template>

<script>
export default {
  props: ['post']
}
</script>

<style lang="scss">
.post-meta {
  font-size: 0.8em;
  opacity: 0.8;

  &__min {
    color: #4fc08d;
  }
}
</style>