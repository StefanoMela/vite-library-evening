<script>
export default {
  props: {

    book: Object,

  },
};
</script>

<template>
  <div class="card h-100">
      <div class="card-header">
          <span
          class="badge text-success"
          v-if="book.genre"
          >{{ book.genre.name }}</span
          >
          <h5 class="card-title">{{book.name}}</h5>
          <span
          v-for="tag in book.tags"
          :style="{ backgroundColor: tag.color }"
          class="badge rounded-pill mx-1"
          >
          {{ tag.label }}
        </span>
    </div>
    <div class="card-body">
       <img v-if="book.cover_img" :src="book.cover_img" class="card-img-top"/>
      <p class="card-text">
        {{ book.description }}
      </p>
      <a href="#" class="btn btn-primary">Clicca per la show</a>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
