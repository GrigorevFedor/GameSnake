<template>
   <div>
    <div class="gameMap">
        <item v-for="item of items" :item = "item" :key="String(item.x) + String(item.y)"/> 
    </div>
   </div>
    
</template>

<script>
import item from "../components/item.vue"

export default {
  components:{ item },
  data() {
      return {
          items:[],
          size: 10,
          }
  },
  methods:{},
  mounted() {
    
    for (let row = 0; row < this.$parent.rowsCount; row++) {
      for (let col = 0; col < this.$parent.colsCount; col++) {
          this.items.push({
            x:row, 
            y:col,
            type: 0
            })
      }      
  }
  }

}
</script>

<style lang="scss">
  .gameMap{
    display: flex;
    flex-wrap: wrap;
    width: 210px;
  }
</style>