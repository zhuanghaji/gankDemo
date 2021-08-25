<template>
  <div class="contentMenu">
    <ul>
      <li v-for="(item, index) of menuList" :key="item._id">
        <button
          :class="{ selected: menuSelectedIndex == index }"
          @click="onContentMenuClick(index)"
        >
          {{ item.title }}
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "contentMenu",
  data() {
    return {
      menuSelectedIndex: 0,
      menuList: [
        {
          _id: "1",
          title: "妹纸",
          type: "Girl",
        },
      ],
    };
  },
  methods: {
    onContentMenuClick(index) {
      this.menuSelectedIndex = index;
      this.$emit("onMenuChange", this.menuList[index].type);
    },
  },
  created() {
    this.$axios({
      url: "https://gank.io/api/v2/categories/Article",
      methods: "get",
    }).then((result) => {
      this.menuList = this.menuList.concat(result.data.data);
    });
  },
};
</script>

<style lang='less' scoped>
.contentMenu {
  margin-bottom: 1rem;
  padding-bottom: 0.5rem;
  box-sizing: border-box;
}

ul {
  display: block;
  list-style: none;
  list-style-type: disc;
  margin-block-start: 1em;
  margin-block-end: 1em;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
}
li {
  display: inline-block;
  box-sizing: border-box;

  button {
    color: #b1b1c1;
    cursor: pointer;
    font-size: 0.75rem;
    position: relative;
    background: transparent;
    border: 1px solid transparent;
    padding: 0.3125rem 0.75rem 0.25rem 0.75rem;
    font-weight: 400;
    overflow: visible;
    line-height: 1.5;
    border-radius: 3px;
    text-decoration: none;
    &:hover {
      color: #2c63ff;
      text-decoration: underline;
    }
  }

  .selected {
    background-color: #2c63ff;
    border-color: #2c63ff;
    color: white;
    &::after {
      position: absolute;
      top: 100%;
      right: 0;
      left: 0;
      width: 14px;
      margin: auto;
      content: "";
      border-top: 5px solid #2c63ff;
      border-right: 7px solid transparent;
      border-bottom: 5px solid transparent;
      border-left: 7px solid transparent;
      box-sizing: border-box;
    }
    &:hover {
      color: white;
      text-decoration: none;
    }
  }
}
</style>