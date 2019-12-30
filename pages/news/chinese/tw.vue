<template>
  <div class="container-sm">
    <news-item :newsList=newsList></news-item>
  </div>
</template>

<script>
import axios from 'axios'
import news_item from '~/components/news_item.vue'

export default {
  layout: "second",
  components: {
    'news-item': news_item
  },
  async asyncData () {
    var url = "https://newsapi.org/v2/top-headlines?country=tw&apiKey=9da0ea85f0024417bf2af4d4a674047c";
    const{data} = await axios.get(url)

    return {
      newsList: data.articles
    };
  }
}
</script>
