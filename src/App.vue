<template>
  <div id="app">
    <ItemSelectView/>
  </div>
</template>

<script>

import ItemSelectView from "@/views/ItemSelectView";
export default {
  name: 'App',
  components: {ItemSelectView}
}
</script>

<style lang="scss">
* {
  margin: 0;
  box-sizing: border-box;
}
</style>
