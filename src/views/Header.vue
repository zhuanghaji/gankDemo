<template>
  <div id="header">
    <div class="container">
        <ul>
            <li>首页</li>
            <li>妹纸</li>
            <li>干货</li>
            <li>专题</li>
            <li>Flutter</li>
            <li>API</li>
            <li>留言</li>
        </ul>
        <div id="title">
            干货集中营
        </div>
    </div>
  </div>
</template>

<script>
export default {

}
</script>

<style lang='less'>
#header {
    height: 8rem;
    width: 100%;
    background: black;
    align-items: center;
    display: flex;
    ul {
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
    #title {
        font-weight: 400;
        font-size: 2.5rem;
        color: white;
        order: 1;
    }
}    



</style>