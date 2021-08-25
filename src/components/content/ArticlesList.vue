<template>
  <div>
    <div class="list-item" v-for="(item, index) of articlesList" :key="index">
      <ContentArticles :articles="item"></ContentArticles>
    </div>
    <div class="ph-item" v-show="isLoadding">
      <div class="ph-col-12">
        <div class="ph-picture"></div>
        <div class="ph-row">
          <div class="ph-col-6 big"></div>
          <div class="ph-col-4 empty big"></div>
          <div class="ph-col-2 big"></div>
          <div class="ph-col-4"></div>
          <div class="ph-col-8 empty"></div>
          <div class="ph-col-6"></div>
          <div class="ph-col-6 empty"></div>
          <div class="ph-col-12"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ContentArticles from "@/components/content/Articles.vue";

export default {
  name: "articlesList",
  props: ["articlesType"],
  components: { ContentArticles },
  data() {
    return {
      articlesList: [],
      isLoadding: false,
      page: 1,
    };
  },
  methods: {
    getArticles() {
      this.isLoadding = true;
      this.$axios({
        url: `https://gank.io/api/v2/data/category/All/type/${this.articlesType}/page/${this.page}/count/10`,
        methods: "get",
      })
        .then((result) => {
          this.articlesList = this.articlesList.concat(result.data.data);
        })
        .finally(() => {
          this.isLoadding = false;
        });
    },
    scrollMoreData() {
      const scrollTopHeight =
        document.documentElement.scrollTop || document.body.scrollTop; //滚动高度
      const clientHeight =
        document.documentElement.clientHeight || window.screen.availHeight; //屏幕可用工作区高度
      const offsetHeight =
        document.documentElement.offsetHeight || document.body.offsetHeight; //网页可见区域高(包括边线的宽)

        if(scrollTopHeight + clientHeight + 50 > offsetHeight) {
            if(!this.isLoadding) {
                this.page++;
                this.getArticles()
            }
        }
    },
  },
  mounted() {
    this.getArticles();
    document.addEventListener("scroll", this.scrollMoreData, false);
  },
  watch: {
    articlesType: {
      handler() {
        this.page = 1;
        this.articlesList = [];
        this.getArticles();
      },
      deep: true,
    },
  },
};
</script>

<style lang='less' scoped>
.list-item {
  margin-bottom: 2rem;
}
.ph-item {
  background-color: #1d1f20 !important;
  border: none !important;
}
</style>