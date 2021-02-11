<template>
  <div>
    <div class="card">
      <h2>Актуальные новотси {{ now }}</h2>
      <span>Открыто: <strong>{{ openRate }}</strong> | Прочитано: <strong>{{ readRate }}</strong></span>
    </div>
    <!-- <div class="card" v-for="item in news" :key="item">
      <h3>{{ item }}</h3>
      <button class="btn"
      @click="isOpen=!isOpen"

      >Открыть</button>
      <p v-if="isOpen">Lorem ipsum dolor sit amet consectetur, adipisicing elit. Unde, veritatis!</p>
    </div> -->
    
    <app-news
    @unmark="unreadNews"
    @read-news="readNews"
     :title="item.title"
      :is-open="item.isOpen"
      :was-read="item.wasRead"
      v-for="item in news"
      :key="item.id"
      @open-news="openNews"
     ></app-news>

     <!-- <app-news
    :news="news"
    @unmark="unreadNews"
    @read-news="readNews"
     :title="item.title"
      :is-open="item.isOpen"
      :was-read="item.wasRead"
      v-for="item in news"
      :key="item.id"
      @open-news="openNews"
     ></app-news> -->
     <!-- @open-news="openRate++" -->
  </div>
</template>
<script>
import TheHeader from './TheHeader.vue'
import AppNews from './AppNews.vue'
export default {
  methods:{
    readNews(id){
      const idx = this.news.findIndex(news => news.id === id)
      this.news[idx].wasRead = true
      this.readRate++
    },
    openNews(){
      this.openRate++

    },
    unreadNews(id){
      const news = this.news.find(news => news.id == id)
      news.wasRead = false
      this.readRate--
    }
  },
  provide(){
    return {
      title:'Список всех новостей',
      news:this.news
    }
  },
    // provide:{
  //   title:'Список всех новостей'
  // },
  data(){
    return {
      openRate: 0,
      readRate: 0,
      now: new Date().toLocaleDateString(),
      news: [
        {
          title: 'Джо Байден победил на выборах США',
          id: 1,
          isOpen:false,
          wasRead: false
        },
        {
          title: 'Vue 3 успешно работает',
          id: 2,
          isOpen:false,
          wasRead: false
        },
        
      ]
    }
  },
  components: {
    TheHeader,
    'app-news': AppNews,
  },
  
}
</script>
<style>
  h2{
    color:red;
  }
</style>