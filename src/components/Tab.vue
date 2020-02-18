<template>
    <div id="tab"></div>
</template>

<script>
export default {
    render (createElement){
      return createElement('div',{
        attrs:{
          id:'tab1'
        }
      },this.message)
    },
    data() {
      return {
        message:'html'
      }
    }
}
</script>

<style>

</style>