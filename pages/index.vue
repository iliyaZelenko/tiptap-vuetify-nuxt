<template>
  <section>
    <h1 class="display-1">
      Tiptap Vuetify
    </h1>

    <v-alert type="info">
      This's an example of how to use with Nuxt.js
    </v-alert>

    <Editor />
  </section>
</template>

<script>
import Editor from '../components/Editor'

export default {
  components: {
    Editor
  }
}
</script>

