<template>
  <div id="app">
    <component :is='layout'>
      <router-view/>
    </component>
  </div>
</template>

<script>
import EditorLayout from '@/layouts/EditorLayout'

export default {
  computed: {
    layout() {
      return (this.$route.meta.layout || 'editor') + '-layout'
    }
  },
  components: {
    EditorLayout
  }
}
</script>
