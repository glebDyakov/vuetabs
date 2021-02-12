<template>
  <div>
    <div class="card">
      <!-- <h2>Актуальные новотси {{ now }}</h2> -->
      <!-- <h2>Slots</h2> -->
      <async-component></async-component>
      <h2>Динамические и ассинхронные компоненты</h2>
      
      <!-- <app-button 
      :color="active === 'one' ? 'primary' : ''" 
      @action="active = 'one'">
        One</app-button>
      <app-button
      :color="active === 'two' ? 'primary' : ''"
      @action="active = 'two'"
      >Two</app-button> -->
      <app-button
      ref="myBtn"
      :color="oneColor" 
      @action="active = 'one'">
        One</app-button>
      <app-button
      :color="twoColor"
      @action="active = 'two'"
      >Two</app-button>
      
      <!-- <span>Открыто: <strong>{{ openRate }}</strong> | Прочитано: <strong>{{ readRate }}</strong></span> -->
    </div>

    <app-text-one v-if="active === 'one'"></app-text-one>
    <app-text-two v-else-if="active === 'two'"></app-text-two>
    
    <!-- <component :is="AppTextOne"></component> -->
   <keep-alive>
    <component :is="comonentName"></component>
  </keep-alive>
    <!-- <app-list> -->
      <!-- <template #default="slotProps">
        <span style="color: #c25205;">
          <strong>{{ slotProps.idx + 1 }}</strong>
          Item: {{ slotProps.iter }}
          </span>
      </template> -->
      <!-- <template #default="{iter, idx}">
        <span style="color: #c25205;">
          <strong>{{ idx + 1 }}</strong>
          Item: {{ iter }}
          </span>
      </template>
    </app-list>
    <app-block>
      <p>Это самый важный текст для нового блока</p>
      <template v-slot:header>
        <h3>Это заголовок</h3>
      </template>
      <template v-slot:footer>
        <hr/>
        <small>Это футер</small>
      </template>
    </app-block> -->

    <!-- <div class="card" v-for="item in news" :key="item">
      <h3>{{ item }}</h3>
      <button class="btn"
      @click="isOpen=!isOpen"

      >Открыть</button>
      <p v-if="isOpen">Lorem ipsum dolor sit amet consectetur, adipisicing elit. Unde, veritatis!</p>
    </div> -->
    
    <!-- <app-news
    @unmark="unreadNews"
    @read-news="readNews"
     :title="item.title"
      :is-open="item.isOpen"
      :was-read="item.wasRead"
      v-for="item in news"
      :key="item.id"
      @open-news="openNews"
     ></app-news> -->

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
// import TheHeader from './TheHeader.vue'
// import AppNews from './AppNews.vue'
// import AppBlock from './AppBlock.vue'
// import AppList from './AppList.vue'
import AppTextOne from './AppTextOne.vue'
import AppButton from './AppButton.vue'
import AppTextTwo from './AppTextTwo.vue'
export default {
  data(){
    return {
      active: 'one'
    }
  },
  components:{
    AppTextTwo, AppTextOne, AppButton
  },
  mounted(){
    this.$refs.myBtn.btnLog()
  },
  computed:{
    // comonentName(){
      // if(this.active === 'one'){
      //   return 'app-text-one'
      // }
      // return 'app-text-one'
      // return 'app-active-' + this.active
    // },
    componentName:{
      get(){
        return 'app-text-' + this.active
      },
      set(value){
        
      } 
      
    },
    oneColor(){
      return this.active === 'one' ? 'primary' : ''
    },
    twoColor(){
      return this.active === 'two' ? 'primary' : ''
    }
  }
  // components:{
  //   AppBlock,
  //   AppList
  // }
  // methods:{
  //   readNews(id){
  //     const idx = this.news.findIndex(news => news.id === id)
  //     this.news[idx].wasRead = true
  //     this.readRate++
  //   },
  //   openNews(){
  //     this.openRate++

  //   },
  //   unreadNews(id){
  //     const news = this.news.find(news => news.id == id)
  //     news.wasRead = false
  //     this.readRate--
  //   }
  // },
  // provide(){
  //   return {
  //     title:'Список всех новостей',
  //     news:this.news
  //   }
  // },
  //   // provide:{
  // //   title:'Список всех новостей'
  // // },
  // data(){
  //   return {
  //     openRate: 0,
  //     readRate: 0,
  //     now: new Date().toLocaleDateString(),
  //     news: [
  //       {
  //         title: 'Джо Байден победил на выборах США',
  //         id: 1,
  //         isOpen:false,
  //         wasRead: false,
  //       },
  //       {
  //         title: 'Vue 3 успешно работает',
  //         id: 2,
  //         isOpen:false,
  //         wasRead: false
  //       },
        
  //     ]
  //   }
  // },
  // components: {
  //   TheHeader,
  //   'app-news': AppNews,
  // },
  
}
</script>
<style>
  /* h2{
    color:red;
  } */
  
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&display=swap');

