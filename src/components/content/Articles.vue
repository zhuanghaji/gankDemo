<template>
  <div class="articles">
    <div class="articles-title hover-blue"><span>{{ articles.category }}</span>{{ articles.title }}</div>
    <div class="sub-title">
      <div class="avatar-view">
        <a>
          <img :src="articles.avatar" />
        </a>
      </div>
      <div class="name-view hover-blue"><a>{{ articles.author }}</a></div>

      <div class="line-view">
        <i>—</i>
      </div>

      <div class="type-view hover-blue">
        <a>{{ articles.type }}</a>
      </div>
      <div class="flex-fill"></div>
      <div class="time-vie">{{ articles.publishedAt }}</div>
    </div>

    <div class="big-img">
        <a>
            <img :src="articles.images[0]"/>
        </a>
    </div>

    <div class="content">
    {{ articles.desc }} </div>
  </div>
</template>

<script>
export default {
  name: "contentArticles",
  props: {
      articles: {

      }
  },
  data() {
    return {};
  },
};
</script>

<style lang='less' scoped>
.articles {
  background: #1d1f20;
  box-sizing: border-box;
  padding: 1.2rem 1.2rem;
  border-radius: .2rem;
  .articles-title {
    color: white;
    font-size: 1rem;
    margin-bottom: 1rem;
    span {
      border-radius: .1rem;
      background: #2c63ff;
      color: white;
      font-size: .75rem;
      margin: 0 .25rem 0 0;
      padding: .25rem .3rem;
      border-radius: .1rem;
      position: relative;
      top: -2px;
    }
  }

  .sub-title {
    margin-bottom: 1rem;
    font-size: .7rem;
    display: flex;
    .avatar-view {
      img {
        background: white;
        text-decoration: none;
        height: 16px;
        width: 16px;
        border-radius: 50%;
      }
    }

    .name-view {
      margin-left: .3rem;
      color: white;
    }

    .line-view {
      color: #2c63ff;
      margin: 0 .3rem;
    }
    .type-view {
      color: white;
    }
    .time-vie {
      color: #585c5f;
      text-align: left;
    }
    .flex-fill {
    flex: 1 1 auto;
    }
  }

  .big-img {
    width: 100%;
    height: 20rem;
    margin-bottom: 1rem;
    img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }
  }

  .content {
    overflow: hidden;
    color:#B1B1C1;
  }

  .hover-blue {
    &:hover {
        color: #2c63ff;
        cursor: pointer;
    }
  }
}

</style>