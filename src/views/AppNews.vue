<template>
    <div class="card">
        <h3>{{ title }}</h3>
        <!-- @click="isOpen=!isOpen" -->
        <button class="btn"
         
         @click="open"
         >{{ isNewsOpen ? 'Закрыть' : "Открыть" }}</button>
        <!-- v-if="isOpen" -->
        <p v-if="isNewsOpen">Lorem ipsum dolor sit amet consectetur, adipisicing elit. Unde, veritatis!</p>
    </div>   
</template>
 <script>
 export default {
    props:{
        //  title:String,
        title:{
            type: String,
            required: true,
        },
        //  id:Number,
        id:{
            type:Number,
            required: true
        },
        //  isOpen:Boolean,
        isOpen:{
            type:Boolean,
            required:false,
            default: false,
            validator(value){
                return true
            }
        }
     },
     data(){
         return {
             isNewsOpen: this.isOpen
         }
     },
     methods:{
         open(){
            //  this.isOpen = !this.isOpen
            this.isNewsOpen = !this.isNewsOpen
            if(this.isNewsOpen){
                this.$emit('open-news')
            }
         }
     }
 }
 </script>