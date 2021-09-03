<template>
  <div id="nav">
    <div id="header" class="container">
      <ul class="main-menu">
        <li class="main-menu-item">首页</li>
        <li class="main-menu-item">妹纸</li>
        <li class="main-menu-item main-menu-item-ganhuo">
          干货<i class="iconfont arrow">&#xe614;</i>

          <ul class="sub-menu">
            <li>Android</li>
            <li>Flutter</li>
            <li>IOS</li>
          </ul>
        </li>
        <li class="main-menu-item">专题</li>
        <li class="main-menu-item">Flutter</li>
        <li class="main-menu-item">API</li>
        <li class="main-menu-item">留言</li>
      </ul>
      <div id="title">干货集中营</div>

      <ul class="right-menu">
        <li><i class="icon iconfont">&#xe653;</i></li>
        <li><i class="icon iconfont">&#xe612;</i></li>
        <li><i class="icon iconfont">&#xe610;</i></li>

        <div class="btn-group">
          <a class="btn-group-left">注册</a><a class="btn-group-right">登录</a>
        </div>
      </ul>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang='less'>
#nav {
  width: 100%;
  height: 8rem;
  background: black;
  margin: 0;
  padding: 0dp;
}
#header {
  height: 100%;
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
    transition: 0.3s color;
    position: relative;

    &:hover {
      color: rgb(82, 82, 82);
      cursor: pointer;
      transition: 0.3s color;
    }
    .main-menu-item {
      font-size: 0.9rem;
      width: 3.2rem;
      line-height: 2rem;
      text-align: center;
      &:hover {
        color: #2c63ff;
        cursor: pointer;
      }
    }
    .main-menu-item-ganhuo {
      &:hover {
        .arrow {
          transform: rotate(180deg);
        }
        .sub-menu {
          opacity: 1;
        }
      }
    }
  }
  .right-menu {
    display: flex;
    list-style: none;
    order: 2;
    .icon {
      font-size: 20px !important;
    }
    li {
      color: #b1b1c1;
      width: 3rem;
      line-height: 2rem;

      &:hover {
        color: #2c63ff;
        cursor: pointer;
      }
    }

    .btn-group {
      a {
        display: inline-block;
        width: 3rem;
        line-height: 2rem;
        height: 2rem;
        font-size: 0.8rem;
        text-align: center;
        box-sizing: border-box;
      }

      .btn-group-left {
        border: #2c63ff solid 1px;
        border-right: none;
        border-radius: 0.3rem 0 0 0.3rem;
        color: #2c63ff;
        &:hover {
          background-size: auto;
          background: #2c63ff;
          color: white;
        }
      }

      .btn-group-right {
        border: #2c63ff solid 1px;
        background: #2c63ff;
        color: white;
        border-radius: 0 0.3rem 0.3rem 0;
        &:hover {
          background-size: auto;
          background: #17317a;
          border: #17317a solid 1px;
        }
      }
    }
  }
  #title {
    font-weight: 400;
    font-size: 2.5rem;
    color: white;
    order: 1;
  }
  .arrow {
    display: inline-block;
    transition: 0.5s;
    color: gray !important;
    margin-left: 0.2rem;
  }
  .sub-menu {
    transition: 0.4s;
    opacity: 0;
    position: absolute;
    top: 1.8rem;
    left: 6rem;
    list-style: none;
    width: 8rem;
    background: rgb(77, 77, 77);
    z-index: 99;
    li {
      transition: 1s;
      color: rgb(192, 192, 192);
      text-align: left;
      box-sizing: border-box;
      padding: 0 0.5rem;
      width: 100%;
      height: 2.3rem;
      line-height: 2.3rem;

      &::before {
        content: "\00A0\00A0";
      }

      &:hover {
        transition: 0.4s;

        color: white;
        &::before {
          content: "\2014\00A0";
          color: rgb(22, 22, 63);
        }
      }
    }
    li:nth-last-child(-n + 2) {
      border-top: white solid 1px;
    }
  }
}
</style>