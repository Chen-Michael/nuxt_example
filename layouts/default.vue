<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbar">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbar">
        <div class="navbar-nav">
          <nuxt-link 
            class="nav-item nav-link" 
            :class="{ active: getNowPageName() == item.pageName }" 
            :to="item.url" 
            :key="index" 
            v-for="(item, index) in newsList"
          >{{item.title}}</nuxt-link>
        </div>
      </div>
    </nav>
    <nuxt />
  </div>
</template>

<script>
export default {
  data () {
    return {
      newsList: [
        {
          title: "Home",
          url: "/",
          pageName: "index"
        },
        {
          title: "BBC",
          url: "/news/english/bbc/",
          pageName: "news-english-bbc"
        },
        {
          title: "CNN",
          url: "/news/english/cnn/",
          pageName: "news-english-cnn"
        },
        {
          title: "TW News",
          url: "/news/chinese/tw/",
          pageName: "news-chinese-tw"
        }
      ]
    };
  },
  methods: {
    getNowPageName () {
      return this.$nuxt.$route.name;
    }
  }
}
</script>

<style>
html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}
</style>
