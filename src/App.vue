<template>
    <h1>{{title}}</h1>
    <p>Welcome...</p>
    <!-- header and text are the props here and props are used to pass the data from parent to children component  -->
    <div v-if="showmodel">
       <!-- <model :header="header" :text="text" theme="sale" @close="togglemodel"/> -->

       <model theme="sale" @close="togglemodel"> 
         <!-- the template that we pass inside here is known as slot.it gets passe as a slot to the model componenet -->
         <h1>sign up for giveaway</h1>
         <p>grab at half price</p>

            <!-- named slots -->

         <template v-slot:links> 
           <a href="">Sign up now</a>
           <a href="">More info</a>
         </template>
       </model>

    </div>

    <div v-if="showmodel2">

       <model theme="" @close="togglemodel2"> 
         <h1>sign up to the newsletter</h1>
         <p>For update and promo </p>
       </model>

    </div>

    <button @click.alt="togglemodel"> Open Modal(alt)</button> <br> <br>
    <button @click="togglemodel2"> Open Modal two</button> <br> <br>
    <input type="text" ref="names"> 
    <button @click="handleclk">click me</button>
</template>

<script>
import model from './components/model.vue'

export default {
  name: 'App',
  data(){
    return{
    title:'My first vue app :)',
    // header:'sign up for the giveaway',
    // text:'grab your giveaway at half price',
    showmodel: false,
    showmodel2:false
    }
  },
  methods:{
    handleclk(){
      console.log(this.$refs.names)
      this.$refs.names.classList.add('active')
      this.$refs.names.focus()
    },
    togglemodel(){
      this.showmodel=!this.showmodel
    },
    togglemodel2(){
      this.showmodel2=!this.showmodel2
    }
  },
  components: {
    model
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  display: inline-block;
  padding-bottom: 10px;
  border-bottom: 1px solid #ddd;
}
</style>
