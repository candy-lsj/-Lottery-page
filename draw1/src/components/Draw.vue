<template>
  <div>
    <div class="content">
      <div class="draw-picture">
        <img src="https://s-dapp.340wan.com/static/img/title.757674d.png" />
      </div>
      <div class="scroll"  >
        <marquee direction="up" scrollamount="3" scrolldelay="100" >
         
            <div class="scroll-result" v-html="mode"></div>
        </marquee>
      </div>
      <div class="draw-box">
        <div class="draw-table">
          <div class="table-head">
            <span>幸运号码</span>
            <span>奖励</span>
          </div>

          <div
            class="table-row"
            v-for="(item, index) in rewardRulers"
            :key="index"
            :class="{'selected-row': selected == index+1, 'table-row-last':index==rewardRulers.length-1,
          }"
          >
            <span>
              {{item.from}}
              <template v-if="item.from < 10000">-{{item.to}}</template>
            </span>
            <span>
              {{item.award}}
              <a href="###" v-if="index==rewardRulers.length-1">大奖记录</a>
            </span>
          </div>
        </div>

        <!-- 开始抽奖 -->
        <div class="draw-result" v-html="result"></div>
        <a class="draw-lottery" href="###" @click="drawClick">{{ buttonText }}</a>
      </div>

      <div class="upgrade">
        <div class="upgrade1">
          <div class="upgrade11">
            <a href="#">{{myname}}</a>
          </div>
          <div class="upgrade12">
            <a href="#">您是初级会员，请先升级会员</a>
          </div>
        </div>
        <div class="upgrade2">
          <div class="upgrade21">
            <a>升级会员，每日最多尊享10次机会</a>
          </div>
          <div class="upgrade22">
            <input
              type="button"
              value="升级"
              onclick=" window.location.href='https://newdex.vip/member'"
            />
          </div>
        </div>
      </div>

      <div class="explanation">
        <div class="activeExplanation">活动说明</div>

        <div class="explanItem">
          <div class="rule">1.抽取幸运号码，根据号码获得对应奖励。</div>
          <div class="rule">2.Newdex会员≥VIP1级拥有抽奖资格，每提升1级会员，每日抽奖次数增加1次，每日上限10次。</div>
          <div class="rule">3.抽奖次数当日有效，不可累加。</div>
        </div>
      </div>
    </div>
  </div>
</template>



<script>
import { ftruncate } from "fs";
export default {
  name: "Draw",
  data() {
    return {
      randing: false,
      round: 0,
      selected: 0,
      buttonText: "开始抽奖(10次)",
      mode:"",
      result: "",
      times: 10,
      reward: "",
      myname:"littlecandy11",
      rewardRulers: [
        { from: 0, to: 9885, award: "0.0003 EOS" },
        { from: 9886, to: 9985, award: "0.0030 EOS" },
        { from: 9986, to: 9993, award: "0.0300 EOS" },
        { from: 9994, to: 9997, award: "0.3000 EOS" },
        { from: 9998, to: 9999, award: "3.0000 EOS" },
        { from: 10000, to: 10000, award: "30.0000 EOS " }
      ]
    };
  },
  methods: {
    drawClick() {
      if (this.randing) {
        return;
      }//用于防止连续点击，最开始点就为真，最后运行完为假，才可以继续点击。
      if (this.times == 0) {
        alert("次数不够了");
        return;
      }
      this.times--;
      this.randing = true;
      this.round = 0;   //计数清零
      this.selected = 0;//清空，不选择表格

      this.randomNumbers();
      
      this.timer = setInterval(() => {
        this.randomNumbers();
      }, 100);   //每隔100ms跳转一次
    },
    //生成一个随机数，Math.random()表示随机0~1的数
    randomNumbers() {
      this.round++;
      var randNum = Math.floor(Math.random() * 10001);
      if (this.round == 10) {
        clearInterval(this.timer);
        this.randResult(randNum);//返回结果
        return;
      }
      this.buttonText = randNum.toString();//返回字符串
    },
    randResult(randNum) {
     this.randing = false; 

     var reward = '';
      if (randNum <= 9885) {
        this.selected = 1;
        reward = 0.0003;
      } else if (randNum <= 9985) {
        this.selected = 2;
        reward = 0.003;
      } else if (randNum <= 9993) {
        this.selected = 3;
        reward = 0.03;
      } else if (randNum <= 9997) {
        this.selected = 4;
        reward = 0.3;
      } else if (randNum <= 9985) {
        this.selected = 5;
        reward = 3.0;
      } else if (randNum <= 9999) {
        this.selected = 6;
        reward = 30.0;
      }
      
      this.result = `本次开奖号码：<span class="red">${randNum}</span>，获得奖励<span class="red">${reward}</span>EOS`;
      this.buttonText = `开始抽奖(${this.times}次)`;
      this.mode = `${this.myname}抽中${reward}EOS`;
    }
    


  }
};
</script>




<!-- Add "scoped" attribute to limit CSS to this component only -->

<style lang="scss">
//设置成全局模式，不然vue只对本页面有效

.red {
  color: red;
}
</style>

<style scoped lang="scss">
//设置输出本次抽奖号码
.draw-result {
  font-size: 20px;
  color: #fff;
  height: 20px;
  margin-top: 15px;
}

