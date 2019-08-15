<template>
  <div class="head-nav">
    <ul class="nav">
      <li>
        <a href="#">币币交易</a>
      </li>
      <li>
        <a href="#">行情列表</a>
      </li>
      <li>
        <a href="#" style="color:#fbb32a;">Newpos</a>
      </li>
      <li>
      <a href="#">委托账户</a>
      </li>
      <li>
        <div class="dropdown">
              <button class="dropbtn">活动中心</button>
                    <div class="dropdown-content">
                            <a href="https://newdex.vip/events/anniversary">周年礼献</a>
                            <a href="https://newdex.vip/events/treasure-hunt">密钥寻宝</a>
                            <a href="#">Newdex大使 </a>
                            <a href="https://newdex.vip/lucky-draw">每日抽奖</a>
                            <a href="https://newdex.vip/candy-airdrop/">糖果空投</a>
                      </div>
                            
          </div>
        
      </li>
    </ul>
    <ul class="nav1">
      <li>
        <a href="#">简体中文</a>
      </li>
      <li>
        <a href="#">APP下载</a>
      </li>
      <li>
        <a href="#">订单</a>
      </li>
      <li>
        <a href="#">退出</a>
      </li>
      <li>
        <a href="#">切换</a>
      </li>
      <li>
        <a href="#">littlecandy1</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Header",
  data: {}
};
</script>

<style lang="scss">

.head-nav {
  width: 100%;
  height: 60px;
  background: #161930;
  min-width: 1200px;
}
a{color:#fff;text-decoration:none}
.nav li{float:left; text-align :center;line-height: 60px; height:60px;}
.nav1 li{float:right;line-height: 60px;height:60px;}
.nav li a{ display:block;  line-height:60px; padding: 0 10px;  color:#fff ;text-align: center;}
.nav1 li a{ display:block;  line-height:60px; padding: 0 10px;  color: #FFF;}
/* 下拉按钮样式 */
.dropbtn {
    background: none;
    color: #fbb32a;
    font-size: 15px;
    border: none;
    cursor: pointer;//	光标呈现为指示链接的指针（一只手）
}
/* 容器 <div> - 需要定位下拉内容 */
.dropdown {
    position: relative;
    display: inline-block;//	行内块元素。
}

/* 下拉内容 (默认隐藏) */

.dropdown-content {
    display: none;
    position: absolute;
    background-color: #f9f9f9;
    width: 110px;
    height:200px;
    border-radius: 4px;
    padding:5px 2px;
    
}
.nav li .dropdown-content a {
  color: #000;
  line-height: 40px;

}
/* 在鼠标移上去后显示下拉菜单 */
.dropdown:hover .dropdown-content {
    display: block;
}
/* 鼠标移上去后修改下拉菜单链接颜色 */
.nav li .dropdown-content a:hover {
  background-color: rgb(0, 110, 255);
  color: #fff;
}


</style>
