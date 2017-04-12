<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <textarea v-model="numberText" style="width: 1000px;height: 500px;margin: 20px;padding: 50px;font-size: 3rem;line-height: 4rem;" ></textarea>
  <button @click="getNumGroup" style="width: 80px;height: 80px;display:inline-block;">测试</button>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
       numberText: ""
    }
  },
  
     methods: {
      getNumGroup() {
        var value = this.numberText;
        var totalpatten = /^(\d){5}(\s\d{5})*$/                  // 匹配全局
        var singlePattern = /\d{5}/g;                            // 匹配五位数字
        var containArr = []
        if (totalpatten.test(value)) {
          var valueArr = value.match(singlePattern);              // 获取数组
          for (var item of valueArr) {                            // 过滤五位数字中有重复的 
            var newArr = item.split("");
            if ([...new Set(newArr)].length != 5) {               // 一组数字中，有重复的，则中断循环
              this.numberText = "";
              return console.log("五位数字中不能有重复！");
            } else {
              containArr.push(item.split("").sort(function(a, b) {return a - b;}).join(""));    // 数组排序
            }
          }
          var resultArr = [...new Set(containArr)];       // 数组去重
          console.log(`textarea里面有${resultArr.length}组不同的数字`);
          this.numberText = "";
        } else {
          console.log('请输入数字，每5位数字以一个空格隔开');
          this.numberText = "";
        }
      }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}


</style>
