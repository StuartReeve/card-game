<template>
  <div id="app">
    <!-- <button @click="shuffleCollection">Shuffle</button>
    <transition-group name="card-collection" tag="div" class="card-collection">
      <Card v-for="champ in champions" :champion="champ" :key="champ"/>
    </transition-group> -->
    <Board />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Card from "./components/Card/Card.vue";
import Board from "./components//Board.vue";
import { Champion } from "./common/interfaces";


@Component({
  components: {
    Card,
    Board
  }
})
export default class App extends Vue {
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
  private champions: Champion[] = [
    this.ekko,
    this.ekko2,
    this.ekko3,
    this.ekko4
  ];

  public shuffleCollection() {
    const winRate = parseFloat((Math.random() * 100).toFixed(2));
    const champ: Champion = {
      Name: "Ekko",
      Role: "Assassin",
      WinRate: winRate,
      Kills: 7.81,
      Deaths: 2.4,
      Assists: 6.07,
      Gold: 11962,
      DamageDealt: 18208,
      DamageTaken: 17222
    };

    this.champions.push(champ);
  }
}
</script>

<style lang="scss">
body {
  box-sizing: border-box;
  //padding: 30px;
  margin: 0;
  height: 100%;
  width: 100%;;
}

.card-collection {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
.card-collection-move {
  transition: all 1s;
}

.card-collection-enter-active,
.card-collection-leave-active {
  transition: all 2s;
}
.card-collection-enter/* .list-leave-active below version 2.1.8 */ {
  transform: translateX(100%);
}
.card-collection-enter-to {
  transform: translateX(0);
}
</style>
