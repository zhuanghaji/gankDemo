<template>
  <div id="app">
    <Header></Header>
    <Content></Content>
  </div>
</template>
<script>
import Header from '@/components/Header.vue'
import Content from '@/components/Content.vue'
export default {
  name: "app",
  components: {
    Header,
    Content
  }
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
}

.container {
  width: 100%;
  padding-left: 15px;
  padding-right: 15px;
  margin-left: auto;
  margin-right: auto;
  box-sizing: border-box;
}

a {
  text-decoration: none;
}
a:link {
  text-decoration: none;
}
a:visited {
  text-decoration: none;
}
a:hover {
  text-decoration: none;
}
a:active {
  text-decoration: none;
}
</style>
