<template>
  <div id="app">
    <div class="main">
      <div class="shuju">
        <span>您选择了 <span>{{ cachR.length }}</span> 个红球 <span>{{ cachB.length }}</span>个蓝球，共
        <span>{{ temp }}</span> 注，共 <span>{{ acount }}</span> 元</span>
      </div>

      <div class="boxR">
        <div class="default" v-for="(itemR,$index) in arrR" @click="clickR (itemR, $index) " :class="{'activeR':itemR.flag}">{{ itemR.num }}</div>
      </div>
      <div class="boxB">
        <div class="default" v-for="(itemB,$index) in arrB" @click="clickB (itemB, $index) " :class="{'activeB':itemB.flag}">{{ itemB.num }}</div>
      </div>
    </div>

    <router-view></router-view>
  </div>
</template>

<script>
  export default {
    name: 'app',
    data: function () {
      return {
        cachR: [],
        cachB: [],
        temp: 0,
        acount: 0,
        arrR: [{ flag: false, num: 1 },
        { flag: false, num: 2 },
        { flag: false, num: 3 },
        { flag: false, num: 4 },
        { flag: false, num: 5 },
        { flag: false, num: 6 },
        { flag: false, num: 7 },
        { flag: false, num: 8 },
        { flag: false, num: 9 },
        { flag: false, num: 10 },
        { flag: false, num: 11 },
        { flag: false, num: 12 },
        { flag: false, num: 13 },
        { flag: false, num: 14 },
        { flag: false, num: 15 },
        { flag: false, num: 16 },
        { flag: false, num: 17 },
        { flag: false, num: 18 },
        { flag: false, num: 19 },
        { flag: false, num: 20 },
        { flag: false, num: 21 },
        { flag: false, num: 22 },
        { flag: false, num: 23 },
        { flag: false, num: 24 },
        { flag: false, num: 25 },
        { flag: false, num: 26 },
        { flag: false, num: 27 },
        { flag: false, num: 28 },
        { flag: false, num: 29 },
        { flag: false, num: 30 },
        { flag: false, num: 31 },
        { flag: false, num: 32 },
        { flag: false, num: 33 },],
        arrB: [{ flag: false, num: 1 },
        { flag: false, num: 2 },
        { flag: false, num: 3 },
        { flag: false, num: 4 },
        { flag: false, num: 5 },
        { flag: false, num: 6 },
        { flag: false, num: 7 },
        { flag: false, num: 8 },
        { flag: false, num: 9 },
        { flag: false, num: 10 },
        { flag: false, num: 11 },
        { flag: false, num: 12 },
        { flag: false, num: 13 },
        { flag: false, num: 14 },
        { flag: false, num: 15 },
        { flag: false, num: 16 }]
      }
    },
    methods: {
      clickR(itemR, index) {
        itemR.flag = !itemR.flag;
        if (itemR.flag) {
          this.cachR.push(itemR.num);
        }
        else {
          this.cachR.pop(itemR.num);
        }
         if(this.cachR.length <= 5){
          this.temp = 0;
          this.acount = 0;

        }
        else if ((this.cachB.length >= 1) && (this.cachR.length >= 6)) {
          if (this.cachR.length == 6) {
            this.temp = 1 * this.cachB.length;
            // alert(temp);

            this.acount = this.temp * 2;

          }
          else {
            function factorial(n) {
              return n > 1 ? n * factorial(n - 1) : 1;
            }
            this.temp = factorial(this.cachR.length) / factorial(6) / factorial(this.cachR.length - 6) * this.cachB.length;

            // alert(myArrayR.combine());
            // var temp = myArrayR.combine() * myArrayB.length;

            this.acount = this.temp * 2;

          }
        }


      　　　　},
      clickB(itemB, index) {
        itemB.flag = !itemB.flag;
        if (itemB.flag) {
          this.cachB.push(itemB.num);
        }
        else {
          this.cachB.pop(itemB.num);
        }
        if(this.cachB.length == 0){
          this.temp = 0;
          this.acount = 0;

        }
        else if ((this.cachB.length >= 1) && (this.cachR.length >= 6)) {
          if (this.cachR.length == 6) {
            this.temp = 1 * this.cachB.length;
            // alert(temp);

            this.acount = this.temp * 2;

          }
          else {
            function factorial(n) {
              return n > 1 ? n * factorial(n - 1) : 1;
            }
            this.temp = factorial(this.cachR.length) / factorial(6) / factorial(this.cachR.length - 6) * this.cachB.length;

            // alert(myArrayR.combine());
            // var temp = myArrayR.combine() * myArrayB.length;

            this.acount = this.temp * 2;

          }
        }


      　　　　}
    }

  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.main{
  height: 200px;
  width: 990px;
  margin: auto;
}
.shuju{
   height: 20px;
  width: 990px;
  margin: auto;
}
.boxR{
  float: left;
  /*background: red;*/
  width: 550px;
  height: 200px;
}
.boxB{
 float: right;
  /*background: red;*/
  width: 294px;
  height: 200px;
}
.default{
  float: left;
  width: 39px;
  height: 37px;
  margin:5px;
  line-height: 36px;
  text-align: center;
  font-weight: bold;
  cursor: pointer;
  font-size: 14px;
  font-family: '微软雅黑';
  background: url(./assets/allbgs.png) no-repeat;
  background-position: -55px 0;
}
.boxR .default:hover{
  background-position: -95px 0; 
}
.boxB .default:hover{
  background-position: -175px 0; 
}
.activeR{
  background-position: -135px 0;
}
.activeB{
  background-position: -215px 0;
}
</style>