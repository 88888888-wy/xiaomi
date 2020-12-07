<template>
  <div class="header">
    <div class="nav-topbar">
      <div class="container">
        <div class="topbar-menu">
          <a href="javascript:;">小米商城</a>
          <a href="javascript:;">MUI</a>
          <a href="javascript:;">云服务</a>
          <a href="javascript:;">协议规则</a>
        </div>
        <div class="topbar-user">
          <a href="javascript:;" v-if="username">{{username}}</a>
          <a href="javascript:;" v-if="!username" @click="login">登录</a>
          <a href="javascript:;" v-if="username">我的订单</a>
          <a href="javascript:;" class="my-cart" @click="goToCart">
            <span class="icon-cart"></span>
            购物车({{cartCount}})
          </a>
        </div>
      </div>
    </div>
    <div class="nav-header">
      <div class="container">
        <div class="header-logo">
          <a href="/#/index"></a>
        </div>
        <div class="header-menu">
          <div class="item-menu">
            <span>小米手机</span>
            <div class="children">
              <ul>
                <li class="product" v-for="(item,index) in phoneList" :key="index">
                  <a v-bind:href="'/#/product/'+item.id" target="_blank">
                    <div class="pro-img">
                      <img v-lazy="item.mainImage" alt="item.subtitle" />
                    </div>
                    <div class="pro-name">{{item.name}}</div>
                    <div class="pro-price">{{item.price | currency}}</div>
                  </a>
                </li>
              </ul>
            </div>
          </div>
          <div class="item-menu">
            <span>RedMi红米</span>
            <div class="children">
              <ul>
                <li class="product">
                  <a href target="_blank">
                    <div class="pro-img">
                      <img
                        v-lazy="'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/cfbedb76699240a6c9a3f875b930983c.png?thumb=1&w=160&h=110&f=webp&q=90'"
                      />
                    </div>
                    <div class="pro-name">Redmi 10X 4G</div>
                    <div class="pro-price">999元起</div>
                  </a>
                </li>
                <li class="product">
                  <a href target="_blank">
                    <div class="pro-img">
                      <img
                        v-lazy="'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/6a6548361871303764d6c66142074524.png?thumb=1&w=160&h=110&f=webp&q=90'"
                      />
                    </div>
                    <div class="pro-name">Redmi 10X 5G 系列</div>
                    <div class="pro-price">1599元起</div>
                  </a>
                </li>
                <li class="product">
                  <a href target="_blank">
                    <div class="pro-img">
                      <img
                        v-lazy="'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/0203f4e7dafcc0c9016a1b48556abf30.jpg?thumb=1&w=160&h=110&f=webp&q=90'"
                      />
                    </div>
                    <div class="pro-name">Redmi K30 Pro</div>
                    <div class="pro-price">2699元起</div>
                  </a>
                </li>
                <li class="product">
                  <a href target="_blank">
                    <div class="pro-img">
                      <img
                        v-lazy="'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e95616fd1620e469386f007eeab1c763.jpg?thumb=1&w=160&h=110&f=webp&q=90'"
                      />
                    </div>
                    <div class="pro-name">Redmi K30 Pro 变焦版</div>
                    <div class="pro-price">3799元起</div>
                  </a>
                </li>
                <li class="product">
                  <a href target="_blank">
                    <div class="pro-img">
                      <img
                        v-lazy="'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/cff2977b8aab1e43b94b2f00083f4ae1.jpg?thumb=1&w=160&h=110&f=webp&q=90'"
                      />
                    </div>
                    <div class="pro-name">Redmi K30</div>
                    <div class="pro-price">1499元起</div>
                  </a>
                </li>
                <li class="product">
                  <a href target="_blank">
                    <div class="pro-img">
                      <img
                        v-lazy="'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/742a328bdaa242aea89ec2a9c8661013.jpg?thumb=1&w=160&h=110&f=webp&q=90'"
                      />
                    </div>
                    <div class="pro-name">Redmi K30 5G</div>
                    <div class="pro-price">1899元起</div>
                  </a>
                </li>
              </ul>
            </div>
          </div>
          <div class="item-menu">
            <span>电视</span>
            <div class="children">
              <ul>
                <li class="product">
                  <a href target="_blank">
                    <div class="pro-img">
                      <img
                        v-lazy="'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/0112cb7e2ea8489fbd36ce3a781d5232.jpg?thumb=1&w=160&h=110&f=webp&q=90'"
                      />
                    </div>
                    <div class="pro-name">Redmi 智能电视 MAX 98''</div>
                    <div class="pro-price">19999元</div>
                  </a>
                </li>
                <li class="product">
                  <a href target="_blank">
                    <div class="pro-img">
                      <img
                        v-lazy="'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f0f2d1079c767a834f098dd824bb6fee.png?thumb=1&w=160&h=110&f=webp&q=90'"
                      />
                    </div>
                    <div class="pro-name">小米电视4A 60英寸</div>
                    <div class="pro-price">1999元</div>
                  </a>
                </li>
                <li class="product">
                  <a href target="_blank">
                    <div class="pro-img">
                      <img
                        v-lazy="'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/70f6c0c28c61e8585805565e5e16da84.png?thumb=1&w=160&h=110&f=webp&q=90'"
                      />
                    </div>
                    <div class="pro-name">Redmi 智能电视 X55</div>
                    <div class="pro-price">1999元</div>
                  </a>
                </li>
                <li class="product">
                  <a href target="_blank">
                    <div class="pro-img">
                      <img
                        v-lazy="'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/6917267948c54c647d2009a98637aac6.jpg?thumb=1&w=160&h=110&f=webp&q=90'"
                      />
                    </div>
                    <div class="pro-name">Redmi 红米电视 70英寸 R70A</div>
                    <div class="pro-price">2999元</div>
                  </a>
                </li>
                <li class="product">
                  <a href target="_blank">
                    <div class="pro-img">
                      <img
                        v-lazy="'//cdn.cnbj0.fds.api.mi-img.com/b2c-mimall-media/00f597a8725eee9245e383c35cd4f7b6.jpg?thumb=1&w=160&h=110'"
                      />
                    </div>
                    <div class="pro-name">小米壁画电视 65英寸</div>
                    <div class="pro-price">6999元</div>
                  </a>
                </li>
                <li class="product">
                  <a href target="_blank">
                    <div class="pro-img">
                      <img
                        v-lazy="'//cdn.cnbj0.fds.api.mi-img.com/b2c-mimall-media/a40904b6a053b73b631a152334388d0e.jpg?thumb=1&w=160&h=110'"
                      />
                    </div>
                    <div class="pro-name">小米全面屏电视E55A</div>
                    <div class="pro-price">1799元</div>
                  </a>
                </li>
              </ul>
            </div>
          </div>
        </div>
        <div class="header-search">
          <div class="wrapper">
            <input type="text" name="keyword" />
            <a href="javascript:;"></a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
