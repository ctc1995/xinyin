<!-- 首页路由 -->
<template>
  <div id="index21" class="wrapper page-index">
    <!--<tab :line-width=2 :custom-bar-width="getBarWidth" :scroll-threshold=4 animated={false}  active-color='#FF4F00' v-model="index">
      <tab-item class="vux-center" :selected="onTab === item.id" v-for="(item, index) in listFun" @on-item-click="onTabClick(item)" :key="index">{{item.className}}</tab-item>
    </tab>-->
    <header class="header">
      <p class="address">深圳</p>
      <p class="title">附近商家</p>
      <router-link to="#" class="search">
        <img src="../assets/images/index/search.png" alt="搜索">
      </router-link>
    </header>

    <scroller
      lock-x
      height="-100"
      scrollbar-y
      use-pullup
      @on-pullup-loading="load1"
      ref="demo1"
      :pullup-config="pullupConfig"
    >
      <div>
        <swiper class="nav-swiper">
          <swiper-item v-for="(navItem, index) of navLists" :key="index">
            <router-link :to="item.href + '/' + itemIndex" v-for="(item, itemIndex) of navItem" :key="itemIndex">
              <img :src="item.icon" :alt="item.title">
              <p>{{item.title}}</p>
            </router-link>
          </swiper-item>
        </swiper>
        <section class="shop-lists">
          <router-link class="shop-item" to v-for="(item, index) in shopLists" :key="index">
            <img class="shop-img" :src="item.img" :alt="item.title">
            <div class="shop-info">
              <span class="shop-distance">{{item.distance}} km</span>
              <section>
                <p class="shop-title">{{item.title}}</p>
                <p class="shop-class">{{item.class}}</p>
                <p class="shop-rate">
                  <section class="star">
                    <img src="../assets/images/index/star.png" alt="★">
                    <img src="../assets/images/index/star.png" alt="★">
                    <img src="../assets/images/index/star.png" alt="★">
                    <img src="../assets/images/index/star.png" alt="★">
                    <img src="../assets/images/index/star.png" alt="★">
                  </section>
                  <section class="star-c" v-bind:style="{width: item.rate*.365+'rem'}">
                    <img src="../assets/images/index/star-c.png" alt="★">
                    <img src="../assets/images/index/star-c.png" alt="★">
                    <img src="../assets/images/index/star-c.png" alt="★">
                    <img src="../assets/images/index/star-c.png" alt="★">
                    <img src="../assets/images/index/star-c.png" alt="★">
                  </section>
                  <span>{{item.rate}}</span>
                </p>
              </section>
              <section>
                <p class="shop-address">{{item.address}}</p>
              </section>
            </div>
          </router-link>
        </section>
      </div>
    </scroller>

    <!-- <swiper v-model="index" height="100%" :show-dots="false">
      <indexNew  v-if="onTab===0" />
      <tabContent v-else :parentId="onTab" />
    </swiper>-->
    <v-footer active="index"/>
    <v-wechatshare :friendShare="weChatShare"/>
  </div>
</template>

