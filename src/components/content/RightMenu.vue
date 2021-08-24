<template>
  <div id="right-menu">
    <div class="calendar">
      <a class="media" href="#">
        <span class="overlay"></span>
      </a>
      <div class="showData">
        <div class="date">
          <span class="day">10</span>
          <span class="my">10月,2021</span>
        </div>
        <div class="data">
          <span class="data-title">妹纸图36期</span>
          <span class="data-type">Random Girl</span>
        </div>
      </div>
      <a class="refresh"><i class="refresh-icon iconfont">&#xe618;</i></a>
    </div>

    <div id="hot" class="card">
      <div class="card-title">本周最🔥妹纸</div>
      <div class="media-group">
        <span class="media"></span>
        <span class="media"></span>
        <span class="media"></span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "rightMenu",
  data() {
    return {};
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
      left: 1.5rem;
      top: 1.2rem;
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

      .data-title {
        font-size: 1.2;
        cursor: pointer;
      }

      .data-type {
        width: auto;
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
    align-self: stretch;
    height: 10rem;
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
}

.card-title {
  color: white;
  font-size: 1rem;
}
</style>