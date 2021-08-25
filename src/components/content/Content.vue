<template>
  <div class="content">
    <div class="content-main">
      <Banner></Banner>
      <ContentMenu class="contentMenu" @onMenuChange="onMenuChange"></ContentMenu>
      <ArticlesList :articlesType="articlesType"></ArticlesList>
    </div>
    <RightMenu class="content-right"></RightMenu>
  </div>
</template>

<script>
import Banner from "@/components/content/Banner.vue";
import ContentMenu from "@/components/content/ContentMenu.vue";
import ArticlesList from "@/components/content/ArticlesList.vue";
import RightMenu from '@/components/content/RightMenu.vue'

export default {
  name: "content",
  components: { Banner, ContentMenu, ArticlesList, RightMenu },
  data() {
    return {
        articlesType: 'Girl',
    };
  },
  methods:{
    onMenuChange(type) {
      this.articlesType = type
    }
  }
};
</script>

<style lang='less' scoped>
.content {
  width: 1140px;
  display: flex;
  margin: 0 auto;
  padding: 3rem;
  flex-direction: row;
}

.content-main {
  flex: 0 0 66.666667%;
  max-width: 66.666667%;
}
.content-right {
  box-sizing: border-box;
  margin-left: 2.2rem;
  width: 100%;
}
</style>