<template> 
    <div class="board">
        <div class="game-mat">
            <div class="discard" @dragover.prevent @drop="discard"></div>
            <div class="play" @dragover.prevent @drop="play"></div>
        </div>
        <div class="hand">
            <Card v-for="(card, i) in hand" :champion="card" :key="i" draggable="true"/>
        </div>       
    </div>    
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import { Champion } from "../common/interfaces";
import Card from "../components/Card/Card.vue";

@Component({
    components: {
        Card
    }
})
export default class Board extends Vue {
  private ekko: Champion = {
    Name: "Ekko",
    Role: "Assassin",
    WinRate: 25,
    Kills: 7.81,
    Deaths: 2.4,
    Assists: 6.07,
    Gold: 11962,
    DamageDealt: 18208,
    DamageTaken: 17222
  };
  private ekko2: Champion = {
    Name: "Ekko",
    Role: "Assassin",
    WinRate: 50,
    Kills: 7.81,
    Deaths: 2.4,
    Assists: 6.07,
    Gold: 11962,
    DamageDealt: 18208,
    DamageTaken: 17222
  };
  private ekko3: Champion = {
    Name: "Ekko",
    Role: "Assassin",
    WinRate: 75,
    Kills: 7.81,
    Deaths: 2.4,
    Assists: 6.07,
    Gold: 11962,
    DamageDealt: 18208,
    DamageTaken: 17222
  };
  private ekko4: Champion = {
    Name: "Ekko",
    Role: "Assassin",
    WinRate: 100,
    Kills: 7.81,
    Deaths: 2.4,
    Assists: 6.07,
    Gold: 11962,
    DamageDealt: 18208,
    DamageTaken: 17222
  };
  private hand: Champion[] = [
    this.ekko,
    this.ekko2,
    this.ekko3,
    this.ekko4
  ];

  private discard(event: DragEvent) {
      event.stopPropagation();
        event.preventDefault();
      console.log(event);
  }

  private play(event: DragEvent) {
      event.stopPropagation();
        event.preventDefault();
      console.log(" I CHOOSE YOU");
  }

 
}
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css?family=PT+Sans|Roboto");
.board {
  width: 100vw;
  height: 100vh;
  background-image: url("../assets/background.jpg");
  background-position: center;
  background-size: cover;
  display: flex;
  flex-direction: column;
  .game-mat {
    display: flex;
    justify-content: space-around;
    .discard,
    .play {
        width:200px;
        height: 200px;
        border: 2px black dashed;
        margin: 50px;
    }
  }
  .hand {
    width: 100%;
    height: 500px;
    border-top: 2px black solid;
    display: flex;
    justify-content: space-around;
  }
}
</style>
