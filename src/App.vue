<template>
  <div id="app">
    <Card :champion="ekko"/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Card from "./components/Card/Card.vue";
import { Champion } from "./common/interfaces";

@Component({
  components: {
    Card
  }
})
export default class App extends Vue {
  private ekko: Champion = {
    Name: "Ekko",
    Role: "Assassin",
    WinRate: 50.2,
    Kills: 7.81,
    Deaths: 2.4,
    Assists: 6.07,
    Gold: 11962,
    DamageDealt: 18208,
    DamageTaken: 17222
  };
}
</script>