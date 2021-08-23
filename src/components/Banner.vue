<!-- 轮播图 -->
<template>
  <div>
    <div id="banner" @mouseenter="stopScroll" @mouseleave="starScroll">
      <div
        :style="{
          transform: 'translate3d(-' + bannerIndex * 750 + 'px, 0px, 0px)',
          transition: 'all ' + transitionTime + 's ease 0s',
          width: bannerList.length * 750 + 'px',
          height: '100%',
        }"
      >
        <div
          v-for="(item, index) in bannerList"
          :key="index"
          class="banner-image"
          :style="{ background: item }"
        ></div>
      </div>
      <div id="banner-up" class="banner-btn" @click="upBanner">上</div>
      <div id="banner-next" class="banner-btn" @click="nextBanner">下</div>
      <div class="bannerPointView">
        <span
          v-for="index of bannerSouceList.length"
          :key="index"
          @click="onPointClick(index)"
          :class="{
            bannerPointActive: index === pointIndex,
            bannerPoint: index !== pointIndex,
          }"
        >
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "banner",
  data() {
    return {
      bannerIndex: 1,
      bannerSouceList: ["green", "red", "blue"],
      bannerList: [],
      bannerInterval: null,
      transitionTime: 1,
      bannerBtnClickTime: 0,
    };
  },
  components: {},
  methods: {
    starScroll() {
      this.bannerInterval = setInterval(() => {
        this.nextBanner();
      }, 3000);
    },
    stopScroll() {
      clearInterval(this.bannerInterval);
    },
    nextBanner() {
      if (!this.canClick()) {
        return;
      }
      if (this.bannerIndex === this.bannerList.length - 2) {
        this.bannerIndex = this.nextBannerIndex;
        setTimeout(() => {
          this.transitionTime = 0;
          this.bannerIndex = 1;
        }, 1000);
      } else {
        this.transitionTime = 1;
        this.bannerIndex = this.nextBannerIndex;
      }
    },
    upBanner() {
      if (!this.canClick()) {
        return;
      }
      if (this.bannerIndex === 1) {
        this.bannerIndex = this.upBannerIndex;
        setTimeout(() => {
          this.transitionTime = 0;
          this.bannerIndex = this.bannerList.length - 2;
        }, 1000);
      } else {
        this.transitionTime = 1;
        this.bannerIndex = this.upBannerIndex;
      }
    },
    canClick() {
      if (new Date().getTime() < this.bannerBtnClickTime + 1000) {
        return false;
      } else {
        this.bannerBtnClickTime = new Date().getTime();
        return true;
      }
    },
    onPointClick(index) {
      if (index !== this.pointIndex) {
        if (index === 1 && this.pointIndex === 3) {
          this.nextBanner();
        } else if (index === 3 && this.pointIndex === 1) {
          this.upBanner();
        } else {
          if (index > this.pointIndex) {
            this.nextBanner();
          } else {
            this.upBanner();
          }
        }
      }
    },
  },
  mounted() {
    this.bannerList.push(this.bannerSouceList[this.bannerSouceList.length - 1]);
    this.bannerList = this.bannerList.concat(this.bannerSouceList);
    this.bannerList.push(this.bannerSouceList[0]);
    this.starScroll();
  },
  computed: {
    upBannerIndex: function () {
      if (this.bannerIndex === 0) {
        return this.bannerList.length - 1;
      } else {
        return this.bannerIndex - 1;
      }
    },
    nextBannerIndex: function () {
      if (this.bannerIndex === this.bannerList.length - 1) {
        return 1;
      } else {
        return this.bannerIndex + 1;
      }
    },
    pointIndex: function () {
      if (
        this.bannerIndex === 0 ||
        this.bannerIndex === this.bannerList.length - 2
      ) {
        return this.bannerSouceList.length;
      } else if (
        this.bannerIndex === this.bannerList.length - 1 ||
        this.bannerIndex === 1
      ) {
        return 1;
      } else {
        return this.bannerIndex;
      }
    },
  },
};
</script>

<style lang='less' scoped>
#banner {
  border-radius: 0.3rem;
  height: 20rem;
  position: relative;
  width: 750px;
  overflow: hidden;
  &:hover {
    .banner-btn {
      opacity: 1;
    }
  }

  .banner-image {
      &::after {
          clear: both;
      }
    float: left;
    width: 750px;
    height: 100%;
    transition: 0.5s;
  }

  .banner-btn {
    transition: 1s;
    opacity: 0;
    position: absolute;
    background: rgba(0, 0, 0, 0.705);
    height: 2rem;
    line-height: 2rem;
    width: 2rem;
    color: white;
    text-align: center;
    top: 50%;
    z-index: 10;
  }

  .bannerPointView {
    position: absolute;
    bottom: 20px;
    right: 20px;
    z-index: 10;
    display: flex;
  }

  .bannerPoint {
    margin-left: 10px;
    width: 1rem;
    height: 0.2rem;
    background: grey;
    transition: 0.3s;
    &:hover {
      cursor: pointer;
    }
  }
  .bannerPointActive {
    background: white;
    margin-left: 10px;
    width: 1.5rem;
    height: 0.2rem;
    transition: 0.3s;
  }
}
#banner-up {
  left: 0;
}
#banner-next {
  right: 0;
}
</style>