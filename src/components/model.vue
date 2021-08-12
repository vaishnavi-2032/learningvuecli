<template>
   <div class="backdrop" @click.self="closemodule">
       <div class="model" :class="{ sale: theme=== 'sale'}">
           <!-- {{header}} -->
           <!-- {{text}} -->
           <!-- defaultslot -->
           <!-- default content will only show up if there is no content to pass in slot -->
          <slot>Default content</slot> 
          <div class="action">
              <!-- named slot -->
            <slot name="links"></slot>
          </div>
       </div>
   </div> 
</template>

<script>
export default {
  props: ['header','text','theme'],
  methods:{
      closemodule(){
          //emitting custome events
          this.$emit('close')
      }
  }
}
</script>

<style>
    .model{
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background: white;
        border-radius: 10px;
    }
    .backdrop{
        top: 0;
        position: fixed;
        background: rgba(0,0,0,0.5);
        width: 100%;
        height: 100%;
    }
    .model h1{
        color: #03cfb4;
        border: none;
        padding: 0;
    }
    .model .action{
        text-align: center;
        margin: 30px 0 10px 0;
    }
    .model .action a{
        color: #333;
        padding: 8px;
        border: 1px solid #eee;
        border-radius: 4px;
        text-decoration: none;
        margin: 10px;
    }
    .model.sale{
        background: crimson;
        color: white;
    }
    .model.sale h1{
        color: white;
    }
    .model.sale .action{
        color: white;
    }
    .model.sale .action a{
        color: white;
    }
</style>