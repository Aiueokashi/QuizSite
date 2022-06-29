<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="10" md="8" lg="6" xl="5">
      <h1>クイズは左のメニューから<h1>
      <div id="peridicTable" data-widget="Kekule.ChemWidget.PeriodicTable" useMiniMode=true></div>
    </v-col>
  </v-row>
</template>

<script>
if (process.browser) {
  const THREE = require("three");
  const Raphael = require("raphael");
  var { Kekule } = require("kekule");
  Kekule.externalResourceManager.register("three.js", THREE);
  Kekule.externalResourceManager.register("Raphael.js", Raphael);
}
export default {
  name: 'IndexPage',

}
</script>
<style>
#peridicTable {
  float: left;
}
</style>
