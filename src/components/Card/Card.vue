<template>
  <div class="card" :class="{flipped: isFlipped}" @click="flipCard">
    <div class="front">
      <div class="header">
        <span class="champ-name">{{champion.Name}}</span>
        <img width="40px" height="40px" src="https://www.dropbox.com/s/yfrwk3dkavoebyp/test2.png?raw=1" /> 
      </div>
      <div class="champion">
        <img src="http://i.imgur.com/7pl8Q3g.png" />
      </div>
      <div class="stats">
        <Stat name="Win Rate" :value="champion.WinRate" :percent="champion.WinRate" />
        <Stat name="Kills" :value="champion.Kills" :percent="56" />
        <Stat name="Deaths" :value="champion.Deaths" :percent="56" />
        <Stat name="Assists" :value="champion.Assists" :percent="56" />
        <Stat name="Gold" :value="champion.Gold" :percent="56" />
        <Stat name="Damage Dealt" :value="champion.DamageDealt" :percent="56" />
        <Stat name="Damage Taken" :value="champion.DamageTaken" :percent="56" />      
      </div>
    </div>
    <div class="back">
      
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import { Champion } from "../../common/interfaces";
import Stat from "./Stat.vue";

@Component({
  components: {
    Stat
  }
})
export default class Card extends Vue {
  @Prop() protected champion: Champion;
  private isFlipped: boolean = false;
  

  public flipCard() {
    this.isFlipped = !this.isFlipped;
  }
}
</script>

<style lang="scss" scoped>
.card {
  font-family: "Gothic A1", sans-serif;
  color: white;
  background-color: #1e2137;
  width: 265px;
  height: 500px;
  border-radius: 15px;
  display: flex;
  flex-direction: column;
  box-sizing: border-box;
  padding: 5px 17px 17px 17px;
  &:hover {
    box-shadow: 0 0 20px rgb(200, 155, 60);
  }
  &.flipped {
    transform: rotateY(180deg);
  }
  .header {
    font-size: 2em;
    display: flex;
    flex-direction: row;
    .champ-name {
      flex: 1;
    }
  }
  .champion {
    img {
      border-radius: 15px;
    }
  }
  .stats {    
    flex: 1;
    text-shadow: 1px 1px black;
    box-sizing: border-box;
    font-size: 0.8em;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
}
</style>
