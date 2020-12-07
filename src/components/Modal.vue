<template>
  <transition name="slide">
    <div class="modal" v-show="showModal">
      <div class="mask"></div>
      <div class="modal-dialog">
        <div class="modal-header">
          <span>{{title}}</span>
          <a href="javascript:;" class="icon-close" v-on:click="$emit('cancel')"></a>
        </div>
        <div class="modal-body">
          <slot name="body"></slot>
        </div>
        <div class="modal-footer">
            <a href="javascript:;" class="btn" v-if="btnType==1" v-on:click="$emit('submit')">{{sureText}}</a>
            <a href="javascript:;" class="btn" v-if="btnType==2" v-on:click="$emit('cancel')">{{cancelText}}</a>
          <div class="btn-group" v-if="btnType==3">
            <a href="javascript:;" class="btn" v-on:click="$emit('submit')">{{sureText}}</a>
            <a href="javascript:;" class="btn" v-on:click="$emit('cancel')">{{cancelText}}</a>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: "modal",
  props: {
    modalType: {
      //弹框:小small、中middle、大large、表单form
      type: String,
      default: "from"
    },
    //弹框标题
    title: String,
    //按钮类型：1:确定按钮 2：取消按钮 3：确定取消
    btnType: String,
    sureText: {
      type: String,
      default: "确定"
    },
    cancelText: {
      type: String,
      default: "取消"
    },
    showModal: Boolean
  }
};
</script>

<style lang="less">
.modal {
  z-index: 10;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  transition: all .5s;
  .mask {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: #000000;
    opacity: 0.5;
  }
  &.slide-enter-active{
      top: 0;
  }
  &.slide-leave-active{
      top: -100%;
  }
  &.slide-enter{
      top: -100%;
  }
  .modal-dialog {
    position: absolute;
    top: 40%;
    left: 50%;
    width: 660px;
    height: auto;
    background-color: #ffffff;
    transform: translate(-50%, -50%);
    .modal-header {
      height: 60px;
      background-color: #f5f5f5;
      padding: 0 25px;
      line-height: 60px;
      font-size: 16px;
      .icon-close {
        position: absolute;
        top: 23px;
        right: 25px;
        width: 14px;
        height: 14px;
        background: url("/imgs/icon-close.png") no-repeat center;
        background-size: contain;
        transition: transform 0.3s;
        &:hover {
          transform: scale(1.5);
        }
      }
    }
    .modal-body {
      padding: 42px 40px 54px;
      font-size: 14px;
    }
    .modal-footer {
      height: 82px;
      line-height: 82px;
      text-align: center;
      background-color: #f5f5f5;
      .btn{
        display: inline-block;
        width: 110px;
        height: 30px;
        line-height: 30px;
        text-align: center;
        background-color: #ff6600;
        color: #ffffff;
        border: none;
        margin-right: 20px;
      }
      .btn-group {
        .btn {
          &:last-child {
            margin-right: 0;
          }
        }
      }
      .btn-default {
        background-color: #b0b0b0;
        color: #ffffff;
        // border: 1px solid #d7d7d7;
      }
      .btn-large {
        width: 202px;
        height: 50px;
        line-height: 50px;
        font-size: 18px;
      }
      .btn-huge {
        width: 300px;
        height: 54px;
        line-height: 54px;
        font-size: 16px;
      }
    }
  }
}
</style>