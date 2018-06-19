<template>
  <div class="card" :class="{flipped: isFlipped}" @click="flipCard" @mousedown="mouseDown" @mouseup="mouseUp" @mousemove="mouseMove">
    <div class="back" on-drop>
               
    </div>
    <div class="front">
      <div class="header">
        <span class="champ-name">{{champion.Name}}</span>
        <img width="40px" height="40px" src="https://www.dropbox.com/s/yfrwk3dkavoebyp/test2.png?raw=1" draggable="false" /> 
      </div>
      <div class="champion">
        <img src="http://i.imgur.com/7pl8Q3g.png" draggable="false" />
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

  private dragging: boolean = false;
  private dragOffset: { x: number; y: number } = { x: 0, y: 0 };

  public flipCard() {
    this.isFlipped = !this.isFlipped;
  }

  private mouseDown(event: MouseEvent) {
    this.dragging = true;
    this.dragOffset.x -= event.clientX;
    this.dragOffset.y -= event.clientY;
    this.$el.style.position = "absolute";
    console.log("dragging", this.dragging);
  }

  private mouseUp(event: MouseEvent) {
    // this.$el.style.position = null;
    // this.$el.style.left = null;
    // this.$el.style.top = null;
    this.dragging = false;
    this.dragOffset = { x: 0, y: 0 };
    console.log("dragging", this.dragging);
  }

  private mouseMove(event: MouseEvent) {
    event.preventDefault();
    if (this.dragging) {
      this.$el.style.left = (event.clientX + this.dragOffset.x) + "px";
      this.$el.style.top = (event.clientY + this.dragOffset.y) + "px";
    }
  }
}
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css?family=PT+Sans");
.card {
  user-select: none;
  position: relative;
  font-family: "PT Sans", sans-serif;
  font-weight: lighter;
  color: white;
  width: 265px;
  height: 500px;
  border-radius: 15px;
  margin-top: 10px;
  .front,
  .back {
    cursor: pointer;
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