<template>
  <div>
    <div class="card">
      <h2>Актуальные новотси {{ now }}</h2>
      <span>Открыто: {{ openRate }}</span>
    </div>
    <!-- <div class="card" v-for="item in news" :key="item">
      <h3>{{ item }}</h3>
      <button class="btn"
      @click="isOpen=!isOpen"

      >Открыть</button>
      <p v-if="isOpen">Lorem ipsum dolor sit amet consectetur, adipisicing elit. Unde, veritatis!</p>
    </div> -->
    
    <app-news
     :title="item.title"
      :is-open="item.isOpen"
      v-for="item in news"
      :key="item.id"
      @open-news="openRate++"
     ></app-news>
  </div>
</template>
<script>
import TheHeader from './TheHeader.vue'
import AppNews from './AppNews.vue'
export default {
  data(){
    return {
      openRate: 0,
      now: new Date().toLocaleDateString(),
      news: [
        {
          title: 'Джо Байден победил на выборах США',
          id: 1
        },
        {
          title: 'Vue 3 успешно работает',
          id: 2
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

</style>