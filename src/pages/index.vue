<template>
  <div class="index">
    <div class="container">
      <div class="swiper-box">
        <div class="nav-menu">
          <ul class="menu-wrap">
            <li class="menu-item">
              <a href="javascript:;">手机 电话卡</a>
              <div class="children">
                <ul v-for="(item,index) in menuList" v-bind:key="index">
                  <li v-for="(sub,j) in item" v-bind:key="j">
                    <a v-bind:href="sub?'/#/product/'+sub.id:''">
                      <img
                        v-bind:src="sub?sub.img:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/0cadc8b00dbe3b5615bd6ab657715baf.png?thumb=1&w=40&h=40&f=webp&q=90'"
                        alt
                      />
                      {{sub?sub.name:'小米9'}}
                    </a>
                  </li>
                </ul>
              </div>
            </li>
            <li class="menu-item">
              <a href="javascript:;">电视 盒子</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">笔记本 显示器 平板</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">家电 插线板</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">出行 穿戴</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">智能 路由器</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">电源 配件</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">健康 儿童</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">耳机 音响</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">生活 箱包</a>
            </li>
          </ul>
        </div>
        <swiper v-bind:options="swiperOption">
          <swiper-slide v-for="(item,index) in slideList" v-bind:key="index">
            <a v-bind:href="'/#/product/'+item.id">
              <img v-bind:src="item.img" />
            </a>
          </swiper-slide>
          <div class="swiper-pagination" slot="pagination"></div>
          <div class="swiper-button-prev" slot="button-prev"></div>
          <div class="swiper-button-next" slot="button-next"></div>
        </swiper>
      </div>
      <div class="ads-box">
        <a v-bind:href="'/#/product/'+item.id" v-for="(item,index) in adsList" v-bind:key="index">
          <img v-lazy="item.img" alt />
        </a>
      </div>
      <div class="banner">
        <a href="/#/product/30">
          <img style="width:100%;height:100%" v-lazy="'/imgs/banner-1.png'" alt />
        </a>
      </div>
      <div class="product-box">
        <div class="container">
          <h2>手机</h2>
          <div class="wrapper">
            <div class="banner-left">
              <a href="/#/product/35">
                <img v-lazy="'/imgs/mix-alpha.jpg'" alt />
              </a>
            </div>
            <div class="list-box">
              <div class="list" v-for="(arr,i) in phoneList" v-bind:key="i">
                <div class="item" v-for="(item,j) in arr" v-bind:key="j">
                  <span v-bind:class="{'new-pro':j%2==0}">新品</span>
                  <div class="item-img">
                    <img v-lazy="item.mainImage" alt />
                  </div>
                  <div class="item-info">
                    <h3>{{item.name}}</h3>
                    <p>{{item.subtitle}}</p>
                    <p class="price" @click="addCart(item.id)">{{item.price}}元</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <service-bar></service-bar>
    <modal
      title="提示"
      sureText="查看购物车"
      btnType="1"
      modalType="middle"
      :showModal="showModal"
      @submit="goToCart"
      v-on:submit="goToCart"
      v-on:cancel="showModal=false"
    >
      <template v-slot:body>
        <p>商品添加成功！</p>
      </template>
    </modal>
  </div>
</template>

<script>
import ServiceBar from "./../components/ServiceBar";
import Modal from "../components/Modal";
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import "swiper/css/swiper.css";

export default {
  name: "index",
  components: {
    Swiper,
    SwiperSlide,
    ServiceBar,
    Modal
  },
  data() {
    return {
      showModal: false,
      swiperOption: {
        autoplay: true, //自动播放
        loop: true, //一直循环
        effect: "cube", //指定动画
        cubeEffect: {
          slideShadows: true,
          shadow: true,
          shadowOffset: 100,
          shadowScale: 0.6
        },
        pagination: {
          //分页
          el: ".swiper-pagination",
          clickable: true
        },
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev"
        }
      },
      slideList: [
        {
          id: "42",
          img: "/imgs/slider/slide-1.jpg"
        },
        {
          id: "45",
          img: "/imgs/slider/slide-2.jpg"
        },
        {
          id: "46",
          img: "/imgs/slider/slide-3.jpg"
        },
        {
          id: "",
          img: "/imgs/slider/slide-4.jpg"
        },
        {
          id: "",
          img: "/imgs/slider/slide-5.jpg"
        }
      ],
      menuList: [
        [
          {
            id: "",
            img:
              "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/0cadc8b00dbe3b5615bd6ab657715baf.png?thumb=1&w=40&h=40&f=webp&q=90",
            name: "Redmi 9"
          },
          {
            id: "",
            img:
              "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/afa28e7477639537f556eb46e3ca5f43.jpeg?thumb=1&w=40&h=40&f=webp&q=90",
            name: "Redmi 10X 4G"
          },
          {
            id: "",
            img:
              "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/d12361002299529816e7e0a6b74e0a25.jpg?thumb=1&w=40&h=40&f=webp&q=90",
            name: "Redmi 10X 5G 系列"
          },
          {
            id: "",
            img:
              "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/0cadc8b00dbe3b5615bd6ab657715baf.png?thumb=1&w=40&h=40&f=webp&q=90",
            name: "Redmi 9"
          }
        ],
        [0, 0, 0, 0],
        [0, 0, 0, 0],
        [0, 0, 0, 0],
        [0, 0, 0, 0],
        [0, 0, 0, 0]
      ],
      adsList: [
        {
          id: 33,
          img: "/imgs/ads/ads-1.png"
        },
        {
          id: 48,
          img: "/imgs/ads/ads-2.jpg"
        },
        {
          id: 45,
          img: "/imgs/ads/ads-3.png"
        },
        {
          id: 47,
          img: "/imgs/ads/ads-4.jpg"
        }
      ],
      phoneList: []
    };
  },
  mounted() {
    this.init();
  },
  methods: {
    init() {
      this.axios
        .get("/products", {
          params: {
            categoryId: 100012,
            pageSize: 14
          }
        })
        .then(res => {
          res.list = res.list.slice(6, 14);
          this.phoneList = [res.list.slice(0, 4), res.list.slice(4, 8)];
        });
    },
    addCart(id) {
      // console.log(1);
      this.axios
        .post("/carts", {
          productId: id,
          selected: true
        })
        .then((res) => {
          this.showModal = true;
          this.$store.dispatch("saveCartCout", res.cartTotalQuantity);
        })
        .catch(() => {
          this.showModal = true;
        });
    },
    goToCart() {
      this.$router.push("/cart");
    }
  }
};
</script>