<script>
import indexNew from "@/views/index/indexNew";
import tabContent from "@/views/index/tabContent";
import vFooter from "@/components/v-footer";
import VWechatshare from "@/components/v-wechatshare";
import { Tab, TabItem, Swiper, SwiperItem, Scroller } from "vux";
import { mapState } from "vuex";
export default {
  data() {
    return {
      listFun: [1, 2, 3, 4, 5, 6],
      index: 0,
      onTab: 0,
      getBarWidth: function() {
        return 66 + "px";
      },
      pullupConfig: {
        content: "上拉加载更多",
        downContent: "松开进行加载",
        upContent: "上拉加载更多",
        loadingContent: "加载中..."
      },
      shopLists: [
        {
          img: require("../assets/images/index/shopImg.jpg"),
          title: "姚记客家菜酒楼",
          class: "酒店美食",
          rate: 4.8,
          address: "深圳市龙岗区华南城1号交易广场3楼3B173",
          distance: 0.2
        },
        {
          img: require("../assets/images/index/shopImg.jpg"),
          title: "姚记客家菜酒楼",
          class: "酒店美食",
          rate: 2,
          address: "深圳市龙岗区华南城1号交易广场3楼3B173",
          distance: 0.2
        },
        {
          img: require("../assets/images/index/shopImg.jpg"),
          title: "姚记客家菜酒楼",
          class: "酒店美食",
          rate: 3.5,
          address: "深圳市龙岗区华南城1号交易广场3楼3B173",
          distance: 0.2
        },
        {
          img: require("../assets/images/index/shopImg.jpg"),
          title: "姚记客家菜酒楼",
          class: "酒店美食",
          rate: 4.7,
          address: "深圳市龙岗区华南城1号交易广场3楼3B173",
          distance: 0.2
        }
      ],
      navLists: [
        [
          {
            icon: require("../assets/images/index/chaoshishangchang.png"),
            title: "超市商场",
            href: "indexClass"
          },
          {
            icon: require("../assets/images/index/meishijiudian.png"),
            title: "美食酒店",
            href: "indexClass"
          },
          {
            icon: require("../assets/images/index/fuzhuangxiaoshou.png"),
            title: "服装销售",
            href: "indexClass"
          },
          {
            icon: require("../assets/images/index/shoujijiadian.png"),
            title: "手机家电",
            href: "indexClass"
          },
          {
            icon: require("../assets/images/index/jiajujiafang.png"),
            title: "家居家纺",
            href: "indexClass"
          },
          {
            icon: require("../assets/images/index/wujinjiancai.png"),
            title: "五金建材",
            href: "indexClass"
          },
          {
            icon: require("../assets/images/index/yinpindian.png"),
            title: "饮品店",
            href: "indexClass"
          },
          {
            icon: require("../assets/images/index/lirenbaojian.png"),
            title: "丽人保健",
            href: "indexClass"
          },
          {
            icon: require("../assets/images/index/pinpaiqiye.png"),
            title: "品牌企业",
            href: "indexClass"
          },
          {
            icon: require("../assets/images/index/zhubaoshoushi.png"),
            title: "珠宝首饰",
            href: "indexClass"
          }
        ],
        [
          {
            icon: require("../assets/images/index/bianlidian.png"),
            title: "便利店",
            href: "indexClass"
          },
          {
            icon: require("../assets/images/index/bianminfuwu.png"),
            title: "便民服务",
            href: "indexClass"
          },
          {
            icon: require("../assets/images/index/qichexiuli.png"),
            title: "汽车修理",
            href: "indexClass"
          },
          {
            icon: require("../assets/images/index/xiuxianyule.png"),
            title: "休闲娱乐",
            href: "indexClass"
          }
        ]
      ]
    };
  },
  components: {
    "v-footer": vFooter,
    "v-wechatshare": VWechatshare,
    indexNew,
    tabContent,
    Tab,
    TabItem,
    Swiper,
    SwiperItem,
    Scroller,
    tabContent,
    indexNew
  },
  beforeCreate() {
    document.title = "新银众商";
  },
  created() {
    this.getAllClassTree();
    this.getClassBylevel();
  },
  computed: {
    ...mapState(["weChatInfo", "weChatShare"])
  },
  methods: {
    // 上拉加载方法
    load1() {
      setTimeout(() => {
        this.shopLists.push(...this.shopLists)
        setTimeout(() => {
          this.$refs.demo1.donePullup();
        }, 100);
      }, 1000);
    },
    onTabClick(item) {
      this.onTab = item.id;
      console.log(this.onTab);
    },
    getClassBylevel() {
      this.$axios
        .get(this.api.getClassBylevel + 1)
        .then(res => {
          if (res.data.code === 1) {
            this.listFun = [];
            res.data.content.unshift({ id: 0, className: "商城首页" });
            this.listFun = res.data.content;
          }
          console.log(res.data);
        })
        .catch(res => {
          //下单失败，请您稍后重试
        });
    },
    getAllClassTree() {
      this.$axios
        .get(this.api.getClassTree)
        .then(res => {
          console.log(res.data);
        })
        .catch(res => {
          //下单失败，请您稍后重试
        });
    }
  }
};
</script> 
<style lang="stylus">
@import '../assets/css/index';

#index21 {
  color: #282828;

  // padding:44px 0 0 0!important;
  .vux-tab-wrap {
    position: fixed;
    height: 44px;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 9;
  }

  .vux-slider {
    height: 100%;
    margin-bottom: .2rem;
  }

  .nav-swiper {
    height: 4rem;
    background-color: #fff;
    margin-top: .2rem;
  }

  .vux-slider > .vux-indicator > a > .vux-icon-dot, .vux-slider .vux-indicator-right > a > .vux-icon-dot, .vux-slider > .vux-indicator > a > .vux-icon-dot.active, .vux-slider .vux-indicator-right > a > .vux-icon-dot.active {
    width: 6.667vw;
    height: 0.6667vw;
  }

  .vux-slider > .vux-indicator > a > .vux-icon-dot.active, .vux-slider .vux-indicator-right > a > .vux-icon-dot.active {
    background-color: #FF4F00;
  }

  .vux-slider > .vux-indicator, .vux-slider .vux-indicator-right {
    right: 41.5vw;
  }

  .vux-slider > .vux-swiper > .vux-swiper-item > a {
    width: 20%;
    height: 50%;
    display: inline-flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .vux-slider > .vux-swiper > .vux-swiper-item > a > img {
    width: 0.84rem;
    height: 0.84rem;
    margin-bottom: 0.1rem;
  }

  .vux-slider > .vux-swiper {
    overflow-y: scroll;
  }

  .shop-lists {
    background-color: #fff;
    padding: 0.4rem 0.3rem;
  }

  .shop-item {
    display: flex;
    align-items: center;
    min-height: 1.9rem;
    .shop-img {
      height: 1.9rem;
      max-width: 30%;
      margin-right: 0.3rem;
    }

    .shop-info {
      position: relative;
      width: 70%;
      min-height: 1.9rem;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      .shop-title{
        font-size: 0.3rem;
        font-weight: 600;
        max-width: 47vw;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
      }
      .shop-distance{
        position: absolute;
        right: 2vw;
        color #8F8F8F;
      }
      .shop-class{
        color: #8C8C8C;
      }
      .shop-address{
        color: #5C5C5C;
        border-bottom: 1px solid #F4F6F5;
      }
      .shop-class, .shop-address{
        font-size: .2rem;
      }
      .shop-address{
        overflow: hidden;
        text-overflow: ellipsis;
        display: -webkit-box;
        -webkit-line-clamp: 2;
        -webkit-box-orient: vertical;
      }
      .shop-rate {
          position: relative;
          span{
              position: absolute;
              left: 26vw;
              top: -0.6vw;
          }
        .star, .star-c{
          width: 1.8rem;
          overflow hidden;
          text-overflow: ellipsis;
          white-space: nowrap;
          position: absolute;
             img {
              width: .3rem;
              height: .3rem;
          }
        }
      }
    }
  }

  .shop-item + .shop-item {
    margin-top: 0.3rem;
  }
}
</style>
