<template>
  <div id="right-menu" ref="rmenu" :style="rMenuStyle">
    <div class="calendar">
      <a
        class="media"
        href="#"
        :style="{
          'background-image': `url(${
            girl && girl.images && girl.images[0] ? girl.images[0] : ''
          })`,
        }"
      >
        <span class="overlay"></span>
      </a>
      <div class="showData">
        <div class="date">
          <span class="day">{{ getDay(girl.publishedAt) }}</span>
          <span class="my"
            >{{ getMoon(girl.publishedAt) }}月,{{
              getYear(girl.publishedAt)
            }}</span
          >
        </div>
        <div class="data">
          <span class="data-title">妹纸图{{ girl.title }}</span>
          <span class="data-type">Random Girl</span>
        </div>
      </div>
      <a class="refresh" @click="getGirl"
        ><i class="refresh-icon iconfont">&#xe618;</i></a
      >
    </div>

    <div id="hot" class="card">
      <div class="card-title">本周最🔥妹纸</div>
      <div class="media-group">
        <span
          class="media"
          v-for="item of hotGirl"
          :key="item._id"
          :style="{
            'background-image': `url(${
              item && item.images && item.images[0] ? item.images[0] : ''
            })`,
          }"
        ></span>
      </div>
    </div>

    <div class="hot-articles card">
      <div class="card-title">本周最热文章</div>
      <div
        class="hot-articles-item"
        v-for="item of hotArticles"
        :key="item._id"
      >
        <span
          class="media"
          :style="{
            'background-image': `url(${
              item && item.images && item.images[0] ? item.images[0] : ''
            })`,
          }"
        ></span>
        <div class="hot-articles-content">
          <span class="title hover-blue">{{ item.desc }}</span>
          <span class="time">{{ item.publishedAt }}</span>
        </div>
      </div>
    </div>

    <div class="hot-articles card">
      <div class="card-title">本周最热干货</div>
      <div class="hot-articles-item" v-for="item of hotGanHuo" :key="item._id">
        <span
          class="media"
          :style="{
            'background-image': `url(${
              item && item.images && item.images[0] ? item.images[0] : ''
            })`,
          }"
        ></span>
        <div class="hot-articles-content">
          <span class="title hover-blue">{{ item.desc }}</span>
          <span class="time">{{ item.publishedAt }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "rightMenu",
  data() {
    return {
      girl: {},
      hotGirl: [],
      hotGanHuo: [],
      hotArticles: [],
      rMenuStyle: {},
      rMenuTypeValue: 0,
    };
  },
  methods: {
    getGirl() {
      this.$axios({
        url: "https://gank.io/api/v2/random/category/Girl/type/Girl/count/1",
        methods: "get",
      }).then((result) => {
        this.girl = result.data.data[0];
      });
    },
    getDay(date) {
      if (date === null) {
        return "";
      }
      var d = new Date(date);
      return d.getDate() < 10 ? "0" + d.getDate() : d.getDate();
    },
    getMoon(date) {
      if (date === null) {
        return "";
      }
      var d = new Date(date);
      return d.getMonth() + 1 < 10
        ? "0" + (d.getMonth() + 1)
        : d.getMonth() + 1;
    },
    getYear(date) {
      if (date === null) {
        return "";
      }
      var d = new Date(date);
      return d.getFullYear();
    },
    getHotGirl() {
      this.$axios({
        url: "https://gank.io/api/v2/hot/likes/category/Girl/count/3",
        methods: "get",
      }).then((result) => {
        this.hotGirl = result.data.data;
      });
    },
    getHotGanHuo() {
      this.$axios({
        url: "https://gank.io/api/v2/hot/likes/category/GanHuo/count/5",
        methods: "get",
      }).then((result) => {
        this.hotGanHuo = result.data.data;
      });
    },
    getHotArticle() {
      this.$axios({
        url: "https://gank.io/api/v2/hot/likes/category/Article/count/5",
        methods: "get",
      }).then((result) => {
        this.hotArticles = result.data.data;
      });
    },
    initData() {
      this.getGirl();
      this.getHotGirl();
      this.getHotGanHuo();
      this.getHotArticle();
    },
    scrollEvent() {
      const scrollTopHeight =
        document.documentElement.scrollTop || document.body.scrollTop; //滚动高度
      const clientHeight =
        document.documentElement.clientHeight || window.screen.availHeight; //屏幕可用工作区高度
      const offsetHeight =
        document.documentElement.offsetHeight || document.body.offsetHeight; //网页可见区域高(包括边线的宽)
      console.log(
        scrollTopHeight +
          "--" +
          clientHeight +
          "--" +
          offsetHeight +
          "--" +
          this.$refs.rmenu.top
      );

      if (scrollTopHeight > 0) {
        this.rMenuStyle = {
          top: `-${this.rMenuTypeValue}px`,
        };
      } else {
        this.rMenuStyle = {
          bottom: `-${this.rMenuTypeValue}px`,
        };
      }
    },
  },
  mounted() {
    this.initData();
    document.addEventListener("scroll", this.scrollEvent, false);
    this.rMenuTypeValue = this.$refs.rmenu.offsetHeight;
    this.rMenuStyle = {
      bottom: `-${this.rMenuTypeValue}px`,
    };
  },
};
</script>