export default {
  name: "nav-header",
  data() {
    return {
      phoneList: [],
    };
  },
  computed: {
    ...mapState(["username", "cartCount"])
    // username () {
    //   console.log(this.$store.state.username);
    //   return this.$store.state.username;
    // },
    // cartCount () {
    //   return this.$store.state.cartCount;
    // }
  },
  filters: {
    currency(val) {
      if (!val) return "0.00";
      return "$" + val.toFixed(2) + "元";
    }
  },
  mounted() {
    this.getProductList();
  },
  methods: {
    login() {
      this.$router.push("/login");
    },
    getProductList() {
      this.axios
        .get("/products", {
          params: {
            categoryId: "100012",
            pageSize: 6
          }
        })
        .then(res => {
          this.phoneList = res.list;
        });
    },
    goToCart() {
      this.$router.push("/cart");
    }
  }
};
</script>

<style lang="less">
.header {
  .nav-topbar {
    height: 39px;
    line-height: 39px;
    background-color: #333333;
    color: #b0b0b0;
  }
  .container {
    width: 1226px;
    height: 100%;
    margin-right: auto;
    margin-left: auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    .topbar-user,
    .topbar-menu {
      height: 100%;
      a {
        text-decoration: none;
        display: inline-block;
        height: 100%;
        color: #b0b0b0;
        margin-right: 17px;
      }
      .my-cart {
        width: 110px;
        margin-right: 0px;
        background-color: #ff6600;
        text-align: center;
        color: #ffffff;
        .icon-cart {
          display: inline-block;
          width: 16px;
          height: 13px;
          background: url("/imgs/icon-cart-checked.png") no-repeat center;
          background-size: contain;
          margin-right: 4px;
        }
      }
    }
  }
  .nav-header {
    .container {
      position: relative;
      width: 1226px;
      margin-right: auto;
      margin-left: auto;
      height: 112px;
      display: flex;
      justify-content: space-between;
      align-items: center;
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
      .header-menu {
        display: inline-block;
        width: 643px;
        padding-left: 209px;
        .item-menu {
          display: inline-block;
          color: #333333;
          font-weight: bold;
          font-size: 16px;
          line-height: 112px;
          margin-right: 20px;
          span {
            cursor: pointer;
          }
          &:hover {
            color: #ff6600;
            .children {
              height: 220px;
              opacity: 1;
            }
          }
          .children {
            position: absolute;
            top: 110px;
            left: 0;
            width: 1226px;
            height: 0;
            opacity: 0;
            overflow: hidden;
            border-top: 1px solid #e5e5e5;
            box-shadow: 0px 7px 6px 0px rgba(0, 0, 0, 0.11);
            z-index: 10;
            transition: all 0.5s;
            background-color: #ffffff;
            .product {
              position: relative;
              float: left;
              width: 16.4%;
              height: 220px;
              font-size: 12px;
              line-height: 12px;
              text-align: center;
              a {
                display: inline-block;
              }
              img {
                height: 111px;
                width: auto;
                margin-top: 10px;
              }
              .pro-img {
                height: 137px;
              }
              .pro-name {
                font-weight: bold;
                margin-top: 3px;
                margin-bottom: 8px;
                color: #333333;
              }
              .pro-price {
                color: #ff6600;
              }
              &:before {
                content: "";
                position: absolute;
                top: 15px;
                right: 5px;
                border-left: 1px solid #d7d7d7;
                height: 100px;
                width: 1px;
              }
              &:last-child:before {
                display: none;
              }
            }
          }
        }
      }
      .header-search {
        width: 319px;
        .wrapper {
          height: 50px;
          border: 1px solid #e0e0e0;
          display: flex;
          align-items: center;
          input {
            border: none;
            box-sizing: border-box;
            border-right: 1px solid #e0e0e0;
            width: 264px;
            height: 50px;
            padding-left: 14px;
          }
          a {
            display: inline-block;
            width: 18px;
            height: 18px;
            background: url("/imgs/icon-search.png") no-repeat center;
            background-size: contain;
            margin-left: 17px;
          }
        }
      }
    }
  }
}

li {
  list-style-type: none;
}
</style>