<template>
  <div v-resize="onResize">
    <slot name="header"/>
    <slot name="toolbar"/>
    <slot name="filter"/>
    <div ref="resizableDiv">
      <slot name="table" :table-height="tableHeight"/>
    </div>
  </div>
</template>

<script>
  import { Resize } from "vuetify/lib/directives";

  export default {
    name: "lynx-base-resizable-list-page",
    data() {
      return {
        tableHeight: 0
      }
    },
    directives: {
      Resize
    },
    props: {
      footerHeight: {
        type: Number,
        default: 59
      }
    },
    methods: {
      onResize () {
        this.tableHeight = window.innerHeight - this.$refs.resizableDiv.getBoundingClientRect().y - this.footerHeight;
      },
    }
  }
</script>

<style scoped>

</style>