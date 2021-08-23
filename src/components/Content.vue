<template>
  <div>
    <Banner></Banner>
    <ContentMenu class="contentMenu"></ContentMenu>
  </div>
</template>

<script>
import Banner from '@/components/Banner.vue'
import ContentMenu from '@/components/ContentMenu.vue'

export default {
  name: 'content',
  components: { Banner, ContentMenu }
}
</script>

<style lang='less'>

</style>