.content {
  width: 100%;
  height: 1300px;

  background-image: linear-gradient(180deg, #3248ca 0, #0c186d) !important;
}

//每日幸运抽奖
.draw-picture {
  padding-top: 30px;
  height: 70px;
}
.draw-picture img {
  height: 65px;
  width: 456px;
  margin: 0 auto;
}

//表格设置，幸运号码，no-repeat背景图只显示一次，不重复。auto(自动/默认)
.draw-box {
  width: 750px;
  height: 568px;
  background: url(/images/bg.png) no-repeat; 
  background-size: 100% auto;
  margin: 0 auto;
  padding: 30px;
  box-sizing: border-box;
}


.draw-table {
  background-color: #fff;
  height: 370px;
  border-radius: 8px;
  overflow: hidden; //超过部分隐藏
}

.draw-table .table-head {
  height: 58px;
  background-color: #e9f2ff;
  overflow: hidden;
  clear: both;
}
//设置表格第一行
.draw-table .table-head span {
  display: block;
  float: left;
  width: 50%;
  height: 100%;
  text-align: center;
  line-height: 58px;
  box-sizing: border-box; //合模式，高宽算在一起。
}
//表格中间
.draw-table .table-row {
  clear: both;
  height: 50px;
}
//表格最后一行

// .draw-table .table-row-last span {
//   display: block;
//   float: left;
//   width: 50%;
//   height: 100%;
//   text-align: center;
//   line-height: 60px;
//   box-sizing: border-box; //合模式，高宽算在一起。
// }
.draw-table .table-row-last span {
  line-height: 60px;
  height: 60px;
}
.draw-table .table-row-last span:last-child {
  line-height: 20px;
  padding: 10px 0;
}
.draw-table .table-row-last a {
  display: block;
  color: #f6c85c;
  font-size: 12px;
}
//设置表格内容位置
.draw-table .table-row span {
  display: block;
  float: left;
  width: 50%;
  height: 100%;
  text-align: center;
  line-height: 50px;
  box-sizing: border-box; //合模式，高宽算在一起。
}

//设置表格边框
.draw-table .table-head span:first-child {
  border-right: #f3f3f3 1px solid;
}
.draw-table .table-row span {
  border-right: 1px solid #f3f3f3;
  border-top: 1px solid #f3f3f3;
}

.draw-table .selected-row {
  border: 1px solid #f6c85c;
  box-shadow: inset 0 0 8px rgba(169, 105, 0, 0.43);
}
//开始抽奖
.draw-lottery {
  display: block;//	此元素将显示为块级元素
  width: 370px;
  height: 64px;
  background: #f3ed39;
  margin: 30px auto;
  box-sizing: border-box;
  border-radius: 8px;
  color: #000;
  text-align: center;
  padding: 20px;
  font-size: 20px;
}
.draw-lottery:hover {
  background-color: orange;
}

//滚动窗口
.scroll {
  height: 80px;
  width: 400px;
  margin: auto;
  text-align: center;
  

}
.scroll-result {
  font-size: 20px;
  color:yellow;
  height: 50px;
  text-align: center;
  line-height: 50px;
}

//升级
.upgrade {
  width: 760px;
  height: 166px;
  color: #fff;
  margin: auto;
  margin-top: 15px;
  padding: 12px 25px;
  border-radius: 8px;
  font-size: 18px;
  box-shadow: inset 0 0 1.1rem hsla(0, 0%, 100%, 0.2); //给div元素添加阴影
  box-sizing: border-box;
}
.upgrade1 {
  width: 100%;
  height: 70px;
  margin: 0;
  padding: 0;
  color: #fff;
  text-align: center;
  border-bottom: 1px dashed hsla(0, 0%, 100%, 0.46); //定义虚线
}
.upgrade2 {
  width: 100%;
  height: 70px;
  margin: 0;
  color: #fff;

  line-height: 70px;
}
.upgrade11 {
  width: 50%;
  float: left;
  height: 70px;
  line-height: 70px;
  text-align: left;
}
.upgrade21 {
  width: 50%;
  float: left;
  height: 70px;
  line-height: 70px;
  text-align: left;
}

.upgrade .upgrade1 .upgrade12 .iconfont {
  font-size: 15px;
}
.upgrade12 {
  width: 50%;
  float: right;
  height: 70px;
  line-height: 70px;
  margin: 0;
  color: #f6c85c;
}
.upgrade12 a {
  margin: 0 30px 0 0;
  float: right;
}
.upgrade22 {
  width: 50%;
  float: left;
  height: 70px;
  line-height: 70px;
}
.upgrade22 input {
  background: rgb(243, 237, 57);
  color: #23309f;
  height: 40px;

  width: 112px;
  border-radius: 8px;
  float: right;
  padding: 0;
  margin: 15px 30px 0 0;
  border: 0px;
}

//活动说明

.explanation {
  width: 760px;
  height: 200px;
  color: #fff;
  text-align: left;
  margin: auto;
  margin-top: 15px;
}
.activeExplanation {
  font-size: 17px;
}
.explanItem {
  margin-top: 15px;
  font-size: 16px;
}

.rule {
  margin-top: 6.4px;
}
</style>
