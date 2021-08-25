<template>
  <div id="app">
    <Header></Header>
    <Content></Content>
    <div id="goTop" class="iconfont" :style="{opacity:showGoTop? 1: 0}" @click="goTop">&#xe64b;</div>
  </div>
</template>
<script>
import Header from "@/components/Header.vue";
import Content from "@/components/content/Content.vue";
export default {
  name: "app",
  data() {
    return {
      showGoTop: false,
      goTopSpeed: 0,
    };
  },
  components: {
    Header,
    Content,
  },
  mounted() {
    window.addEventListener("scroll", this.handlScroll);
  },
  methods: {
    handlScroll() {
      let scrollTop =
        window.pageYOffset ||
        document.documentElement.scrollTop ||
        document.body.scrollTop;
      if (scrollTop > 200) {
        this.showGoTop = true;
        this.goTopSpeed = scrollTop / 30
      } else {
        this.showGoTop = false;
      }
    },
    goTop() {
        let top = document.documentElement.scrollTop || document.body.scrollTop;
      // 实现滚动效果 
      const timeTop = setInterval(() => {
        document.body.scrollTop = document.documentElement.scrollTop = top -= 50;
        if (top <= 0) {
          clearInterval(timeTop);
        }
      }, 10);
    }
  },
};
</script>

<style lang='less'>
* {
  padding: 0;
  margin: 0;
}

.container {
  width: 100%;
  padding-left: 15px;
  padding-right: 15px;
  margin-left: auto;
  margin-right: auto;
  box-sizing: border-box;
}

a {
  text-decoration: none;
}
a:link {
  text-decoration: none;
}
a:visited {
  text-decoration: none;
}
a:hover {
  text-decoration: none;
}
a:active {
  text-decoration: none;
}

#goTop {
  width: 2rem;
  height: 2rem;
  background-color: #2c63ff;
  border-radius: .3rem;
  position: fixed;
  bottom: 3rem;
  right: 3rem;
  color: white;
  box-sizing: border-box;
  font-size: 1rem;
  text-align: center;
  line-height: 2rem;
  transition: .5s;
}
</style>
