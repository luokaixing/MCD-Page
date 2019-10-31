<!-- home -->
<template>
  <div class="mybody">
    <div class="home-body">
      <div class="list-swarper">
        <ul>
          <li class="item-img" v-for="(food,index) in loopfood" :key="food.foodId">
            <br>
            <span class="list-span">{{food.foodTime}}</span><br>
            <img
              :src="food.foodImg"
              class="swarper-img"
              @click="handleswiper(index)"
            />
          </li>
        </ul>
      </div>
      <div>
        <img src="@/assets/code.png" alt class="qr-code" />
      </div>
    </div>
    <div class="foot">
      <div v-if="flag">
        <img src="@/assets/tab1-active.png" alt id="foot-img1" @click="handletab1" />
        <img src="@/assets/tab2-default.png" alt id="foot-img2" @click="handletab2" />
      </div>
      <div v-else>
        <img src="@/assets/tab1-default.png" alt id="foot-img1" @click="handletab1" />
        <img src="@/assets/tab2-active.png" alt id="foot-img2" @click="handletab2" />
      </div>
    </div>
    <div class="myswiper" v-show="imgflag">
      <div class="swiper-container">
        <div class="swiper-wrapper">
          <div class="swiper-slide" v-for="food in loopfood" :key="food.foodId">
            <img :src="food.foodImg" class="slide-img" />
          </div>
        </div>
        <div class="close-flag" @click="closeimg">
          <span class="xicon">
            <img src="@/assets/close.png" />
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Swiper from "swiper";
export default {
  data() {
    return {
      imgflag: false, // 控制 swiper 显示开关
      flag: true, // 控制按钮显示开关
      mySwiper: null,
      loopfood: [],
      foods1: [
        {
          foodId: 1,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/8.30-thumb.jpg",
          foodTime: 8.8
        },
        {
          foodId: 2,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/8.30-thumb.jpg",
          foodTime: 8.9
        },
        {
          foodId: 3,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/8.22-thumb.jpg",
          foodTime: 8.1
        },
        {
          foodId: 4,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/8.30-thumb.jpg",
          foodTime: 8.11
        },
        {
          foodId: 5,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/8.22-thumb.jpg",
          foodTime: 8.12
        },
        {
          foodId: 6,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/8.30-thumb.jpg",
          foodTime: 8.13
        },
        {
          foodId: 7,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/8.22-thumb.jpg",
          foodTime: 8.14
        },
        {
          foodId: 8,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/8.22-thumb.jpg",
          foodTime: 8.15
        },
        {
          foodId: 9,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/8.22-thumb.jpg",
          foodTime: 8.16
        },
        {
          foodId: 10,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/8.22-thumb.jpg",
          foodTime: 8.17
        },
        {
          foodId: 11,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/8.22-thumb.jpg",
          foodTime: 8.18
        },
        {
          foodId: 12,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/8.22-thumb.jpg",
          foodTime: 8.19
        },
        {
          foodId: 13,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/9.3-thumb.jpg",
          foodTime: 8.2
        },
        {
          foodId: 14,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/9.3-thumb.jpg",
          foodTime: 8.21
        },
        {
          foodId: 15,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/9.3-thumb.jpg",
          foodTime: 8.22
        },
        {
          foodId: 16,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/9.3-thumb.jpg",
          foodTime: 8.23
        },
        {
          foodId: 17,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/9.3-thumb.jpg",
          foodTime: 8.24
        },
        {
          foodId: 18,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/9.3-thumb.jpg",
          foodTime: 8.25
        },
        {
          foodId: 19,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/9.4-thumb.jpg",
          foodTime: 8.26
        },
        {
          foodId: 20,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/9.4-thumb.jpg",
          foodTime: 8.27
        },
        {
          foodId: 21,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/9.4-thumb.jpg",
          foodTime: 8.28
        },
        {
          foodId: 22,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/9.4-thumb.jpg",
          foodTime: 8.29
        },
        {
          foodId: 23,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/9.4-thumb.jpg",
          foodTime: 8.3
        },
        {
          foodId: 24,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/9.4-thumb.jpg",
          foodTime: 8.31
        },
        {
          foodId: 25,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.26-thumb.jpg",
          foodTime: 9.1
        },
        {
          foodId: 26,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.26-thumb.jpg",
          foodTime: 9.2
        },
        {
          foodId: 27,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.26-thumb.jpg",
          foodTime: 9.3
        },
        {
          foodId: 28,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.26-thumb.jpg",
          foodTime: 9.4
        }
      ],
      foods2: [
        {
          foodId: 1,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/8.20-thumb.jpg",
          foodTime: 8.8
        },
        {
          foodId: 2,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/8.20-thumb.jpg",
          foodTime: 8.9
        },
        {
          foodId: 3,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/8.20-thumb.jpg",
          foodTime: 8.1
        },
        {
          foodId: 4,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/8.20-thumb.jpg",
          foodTime: 8.11
        },
        {
          foodId: 5,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/8.20-thumb.jpg",
          foodTime: 8.12
        },
        {
          foodId: 6,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface/images/stores/8.20-thumb.jpg",
          foodTime: 8.13
        },
        {
          foodId: 7,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.11-thumb.jpg",
          foodTime: 8.14
        },
        {
          foodId: 8,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.11-thumb.jpg",
          foodTime: 8.15
        },
        {
          foodId: 9,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.11-thumb.jpg",
          foodTime: 8.16
        },
        {
          foodId: 10,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.11-thumb.jpg",
          foodTime: 8.17
        },
        {
          foodId: 11,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.11-thumb.jpg",
          foodTime: 8.18
        },
        {
          foodId: 12,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.11-thumb.jpg",
          foodTime: 8.19
        },
        {
          foodId: 13,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.27-thumb.jpg",
          foodTime: 8.2
        },
        {
          foodId: 14,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.27-thumb.jpg",
          foodTime: 8.21
        },
        {
          foodId: 15,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.27-thumb.jpg",
          foodTime: 8.22
        },
        {
          foodId: 16,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.27-thumb.jpg",
          foodTime: 8.23
        },
        {
          foodId: 17,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.27-thumb.jpg",
          foodTime: 8.24
        },
        {
          foodId: 18,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.27-thumb.jpg",
          foodTime: 8.25
        },
        {
          foodId: 19,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.20-thumb.jpg",
          foodTime: 8.26
        },
        {
          foodId: 20,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.20-thumb.jpg",
          foodTime: 8.27
        },
        {
          foodId: 21,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.20-thumb.jpg",
          foodTime: 8.28
        },
        {
          foodId: 22,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.20-thumb.jpg",
          foodTime: 8.29
        },
        {
          foodId: 23,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.20-thumb.jpg",
          foodTime: 8.3
        },
        {
          foodId: 24,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.20-thumb.jpg",
          foodTime: 8.31
        },
        {
          foodId: 25,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.13-thumb.jpg",
          foodTime: 9.1
        },
        {
          foodId: 26,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.13-thumb.jpg",
          foodTime: 9.2
        },
        {
          foodId: 27,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.13-thumb.jpg",
          foodTime: 9.3
        },
        {
          foodId: 28,
          foodImg:
            "http://mcdonald.rfthunder.com/88/interface//images/delivery/8.13-thumb.jpg",
          foodTime: 9.4
        }
      ]
    };
  },
  mounted: function() {
    this.loopfood = this.foods1;
    //初始化swiper
    this.mySwiper = new Swiper(".swiper-container", {
      observer: true,
      observeParents: true,
      speed: 300,
      initialSlide: 0 //初始跳转到哪一个swiper
    });
  },
  methods: {
    handletab1() {
      this.loopfood = this.foods1;
      this.flag = true;
    },
    handletab2() {
      this.loopfood = this.foods2;
      this.flag = false;
    },
    /**
     * @param index Int default 0
     * return Int
     * 方法是用来根据索引值跳转至制定位置
     */
    handleswiper(index) {
      // 打开 swiper
      this.imgflag = true;
      // console.log(this.mySwiper);
      // 通过传递的索引值跳转到 swiper 的页面
      this.mySwiper.slideTo(index, 1000, false);
    },
    //关闭swiper
    closeimg() {
      this.imgflag = false;
    }
  }
};
</script>

