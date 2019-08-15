<template>
  <div>
    <footer>
      <div class="bg">
        <div class="bg1">
          <div class="bg11">
            <a
              href="https://newdex.zendesk.com/hc/zh-cn/categories/360000803611-%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98"
            >常见问题</a>
            <a href="#">公告中心</a>
            <a href="#">费率说明</a>
            <a href="#">提交工具</a>
          </div>
          <div class="bg12">
            <a href="#">市场有风险，投资需谨慎</a>
          </div>
        </div>
      
        <div class="bg2">
          <div class="bg21">
            <a>Copyright © 2018 Newdex Inc. All rights reserved.</a>
          </div>
          <div class="bg22">
            <a>24H成交额：44700.1458 EOS 2118.86 USDⓈ GBI：13562.86 EOS: ¥ 30.88</a>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: "Footer",
  data: {}
};
</script>

<style lang="scss">
.bg {
  width: 100%;
  height: 110px;
  background: #161930;
  color: #fff;
}
.bg1 {
  width: 100%;
  height: 50px;
  line-height: 50px;
  margin: 0;
  padding: 0;
  text-align: center;
  float: left;
}
.bg2 {
  width: 100%;
  height: 60px;
  margin: 0;
  padding: 0;
  text-align: center;
  float: right;
  border-top: 0.5px solid #f3f3f3;//设置实线
  
}
.bg11 {
  width: 50%;
  float: left;
  line-height: 50px;
}
.bg12 {
  width: 50%;
  float: right;
  height: 50px;
  line-height: 50px;
}
.bg12 a{float:right;
     padding:0 110px}
.bg21 {
  width: 50%;
  float: left;
  height: 60px;
  line-height:60px;
  padding:0  10px;
  box-sizing: border-box; 
}
.bg22 {
  width: 50%;
  float: left;
  height: 60px;
  line-height:60px;
}
.bg .bg1 .bg12 .iconfont {
  font-size: 15px;
}
.bg11 a{padding: 0 10px;}
</style>