<style lang='less' scoped>
#right-menu {
  display: flex;
  flex-direction: column;
}
.calendar {
  border-radius: 0.5rem;
  position: relative;
  display: flex;
  flex-direction: column;
  margin-bottom: 2rem;

  .media {
    width: 100%;
    border-radius: 0.3rem;
    height: 100%;
    background-image: url(https://ae01.alicdn.com/kf/U11829fe9d4ae4d96b053dbf1b1cc7382g.jpg);
    background-size: cover;
    background-repeat: no-repeat;
    background-position: 50% 50%;
    background-color: rgba(120, 120, 120, 0.1);
    position: absolute;
    .overlay {
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.66);
      top: 0;
      position: absolute;
      left: 0;
      opacity: 0.22;
    }
  }

  &::before {
    padding-top: 100%;
    display: block;
    content: "";
  }
  .showData {
    position: absolute;
    width: 100%;
    height: 100%;
    .date {
      display: flex;
      flex-direction: column;
      color: white;
      position: relative;
      left: 1.2rem;
      top: 1.2rem;
      width: 5rem;
      text-align: center;
      .day {
        font-size: 3rem;
        font-weight: 300;
      }
      .my {
        font-size: 0.6rem;
      }
    }

    .data {
      display: flex;
      flex-direction: column;
      position: absolute;
      bottom: 1.2rem;
      left: 1.5rem;
      color: white;
      align-items: center;

      .data-title {
        font-size: 1.2;
        cursor: pointer;
      }

      .data-type {
        width: 4.5rem;
        margin-top: 0.5rem;
        font-size: 0.5rem;
        background: #2c63ff;
        padding: 0.1rem 0.2rem;
      }
    }
  }
  .refresh {
    text-align: center;
    position: absolute;
    bottom: 1.5rem;
    right: 1.5rem;
    cursor: pointer;
    .refresh-icon {
      color: white;
      font-size: 1.3rem !important;
    }
  }
}

#hot {
  width: 100%;
  position: relative;
  display: flex;
  flex-direction: column;
  .media-group {
    box-sizing: border-box;
    display: flex;
    width: 100%;
    justify-content: space-between;
    height: 8rem;
    .media {
      box-sizing: border-box;
      width: 30%;
      height: 100%;
      border-radius: 0.3rem;
      background-image: url(https://ae01.alicdn.com/kf/U11829fe9d4ae4d96b053dbf1b1cc7382g.jpg);
      background-size: cover;
      background-repeat: no-repeat;
      background-position: 50% 50%;
      background-color: rgba(120, 120, 120, 0.1);
    }
  }
}

.card {
  border-radius: 0.3rem;
  background-color: #1d1f20;
  padding: 1rem;
  box-sizing: border-box;
  margin-bottom: 2rem;
}

.card-title {
  color: white;
  font-size: 1rem;
  margin-bottom: 1rem;
}

.hot-articles-item {
  position: relative;
  display: flex;
  flex-direction: row;
  height: 4.5rem;
  margin-bottom: 1rem;
  .hot-articles-content {
    margin-left: 0.5rem;
    height: 100%;
    display: flex;
    width: 65%;
    flex-direction: column;
    flex: 1 1 auto;
    .title {
      color: white;
      font-size: 0.9rem;
      overflow: hidden;
      line-clamp: 2;
      &:hover {
        color: #2c63ff;
        cursor: pointer;
      }
    }
    .time {
      margin-top: 1.1rem;
      color: gray;
      font-size: 0.5rem;
    }
  }

  .media {
    box-sizing: border-box;
    height: 100%;
    width: 35%;
    border-radius: 0.3rem;
    background-image: url(https://ae01.alicdn.com/kf/U11829fe9d4ae4d96b053dbf1b1cc7382g.jpg);
    background-size: cover;
    background-repeat: no-repeat;
    background-position: 50% 50%;
    background-color: rgba(120, 120, 120, 0.1);
  }
}

.hot-tag {
  display: flex;
  flex-wrap: wrap;
  .tag-item {
    display: block;
    padding: 0 0.5rem;
  }
}

.hover-blue {
  color: white;

  &:hover {
    color: #2c63ff;
    cursor: pointer;
  }
}
</style>