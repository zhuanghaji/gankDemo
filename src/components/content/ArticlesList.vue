<template>
  <div>
    <div class="list-item" v-for="(item, index) of articlesList" :key="index">
      <ContentArticles :articles="item"></ContentArticles>
    </div>
  </div>
</template>

<script>
import ContentArticles from "@/components/content/Articles.vue";

export default {
  name: "articlesList",
  components: { ContentArticles },
  data() {
    return {
      articlesList: [
        {
          type: "学习",
          title: "Vue教程",
          avatar: "https://gank.io/images/f4f6d68bf30147e1bdd4ddbc6ad7c2a2",
          imgSrc: "https://gank.io/images/f4f6d68bf30147e1bdd4ddbc6ad7c2a2",
          author: "庆龙",
          time: "一天前",
          content: "Vue入门到精通",
        },
        {
          type: "学习",
          title: "Vue教程",
          avatar: "https://gank.io/images/f4f6d68bf30147e1bdd4ddbc6ad7c2a2",
          imgSrc: "https://gank.io/images/f4f6d68bf30147e1bdd4ddbc6ad7c2a2",
          author: "庆龙",
          time: "一天前",
          content: "Vue入门到精通",
        },
        {
          type: "学习",
          title: "Vue教程",
          avatar: "https://gank.io/images/f4f6d68bf30147e1bdd4ddbc6ad7c2a2",
          imgSrc: "https://gank.io/images/f4f6d68bf30147e1bdd4ddbc6ad7c2a2",
          author: "庆龙",
          time: "一天前",
          content: "Vue入门到精通",
        },
        {
          type: "学习",
          title: "Vue教程",
          avatar: "https://gank.io/images/f4f6d68bf30147e1bdd4ddbc6ad7c2a2",
          imgSrc: "https://gank.io/images/f4f6d68bf30147e1bdd4ddbc6ad7c2a2",
          author: "庆龙",
          time: "一天前",
          content: "Vue入门到精通",
        },
      ],
    };
  },
};
</script>

<style lang='less' scoped>
    .list-item {
        margin-bottom: 2rem;
    }
</style>