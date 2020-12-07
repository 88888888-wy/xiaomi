<template>
  <div class="service">
    <div class="container">
      <ul>
        <li>
          <span class="icon-setting"></span>预约维修服务
        </li>
        <li>
          <span class="icon-7day"></span>7天无理由退货
        </li>
        <li>
          <span class="icon-15day"></span>15天免费换货
        </li>
        <li>
          <span class="icon-post"></span>满99元包邮
        </li>
        <li>
          <span class="icon-loc"></span>520余家售后网点
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "service-bar"
};
</script>

<style lang="less">
.service {
  height: 36px;
  padding-left: 33px 0;
  color: #666666;
  font-size: 16px;
  .container {
    height: 100%;
    li {
      display: inline-block;
      width: 19.2%;
      text-align: center;
      border-right: 1px solid #e5e5e5;
      &:last-child {
        border: none;
      }
      span {
        display: inline-block;
        width: 20px;
        height: 20px;
        vertical-align: middle;
        margin-right: 8px;
      }
      .icon-setting {
        display: inline-block;
        width: 20px;
        height: 20px;
        background: url("/imgs/icon-setting.png") no-repeat center;
        background-size: contain;
      }
      .icon-7day {
        display: inline-block;
        width: 20px;
        height: 20px;
        background: url("/imgs/icon-7day.png") no-repeat center;
        background-size: contain;
      }
      .icon-15day {
        display: inline-block;
        width: 20px;
        height: 20px;
        background: url("/imgs/icon-15day.png") no-repeat center;
        background-size: contain;
      }
      .icon-post {
        display: inline-block;
        width: 20px;
        height: 20px;
        background: url("/imgs/icon-post.png") no-repeat center;
        background-size: contain;
      }
      .icon-loc {
        display: inline-block;
        width: 20px;
        height: 20px;
        background: url("/imgs/icon-loc.png") no-repeat center;
        background-size: contain;
      }
    }
  }
}
</style>