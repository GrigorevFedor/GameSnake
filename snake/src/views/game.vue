<template>
   <div>
    <p align="center" id="score"></p>
    <gameMap ref="gameMap"/>
    <div id="menu">
      <div id="playButton" class="menuButton">Старт</div>
      <div id="newGameButton" class="menuButton">Новая игра</div>
    </div>
   </div>
    
</template>

<script>
import gameMap from "../components/gameMap.vue"

export default {
  components:{gameMap},
  data(){
    return {
    rowsCount: 21,
    colsCount: 21,
    speed: 4,
    winFoodCount: 50, 
  } 
  },


}
</script>


