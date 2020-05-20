<template>
    <div class="item">
    </div>
</template>

<script>

export default {
 
  data(){
      return {
      x: undefined,
      y: undefined,
      }
  }
}
</script>

<style lang="scss">
    @import '../layout/styles.scss';
    .item{
        width: 10px;
        height: 10px;
        border: 1px solid black;
        box-sizing: border-box;
    }
</style>