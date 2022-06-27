<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="10" md="8" lg="6" xl="5">
      <div id="composer" style="width:600px;height:400px" data-widget="Kekule.Editor.Composer" data-chem-obj="url(#Benzene)"></div>
      <div id="chemViewer" style="width:100%;height:650px"
		  data-widget="Kekule.ChemWidget.Viewer2D" data-enable-toolbar="true" data-auto-size="false" data-padding="20"
		  data-toolbar-evoke-modes="[0]"
		  data-chem-obj="url(#サリチル酸)"></div>
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
  name: "TestPage",
  head() {
    return {
      link: [
        {
          src: 'chemData/2D/サリチル酸.mol',
          body: true,
          defer: false,
          hid: 'サリチル酸',
          type: 'chemical/x-mdl-molfile',
          id: 'サリチル酸'
        },
      ],
    };
  },
  mounted() {
    
  },

};
</script>
