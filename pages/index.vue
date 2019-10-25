<template>
  <div class="editor-wrap">
    <header>header</header>
    <section>
      <component-bar></component-bar> <!--chloe-->
      <preview-frame></preview-frame> <!--mary-->
      <edit-frame></edit-frame> <!--daisy-->
    </section>
    <footer>footer</footer>
  </div>
</template>

<script>
import ComponentBar from '~/components/editor/component-bar'
import PreviewFrame from '~/components/editor/preview-frame'
import EditFrame from '~/components/editor/edit-frame'
export default {
  components: {
    ComponentBar,
    PreviewFrame,
    EditFrame,
  }
}
</script>

<style scoped>
  .editor-wrap {

  }
</style>

