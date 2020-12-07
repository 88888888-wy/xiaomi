<template>
  <div class="footer">
    <div class="footer-logo">
      <img src="/imgs/logo-footer.png" alt />
      <p>小米商城</p>
    </div>
    <div class="footer-link">
      <a href="https://www.imooc.com/u/1343480" target="_blank">MIUI</a>
      <span>|</span>
      <a href="https://coding.imooc.com/class/113.html" target="_blank">米家</a>
      <span>|</span>
      <a href="https://coding.imooc.com/class/236.html" target="_blank">米聊</a>
      <span>|</span>
      <a href="https://coding.imooc.com/class/343.html" target="_blank">多看</a>
      <span>|</span>
      <a href="https://www.bilibili.com/">游戏</a>
      <span>|</span>
      <a href="https://www.huya.com/?ptag=gouzai&rso=huya_h5_395">政企服务</a>
      <span>|</span>
      <a href="https://fanyi.baidu.com/">小米天猫店</a>
      <span>|</span>
      <a href="https://www.bootcss.com/">小米集团隐私政策</a>
      <span>|</span>
      <a href="https://www.webpackjs.com/">小米公司儿童信息保护规则</a>
      <span>|</span>
      <a href="https://cn.vuejs.org/">小米商城隐私政策</a>
      <span>|</span>
      <a href="https://github.com/">小米商城用户协议</a>
      <span>|</span>
      <a href="http://nodejs.cn/api/path.html#path_path_join_paths">问题反馈</a>
      <span>|</span>
      <a href="https://www.iconfont.cn/">Select Location</a>
    </div>
    <div class="copyright">
      © mi.com
      <span class="domain">京ICP证110507号</span> 京ICP备10046444号 京公网安备11010802020134号 京网文[2020]0276-042号
    </div>
  </div>
</template>

<script>
export default {
  name: "nav-footer"
};
</script>

<style lang="less">
.footer {
  height: 234px;
  border-top: 4px solid #ff6600;
  background-color: #333333;
  color: #999999;
  font-size: 16px;
  text-align: center;
  .footer-logo {
    margin-top: 30px;
    margin-bottom: 30px;
    img {
      width: 53px;
      height: 36px;
      margin-bottom: 13px;
    }
  }
  .footer-link {
    margin-bottom: 13px;
    a {
      color: #999999;
      display: inline-block;
      font: 14px/1.5 Helvetica Neue, Helvetica, Arial, Microsoft Yahei,
        Hiragino Sans GB, Heiti SC, WenQuanYi Micro Hei, sans-serif;
    }
    span {
      margin: 0 10px;
    }
  }
  .copyright {
    .domain {
      color: #000000;
    }
  }
}

a {
  text-decoration: none;
}
</style>