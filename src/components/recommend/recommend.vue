<template>
  <div class="recommend">
    <scroll class="recommend-content">
      <div>
        <div class="slider-wrapper">
          <slider></slider>
        </div>
        <div class="recommend-list">
          <h1 class="list-title">推荐歌单</h1>
          <ul>
            <li class="ul-li" v-for="item of recommendList" :key="item.id">
              <div class="pic-container">
                <img :src="item.picUrl" alt />
              </div>
              <p class="pic-count">
                <i class="iconfont icon-search"></i>
                {{Math.floor(item.playCount / 10000)}}万
              </p>
              <div class="pic-title-container">
                <p class="pic-title">{{item.name}}</p>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </scroll>
  </div>
</template>

<script>
import Slider from "base/slider/slider";
import { getRecommendList } from "api/recommend";
import { ERROK } from "common/js/config";
import Scroll from "base/scroll/scroll";
export default {
  name: "recommend",
  components: {
    Slider,
    Scroll,
  },
  data() {
    return {
      recommendList: [],
    };
  },
  created() {
    this._getRecommendList();
  },
  methods: {
    _getRecommendList() {
      getRecommendList().then((res) => {
        if (res.status === ERROK) {
          console.log(res);
          this.recommendList = res.data.result;
        }
      });
    },
  },
};
</script>

<style scoped lang='stylus'>
@import '~common/stylus/variable';

.recommend {
  position: fixed;
  width: 100%;
  top: 88px;
  bottom: 0;
  z-index: 100;

  .recommend-content {
    width: 100%;
    height: 100%;
    overflow: hidden;

    .slider-wrapper {
      width: 100%;
      margin: 0 auto;
      border-radius: 5px;
      overflow: hidden;
      background-color: $color-background;
    }

    .recommend-list {
      position: relative;
      box-sizing: border-box;
      width: 100%;
      text-align: center;

      .list-title {
        height: 65px;
        line-height: 65px;
        padding-left: 1.5%;
        text-align: left;
        font-size: $font-size-medium;
        font-weight: bold;
        color: $color-text;
      }

      .ul-li {
        display: inline-block;
        position: relative;
        box-sizing: border-box;
        width: 33%;
        padding: 0 1%;

        .pic-container {
          position: relative;
          display: inline-block;
          width: 100%;
          margin-bottom: 5px;

          img {
            width: 100%;
            height: 100%;
            border-radius: 3px;
          }
        }

        .pic-count {
          position: absolute;
          top: 5px;
          right: 8px;
          font-size: $font-size-small-s;
          color: $color-text-l;
        }

        .pic-title-container {
          height: 40px;
          line-height: 16px;
          text-align: left;
          margin-bottom: 10px;
          font-size: $font-size-small;
          float: left;
          overflow: hidden;
        }
      }
    }
  }
}
</style>