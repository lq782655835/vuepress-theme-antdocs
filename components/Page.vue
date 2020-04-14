<template>
  <main class="page">
    <slot name="top" />
    <article class="page-article">
      <Content class="theme-antdocs-content page-article__body"/>
      <Preview :src="previewURL" class="page-article__preview"/>
    </article>
    <PageEdit />

    <PageNav v-bind="{ sidebarItems }" />

    <slot name="bottom" />
  </main>
</template>

<script>
import PageEdit from '@theme/components/PageEdit.vue'
import PageNav from '@theme/components/PageNav.vue'
import Preview from '@theme/components/Preview.vue'
export default {
  components: { PageEdit, PageNav,Preview },
  props: ['sidebarItems'],
  computed: {
        previewURL() {
          return `${this.$themeConfig.phoneURL}#/${this.$page.title}`
        }
  }
}
</script>

<style lang="less">
@import '../styles/palette.less';
@import "../styles/wrapper.less";
.page {
  padding-bottom: 2rem;
  display: block;
  .page-article {
        display: flex;
        width: 100%;
        .page-article__body {
            flex: 1;
        }
        .page-article__preview {
            min-width: 320px;
            height: 580px;
            margin: 90px 30px 30px 30px;
        }
    }
}
@media (max-width: @MQMobile) {
  .page {
    margin-top: -@navbarHeight;
  }
}
</style>
