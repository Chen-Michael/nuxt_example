<template>
  <div class="container-sm">
    <div class="card mb-3" :key="index" v-for="(item, index) in newsList">
      <img :src="item.urlToImage" :alt="item.title" class="card-img-top">
      <div class="card-body">
        <h5 class="card-title">
          <a :href="item.url" target="_blank">{{item.title}}</a>
        </h5>
        <p class="card-text">{{item.description}}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    props: {
        newsList: {
            type: Array,
            required: true
        }
    }
}
</script>