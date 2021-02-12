<template>
    <button @click="$emit('action')" class="btn" :class="color">
        <!-- {{ text }} -->
        <slot/>
    </button>
</template>
<script>
export default {
    emits:[
        'action'
    ],
    methods:{
        btnLog(){
            console.log('Button log')
        }
    },
    props:{
        // text: {
        //     type: String,
        //     required: true
        // },
        color:{
            type:String,
            default:'',
            validator(value){
                ['', 'primary', 'danger'].includes(value)
            }
        }
    }
}
</script>
<style scoped>

</style>