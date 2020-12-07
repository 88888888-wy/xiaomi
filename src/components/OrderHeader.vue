<template>
  <div class="order-header">
    <div class="container clearfix">
      <div class="header-logo">
        <a href="/#/index"></a>
      </div>
      <div class="title">
        <h2>
          {{title}}
          <slot name="tip"></slot>
        </h2>
      </div>
      <div class="username">
        <a href="javascript:;">{{username}}</a>
      </div>
    </div>
  </div>
</template>

<script>
import {mapState} from 'vuex'
export default {
  name: "order-header",
  props:{
      title:String
  },
  computed:{
      ...mapState(['username','cartCount'])
  }
};
</script>

<style lang="less">
.order-header {
  padding: 30px 0;
  .container {
    .header-logo {
      float: left;
    }
    .header-logo {
      display: inline-block;
      width: 55px;
      height: 55px;
      background-color: #ff6600;
      a {
        text-decoration: none;
        display: inline-block;
        width: 110px;
        height: 55px;
        &:before {
          content: "";
          display: inline-block;
          width: 55px;
          height: 55px;
          background: url("/imgs/mi-logo.png") no-repeat center;
          background-size: 55px;
          transition: margin 0.2s;
        }
        &:after {
          content: "";
          display: inline-block;
          width: 55px;
          height: 55px;
          background: url("/imgs/mi-home.png") no-repeat center;
          background-size: 55px;
        }
        &:hover:before {
          margin-left: -55px;
          transition: margin 0.2s;
        }
      }
    }
    .title,
    .username {
      display: inline-block;
      height: 55px;
      line-height: 55px;
    }
    .title {
      font-size: 28px;
      color: #333333;
      margin-left: 54px;
      h2 {
          margin-top: 0;
        span {
          font-size: 14px;
          margin-left: 17px;
          color: #999999;
        }
      }
    }
    .username{
        float: right;
        a{
            color: #666666;
            font-size: 16px;
        }
    }
  }
}
</style>