* {
    box-sizing: border-box;
}

body {
    font-family: Inter, Roboto, Oxygen, Fira Sans, Helvetica Neue, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-size: 16px;
    color: #2c3e50;
    background: #2c3e50;
}

hr {
    margin: 1rem 0;
}

strong,
.bold {
    font-weight: 500;
}

ol,
p,
ul {
    line-height: 1.7;
}

a {
    color: #3eaf7c;
    font-weight: 500;
    text-decoration: none;
}

h1,
h2,
h3,
h4,
h5,
h6 {
    font-weight: 500;
    line-height: 1.45;
}

h1 {
    font-size: 2.2rem;
    font-weight: 600;
}

h2 {
    font-size: 1.65rem;
    padding-bottom: 0.3rem;
    border-bottom: 1px solid #eaecef;
}

h3 {
    font-size: 1.35rem;
}

/*.primary {*/
/*    color: #42b983;*/
/*}*/

/*.danger {*/
/*    color: #e53935;*/
/*}*/

.btn {
    color: #42b983;
    position: relative;
    place-content: center;
    place-items: center;
    width: fit-content;
    border-radius: 99px;
    letter-spacing: 0.05em;
    border: 1px solid #42b983;
    text-decoration: none;
    text-transform: uppercase;
    margin-right: 10px;
    padding: 0.5rem 1.5rem;
    white-space: nowrap;
    font-weight: 700;
    outline: none;
    background: #fff;
    transition: all 0.22s;
}

.btn:hover {
    cursor: pointer;
    opacity: 0.8;
}

.btn:disabled {
    cursor: not-allowed;
    opacity: 1!important;
    background: #eee!important;
    border-color: #ddd!important;
    color: #999!important;
}

.btn:active {
    box-shadow: inset 1px 1px 1px rgba(0, 0, 0, 0.3);
}

.btn.primary {
    background: #42b983;
    color: #fff;
}

.btn.danger {
    background: #e53935;
    color: #fff;
    border-color: #e53935;
}

.btn.warning {
    background: #c25205;
    color: #fff;
    border-color: #c25205;
}

.container {
    margin: 0 auto;
    max-width: 1000px;
}

.container.with-nav {
    margin-top: 70px;
}

.pt-2 {
    padding-top: 2rem;
}

.pt-1 {
    padding-top: 1rem;
}

.pt-5 {
    padding-top: 5rem;
}

.form-control {
    position: relative;
    margin-bottom: 0.5rem;
}

.form-control input,
.form-control select {
    margin: 0;
    outline: none;
    border: 2px solid #ccc;
    display: block;
    width: 100%;
    color: #2c3e50;
    padding: 0.5rem 1.5rem;
    border-radius: 3px;
    font-size: 1rem;
}

.form-control small {
    color: #e53935;
}

.form-control.invalid input {
    border-color: #e53935;
}

.form-checkbox {
    margin-bottom: 1rem;
}

.form-checkbox .label {
    display: block;
    margin: 0 0 0.3rem 0.3rem;
    font-weight: 500;
}

.form-checkbox .checkbox input {
    margin-right: 1rem;
}

.form-control label {
    display: block;
    margin: 0 0 0.3rem 0.3rem;
    font-weight: 500;
}

