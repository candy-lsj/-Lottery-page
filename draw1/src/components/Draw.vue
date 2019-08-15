<template>
  <div>
    <div class="content">
      <div class="draw-picture">
        <img src="https://s-dapp.340wan.com/static/img/title.757674d.png" />
      </div>
      <div class="scroll">
        <marquee direction="up" scrollamount="3" scrolldelay="100">滚动内容</marquee>
      </div>
      <div class="draw-box">
        <div class="draw-table">
          <div class="table-head">
            <span>幸运号码</span>
            <span>奖励</span>
          </div>
          <div class="table-row" :class="{'selected-row': selected == 1}">
            <span>0-9885</span>
            <span>0.0003 EOS</span>
          </div>
          <div class="table-row" :class="{'selected-row': selected == 2}">
            <span>9886-9985</span>
            <span>0.0030 EOS</span>
          </div>
          <div class="table-row" :class="{'selected-row': selected == 3}">
            <span>9986-9993</span>
            <span>0.0300 EOS</span>
          </div>
          <div class="table-row" :class="{'selected-row': selected == 4}">
            <span>9994-9997</span>
            <span>0.3000 EOS</span>
          </div>
          <div class="table-row" :class="{'selected-row': selected == 5}">
            <span>9998-9999</span>
            <span>3.0000 EOS</span>
          </div>
          <div class="table-row-last" :class="{'selected-row': selected == 6}">
            <span>10000</span>
            
                <div class="record1">30.0000 EOS </div>
                 <div class="record2">大奖记录</div>
          
          </div>
        </div>

        <!-- 开始抽奖 -->
        <div class="draw-result" v-html="result"></div>
        <a class="draw-lottery" href="###" @click="drawClick">{{ buttonText }}</a>
      </div>

      <div class="upgrade">
        <div class="upgrade1">
          <div class="upgrade11">
            <a href="#">littlecandy1</a>
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
import { ftruncate } from 'fs';
export default {
  name: "Draw",
  data() {
    return {
      selected: 0,
      buttonText: "开始抽奖(10次)",
      result: "",
      times: 10,
      reward: "",
      
    };
  },
  methods: {
    drawClick() {
      if (this.times == 0) {
        alert("次数不够了");
        return;
      }
      this.times--;
      //生成一个随机数，Math.random()表示随机0~1的数
     var randNum = Math.floor(Math.random() * 10001);
    
      //草稿
      var reward = "";
      if (randNum <= 9885) {
        this.selected = 1;
        reward = 0.0003;
      } else if (randNum <= 9985) {
        this.selected = 2;
        reward = 0.0030;
      } else if (randNum <= 9993) {
        this.selected = 3;
        reward = 0.0300;
      } else if (randNum <= 9997) {
        this.selected = 4;
        reward = 0.3000;
      } else if (randNum <= 9985) {
        this.selected = 5;
        reward = 3.00000;
      } else if (randNum <= 9999) {
        this.selected = 6;
        reward = 30.0000;
      }

      this.result = `本次开奖号码：<span class="red">${randNum}</span>，获得奖励<span class="red">${reward}</span>EOS`;
      this.buttonText = `开始抽奖(${this.times}次)`;
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
  height: 120px;
}
.draw-picture img {
  height: 65px;
  width: 456px;
  margin: 0 auto;
}

//表格设置，幸运号码
.draw-box {
  width: 750px;
  height: 568px;
  background: url(/images/bg.png) no-repeat;
  background-size: 100% auto;
  margin: 0 auto;
  padding: 30px;
  box-sizing: border-box;
}

.draw-lottery {
  display: block;
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

.draw-table .table-row-last span {
  display: block;
  float: left;
  width: 50%;
  height: 100%;
  text-align: center;
  line-height: 60px;
  box-sizing: border-box; //合模式，高宽算在一起。
}
.table-row-last .record{width:50%;height:30px;}
.table-row-last .record2{color:#f6c85c;height:30px;}
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

//滚动窗口
.scroll {
  height: 50px;
  width: 100px;
  margin: auto;
  color: #fff;
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
  margin: 0  ;
  color: #f6c85c;
}
.upgrade12 a{margin:0 30px 0 0;float:right}
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
  padding:  0;
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
