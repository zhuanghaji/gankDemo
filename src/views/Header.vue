<template>
  <div id="header" class="container">
    <ul class="main-menu">
      <li>首页</li>
      <li>妹纸</li>
      <li>干货</li>
      <li>专题</li>
      <li>Flutter</li>
      <li>API</li>
      <li>留言</li>
    </ul>
    <div id="title">干货集中营</div>

    <ul class="right-menu">
      <li></li>
      <li></li>
      <li></li>

    <div class="btn-group">
        <a>注册</a><a>登录</a>
    </div>
    </ul>
  </div>
</template>

<script>
export default {};
</script>

<style lang='less'>
#header {
  height: 8rem;
  width: 1140px;
  background: black;
  align-items: center;
  display: flex;
  .main-menu {
    margin-left: 2.5rem;
    margin-right: auto;
    order: 2;
    display: flex;
    list-style: none;
    color: white;
    &:hover {
      color: rgb(82, 82, 82);
      cursor: pointer;
    }
    li {
      width: 3rem;
      line-height: 2rem;
      text-align: center;
      &:hover {
        color: #2c63ff;
        cursor: pointer;
      }
    }
  }
  .right-menu {
    display: flex;
    list-style: none;
    order: 2;
    li {
      color: orange;
      font-size: 1.5rem;
      width: 3rem;
      line-height: 2rem;
      &::before {
        content: "\21AA";
      }
      &:hover {
        color: #2c63ff;
        cursor: pointer;
      }
    }

    .btn-group {
        user-select: none;
    }
  }
  #title {
    font-weight: 400;
    font-size: 2.5rem;
    color: white;
    order: 1;
  }
}
</style>