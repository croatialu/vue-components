<template>
  <div id="app">
    <!-- <TabHeader ></TabHeader> -->
    <TabHeaderCopy></TabHeaderCopy>
  </div>
</template>

<script>
import TabHeader from "./components/TabHeader"
import TabHeaderCopy from "./components/TabHeaderCopy"
export default {
  name: 'app',
  data () {
    return {
    }
  },
  components: {
    TabHeader,
    TabHeaderCopy
  }
}
</script>

<style>


html, body {
  width: 100%;
  height: 100%;
  overflow: hidden;
  margin: 0;
}

html {
  font-size: 100px;

}




body {
  font-size: .16rem;
}




</style>
