<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="10" md="8" lg="6" xl="5">
      <div id="composer" style="width:600px;height:400px" data-widget="Kekule.Editor.Composer" data-chem-obj="url(#Benzene)"></div>
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
  mounted() {
    let cmlData = '<cml xmlns="http://www.xml-cml.org/schema"><molecule id="m1"><atomArray><atom id="a3" elementType="C" x2="11.103486989694215" y2="44.922666666666665"/><atom id="a2" elementType="C" x2="11.103486989694215" y2="44.12266666666667"/><atom id="a4" elementType="C" x2="10.410666666666666" y2="45.32266666666666"/><atom id="a1" elementType="C" x2="10.410666666666666" y2="43.72266666666667"/><atom id="a5" elementType="C" x2="9.717846343639115" y2="44.922666666666665"/><atom id="a6" elementType="C" x2="9.717846343639115" y2="44.12266666666667"/><atom id="a7" elementType="C" x2="11.796307312721764" y2="45.28"/><atom id="a10" elementType="O" x2="12.46938885071484" y2="44.847609848385886"/><atom id="a9" elementType="O" x2="11.834227399369258" y2="46.07910078652736"/></atomArray><bondArray><bond id="b2" order="S" atomRefs2="a3 a2"/><bond id="b3" order="D" atomRefs2="a3 a4"/><bond id="b7" order="S" atomRefs2="a3 a7"/><bond id="b1" order="D" atomRefs2="a2 a1"/><bond id="b4" order="S" atomRefs2="a4 a5"/><bond id="b6" order="S" atomRefs2="a1 a6"/><bond id="b5" order="D" atomRefs2="a5 a6"/><bond id="b9" order="S" atomRefs2="a7 a10"/><bond id="b8" order="D" atomRefs2="a7 a9"/></bondArray></molecule></cml>'
    let mol = Kekule.IO.loadFormatData(cmlData, 'cml');
  },

};
</script>
