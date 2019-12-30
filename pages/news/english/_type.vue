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
import axios from 'axios'

function getTypeName(type) {
  switch (type.toLowerCase()) {
    case "cnn":
      return "cnn";
    case "bbc":
      return "bbc-news";
    default:
      return null;
  }
}

export default {
  page_count: 0,
  validate ({ params }) {
    let type = params.type;

    if (typeof type == "undefined" || getTypeName(type) == null) {
      return false;
    }

    return true;
  },
  async asyncData ({ params }) {
    var url = "https://newsapi.org/v2/top-headlines?sources=" + getTypeName(params.type) + "&apiKey=9da0ea85f0024417bf2af4d4a674047c";
    const{data} = await axios.get(url)

    return {
      newsList: data.articles
    };
  }
}
</script>
