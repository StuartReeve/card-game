<template> 
    <div class="stat">        
        <div class="stat-bar">
            <span class="stat-name">{{name}}</span>          
            <span class="stat-percent">{{value}}</span>
            <div class="stat-bar-percent" :style="percentStyle"></div>
        </div>        
    </div>
    
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class Stat extends Vue {
  @Prop() name: string;
  @Prop() value: number;
  @Prop() percent: number;

  public mounted() {
  }

  get percentStyle() {
      const temp = {
      width: `${this.percent}%`
    };
    return temp;
  }
}
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css?family=PT+Sans|Roboto');
.stat {
  font-family: 'Roboto', sans-serif;
  flex-direction: row;
  align-items: center;
  margin-top: 12px;
  .stat-name {
    transform: skewX(20deg);
    position: absolute;
    top: -10px;
  }
  .stat-bar {
    border-left: 5px solid rgb(200, 155, 60);
    transform: skewX(-20deg);
    flex: 1;
    height: 15px;
    background: #131321;
    .stat-bar-percent {
      background: linear-gradient(to right, #0899cf, #0dcaa2);
      height: 100%;
    }
  }
  .stat-percent {
    transform: skewX(20deg);
    float: right;
    margin-right: 15px;
    line-height: 15px;
  }
}
</style>
