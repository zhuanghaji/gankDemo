<template>
  <div>
    <ul>
        <li v-for="(item, index) of menuList" :key="index">
            <button>{{ item }}</button>
        </li>
    </ul>
  </div>
</template>

<script>
export default {
    name:'contentMenu',
    data() {
        return {
            menuSelectedIndex: 0,
            menuList: ['最新', '妹纸', '推荐', 'Android', 'Flutter', 'IOS', '前端', '后端', 'APP']
        }
    }
}
</script>

<style lang='less' scoped>
    ul {
        
        list-style: none;
    }
    li {
        display: inline-block;
    }
</style>