<style lang="less">
.index {
  width: 1226px;
  min-width: 1226px;
  margin: 0 auto;
  .container {
    .swiper-box {
      height: 100%;
      .nav-menu {
        height: 460px;
        position: absolute;
        width: 264px;
        z-index: 9;
        padding: 2px 0;
        font-size: 14px;
        background: rgba(105, 101, 101, 0.6);
        box-sizing: border-box;
        .menu-wrap {
          padding-left: 0;
          .menu-item {
            height: 43px;
            line-height: 42px;
            a {
              position: relative;
              display: block;
              color: #ffffff;
              padding-left: 40px;
              &:after {
                position: absolute;
                right: 30px;
                top: 15px;
                content: "";
                display: inline-block;
                width: 10px;
                height: 15px;
                background: url("/imgs/icon-arrow.png") no-repeat center;
                background-size: contain;
              }
            }
            &:hover {
              background-color: #ff6600;
              .children {
                display: block;
              }
            }
            .children {
              display: none;
              width: 962px;
              height: 458px;
              background-color: #ffffff;
              position: absolute;
              top: 0;
              left: 264px;
              border: 1px solid #e5e5e5;
              ul {
                display: flex;
                justify-content: space-between;
                height: 75px;
                li {
                  height: 75px;
                  line-height: 75px;
                  flex: 1;
                  // padding-left: 23px;
                }
                a {
                  color: #333333;
                  font-size: 14px;
                }
                img {
                  vertical-align: middle;
                  margin-right: 15px;
                }
              }
            }
          }
        }
      }
      .swiper-container {
        height: 100%;
        .swiper-button-prev {
          left: 274px;
        }
        img {
          width: 100%;
          height: 100%;
        }
      }
    }
    .ads-box {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 10px;
      margin-bottom: 31px;
      // align-items: ;
      a {
        width: 296px;
        height: 167px;
        img {
          width: 100%;
          height: 100%;
        }
      }
    }
    .banner {
      margin-bottom: 50px;
    }
    .product-box {
      // background-color: #f5f5f5;
      padding: 30px 0 50px;
      h2 {
        font-size: 22px;
        height: 21px;
        line-height: 21px;
        color: #333333;
        margin-bottom: 20px;
      }
      .wrapper {
        display: flex;
        .banner-left {
          margin-right: 16px;
          img {
            width: 224px;
            height: 619px;
          }
        }
        .list-box {
          .list {
            display: flex;
            justify-content: space-between;
            align-items: center;
            width: 986px;
            margin-bottom: 14px;
            &:last-child {
              margin-bottom: 0;
            }
            .item {
              width: 236px;
              height: 302px;
              background-color: #ffffff;
              text-align: center;
              span {
                display: inline-block;
                width: 67px;
                height: 24px;
                font-size: 14px;
                line-height: 24px;
                color: #ffffff;
                &.new-pro {
                  background-color: #7ecf68;
                }
                &.kill-pro {
                  background-color: #e82626;
                }
              }
              .item-img {
                img {
                  width: 100%;
                  height: 160px;
                }
              }
              .item-info {
                h3 {
                  font-size: 14px;
                  color: #333333;
                  line-height: 14px;
                  font-weight: bold;
                }
                p {
                  color: #999999;
                  line-height: 13px;
                  margin: 6px auto 13px;
                }
                .price {
                  color: #f20a0a;
                  font-size: 14px;
                  font-weight: bold;
                  cursor: pointer;
                  &:after {
                    display: inline-block;
                    width: 22px;
                    height: 22px;
                    background: url("/imgs/icon-cart-hover.png") no-repeat
                      center;
                    background-size: 22px;
                    content: "";
                    margin-left: 5px;
                    vertical-align: middle;
                  }
                }
              }
            }
          }
        }
      }
    }
  }
}
</style>