<style scoped>
.mybody{
  position:fixed;
  height: 100vh;
  width: 100vw;
}
.myswiper {
  position: fixed;
  top: 0px;
  left: 0px;
  right: 0px;
  bottom: 0px;
  width: 750px;
  height: 1334px;
  z-index: 999;
  overflow: hidden;
  background-color: rgba(0, 0, 0, 0.6);
}
.slide-img {
  width: 642px;
  height: 959px;
  z-index: 9999;
  display: inline-block;
  border-radius:10px;
  overflow: hidden;
}
.swiper-slide{
  display: flex;
  justify-content: center;
  align-items: center;
}
.swiper-container {
  width: 750px;
  height: 1334px;
}
.close-flag {
  width: 64px;
  height: 64px;
  display: inline-block;
  position: fixed;
  top: 1180px;
  left: 335px;
  border: 1px solid white;
  border-radius: 50%;
  z-index: 9999;
}
.home-body {
  width: 716px;
  height: 1040px;
  margin: auto;
  background-image: url(../assets/home-pic4.png);
  background-size: 716px 1040px;
  background-position: center;
  background-repeat: no-repeat;
  position: relative;
}
.list-swarper {
  padding: 100px 40px;
  color: red;
}
.list-span {
  margin-left: 21px;
  padding-top: 20px;
}
.swarper-img {
  display: inline-block;
  width: 72px;
  height: 107px;
  margin-right: 5px;
  margin-top: 5px;
}
.item-img {
  display: inline-block;
  list-style: none;
  margin-left: 13px;
}
.qr-code {
  display: inline-block;
  position: absolute;
  right: 105px;
  bottom: 148px;
  width: 157px;
  height: 157px;
}
.foot {
  width: 750px;
  height: 200px;
}
#foot-img1 {
  display: inline-block;
  width: 238px;
  height: 80px;
  margin: auto;
  padding-left: 83px;
  margin-top: 129px;
}
#foot-img2 {
  display: inline-block;
  width: 238px;
  height: 80px;
  margin: auto;
  padding-left: 83px;
  margin-top: 129px;
}
</style>
