<template>
  <div class="slider">
    <swiper :options="swiperOption" ref="mySwiper" v-if="bannerList.length">
      <!-- slides -->
      <swiper-slide v-for="item of bannerList" :key="item.id">
        <img :src="item.imageUrl" alt class="slider-img" />
      </swiper-slide>
      <!-- Optional controls -->
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
import { getBanner } from "api/recommend";
import { ERROK } from "common/js/config";

export default {
  name: "slider",
  data() {
    return {
      bannerList: [],
      swiperOption: {
        loop: true,
        autoplay: 2000,
        autoplayDisableOnInteraction: false,
        pagination: '.swiper-pagination',
      },
    };
  },
  created() {
    this._getBanner();
  },
  methods: {
    _getBanner() {
      getBanner().then((res) => {
        if (res.status === ERROK) {
          this.bannerList = res.data.banners.slice(5);
        }
      });
    },
  },
};
</script>

<style scoped lang="stylus">
@import '~common/stylus/variable';
.slider >>> .swiper-pagination-bullet {
  background-color: $color-background;
  opacity: 0.8;
}
.slider >>> .swiper-pagination-bullet-active {
  width: 8px;
  border-radius: 5px;
  background-color: $color-theme;
}
.slider-img {
  width: 100%;
}
</style>
