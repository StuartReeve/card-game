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
        <Stat name="Kills" :value="champion.Kills" :percent="100" />
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
@import url('https://fonts.googleapis.com/css?family=PT+Sans');
.card {
  position: relative;
  font-family: 'PT Sans', sans-serif;
  font-weight: lighter;
  color: white;
  width: 265px;
  height: 500px;
  border-radius: 15px;
  .front,
  .back {
    background-color: #1e2137;
    border-radius: 15px;
    backface-visibility: hidden;
    position: absolute;
    width: 100%;
    height: 100%;
    transition: 1s;
    transform-style: preserve-3d;

    &:hover {
      box-shadow: 0 0 20px rgb(200, 155, 60);
    }
  }
  .front {
    display: flex;
    flex-direction: column;
    box-sizing: border-box;
    padding: 5px 17px 17px 17px;
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
  .back {
    background-image: url("../../assets/logo.png");
    background-position: center;
    background-repeat: no-repeat;
    transform: rotateY(-180deg);
  }
  &.flipped {
    .front {
      transform: rotateY(-180deg);
    }
    .back {
      transform: rotateY(0);
    }
  }
}
</style>