.form-control input:active,
.form-control input:focus {
    transition: border 0.22s;
    border: 2px solid #42b983;
}

.card {
    overflow: hidden;
    padding: 1rem;
    margin-bottom: 1rem;
    border-radius: 10px;
    box-shadow: 2px 3px 10px rgba(0, 0, 0, 0.2);
    background: #fff;
}

.card.marked {
    border: 4px solid #42b983;
}

.card.center {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.list {
    margin: 0;
    padding: 0;
    list-style: none;
}

.list-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0.5rem 0;
    transition: .22s all;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
}

.list-item:hover {
    background: #eee;
}

.alert {
    padding: 1rem 1.5rem;
    border-left-width: .5rem;
    border-left-style: solid;
    margin: 1rem 0;
    position: relative;
    border-bottom-right-radius: 2px;
    border-top-right-radius: 2px;
}

.alert.primary {
    border-color: #42b983;
    background-color: #f8f8f8;
}

.alert.danger {
    border-color: #e53935;
    background-color: #f8f8f8;
}

.alert.warning {
    border-color: #c25205;
    background-color: #f8f8f8;
}

.alert p {
    color: #222;
    line-height: 1.7;
}

.alert-title {
    text-transform: uppercase;
    font-weight: 600;
    margin-bottom: -.4rem;
    color: #222;
}

.modal {
    position: fixed;
    top: 60px;
    width: 600px;
    padding: 1rem;
    background: #fff;
    z-index: 1000;
    left: 50%;
    border-radius: 10px;
    transform: translateX(-50%);
    box-shadow: 2px 3px 10px rgba(0, 0, 0, 0.2);
}

.modal-backdrop {
    position: fixed;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
    background: rgba(0, 0, 0, .35);
}





.loader {
    font-size: 10px;
    margin: 50px auto;
    text-indent: -9999em;
    width: 11em;
    height: 11em;
    border-radius: 50%;
    background: #ffffff;
    background: -moz-linear-gradient(left, #ffffff 10%, rgba(255, 255, 255, 0) 42%);
    background: -webkit-linear-gradient(left, #ffffff 10%, rgba(255, 255, 255, 0) 42%);
    background: -o-linear-gradient(left, #ffffff 10%, rgba(255, 255, 255, 0) 42%);
    background: -ms-linear-gradient(left, #ffffff 10%, rgba(255, 255, 255, 0) 42%);
    background: linear-gradient(to right, #ffffff 10%, rgba(255, 255, 255, 0) 42%);
    position: relative;
    -webkit-animation: load3 1.4s infinite linear;
    animation: load3 1.4s infinite linear;
    -webkit-transform: translateZ(0);
    -ms-transform: translateZ(0);
    transform: translateZ(0);
}
.loader:before {
    width: 50%;
    height: 50%;
    background: #ffffff;
    border-radius: 100% 0 0 0;
    position: absolute;
    top: 0;
    left: 0;
    content: '';
}
.loader:after {
    background: #2c3e50;
    width: 75%;
    height: 75%;
    border-radius: 50%;
    content: '';
    margin: auto;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
}
@-webkit-keyframes load3 {
    0% {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    100% {
        -webkit-transform: rotate(360deg);
        transform: rotate(360deg);
    }
}
@keyframes load3 {
    0% {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    100% {
        -webkit-transform: rotate(360deg);
        transform: rotate(360deg);
    }
}

.navbar {
    display: flex;
    padding: 0 2rem;
    justify-content: space-between;
    align-items: center;
    position: fixed;
    z-index: 20;
    top: 0;
    left: 0;
    right: 0;
    height: 56px;
    background-color: #fff;
    box-sizing: border-box;
    border-bottom: 1px solid #eaecef;
}

.navbar-menu {
    list-style: none;
    display: flex;
}

.navbar-menu li {
    margin-right: 2rem;
}

.navbar-menu li a {
    color: #2c3e50;
    text-decoration: none;
}

.navbar-menu li a:hover, .navbar-menu li a.active {
    border-bottom: 2px solid #3eaf7c;
}
</style>