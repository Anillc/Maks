<template>
  <main class="page">
    <slot name="top" />

    <Content class="theme-default-content" />
    <PageEdit />

    <PageNav v-bind="{ sidebarItems }" />

    <slot name="bottom" />
    
    <div class="gitalk-out">
        <div ref="gitalk"></div>
    </div>
  </main>
</template>

<script>
import PageEdit from '@theme/components/PageEdit.vue'
import PageNav from '@theme/components/PageNav.vue'

import 'gitalk/dist/gitalk.css'
import Gitalk from 'gitalk'

export default {
  components: { PageEdit, PageNav },
  props: ['sidebarItems'],
  mounted() {
    let gitalk = new Gitalk({
      clientID: '596e5e499fdeccbda70e',
      clientSecret: 'a34c47d89879fa27cf31d124f62492a1e6ca6ede',
      repo: 'Maks',
      owner: 'kou-yi',
      admin: ['kou-yi'],
      id: location.pathname,
      distractionFreeMode: false
    })
    gitalk.render(this.$refs.gitalk)
  }
}
</script>

<style lang="stylus">
@require '../styles/wrapper.styl'

.page
  padding-bottom 2rem
  display block

</style>

<style scoped>
.gitalk-out {
    max-width: 720px;
    margin: 0 auto;
    position: relative;
    z-index: 1;
}
@media (max-width: 720px) {
    .gitalk-out {
        width: 90%;
    }
}
</style>
