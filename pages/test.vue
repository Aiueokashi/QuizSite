<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="10" md="8" lg="6" xl="5">
      <div id="chemViewer" style="width:500px;height:400px" data-widget="Kekule.ChemWidget.Viewer" data-chem-obj="url(#molecule)"></div>
    </v-col>
  </v-row>
</template>

<script>
import * as THREE from 'three';
import * as Raphael from 'raphael';
import {Kekule} from 'kekule';
Kekule.externalResourceManager.register('three.js', THREE);
Kekule.externalResourceManager.register('Raphael.js', Raphael);
  
export default {
  name: 'TestPage',
  mounted(){
    var cmlData = '<cml xmlns="http://www.xml-cml.org/schema"><molecule id="m1"><atomArray><atom id="a2" elementType="C" x2="7.493264658965051" y2="35.58088907877604"/><atom id="a3" elementType="O" x2="8.186084981992602" y2="35.18088907877604"/><atom id="a1" elementType="C" x2="6.800444335937501" y2="35.18088907877604"/></atomArray><bondArray><bond id="b2" order="S" atomRefs2="a2 a3"/><bond id="b1" order="S" atomRefs2="a2 a1"/></bondArray></molecule></cml>';
    var myMolecule = Kekule.IO.loadFormatData(cmlData, 'cml');
    chemViewer.setChemObj(myMolecule);
    var molecule = chemViewer.getChemObj();
    var cmlData = Kekule.IO.saveFormatData(obj, 'cml');
  },
}
</script>