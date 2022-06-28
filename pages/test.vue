<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="10" md="8" lg="6" xl="5">
    <script id="chem2" type="chemical/x-mdl-molfile" src="static/chemData/2D/benzenoanthracene.mol"></script>
    <script id="chem1" type="chemical/x-mdl-molfile">
Marvin  06041312482D          

 10 10  0  0  0  0            999 V2000
    4.7971  -23.1983    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    5.5115  -23.6108    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    4.7971  -22.3733    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    6.2260  -22.3734    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    6.2260  -23.1984    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    5.5115  -21.9608    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    6.9404  -21.1359    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0
    6.9404  -21.9610    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    7.6548  -22.3734    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0
    6.9404  -23.6107    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0
  2  1  2  0  0  0  0
  1  3  1  0  0  0  0
  4  8  1  0  0  0  0
  4  5  2  0  0  0  0
  2  5  1  0  0  0  0
  5 10  1  0  0  0  0
  6  4  1  0  0  0  0
  3  6  2  0  0  0  0
  8  7  2  0  0  0  0
  8  9  1  0  0  0  0
M  END
</script>
    <span id="viewer2D1" style="display:block" data-widget="Kekule.ChemWidget.Viewer2D"
      data-chem-obj="url(#chem1)" data-predefined-setting="basic" data-auto-size="true"></span>
     <span id="viewer2D1" style="display:block" data-widget="Kekule.ChemWidget.Viewer2D"
      data-chem-obj="url(#chem2)" data-predefined-setting="basic" data-auto-size="true"></span>
    </v-col>
  </v-row>
</template>

<script>


export default {
  name: "TestPage",
  head() {
      return {
        link: [
          {
            hid: 'サリチル酸',
            id: 'サリチル酸',
            type: 'chemical/x-mdl-molfile',
            href: 'static/chemData/2D/サリチル酸.mol'
          },{
            hid: 'benzene',
            id: 'benzene',
            type: 'chemical/x-mdl-molfile',
            href: 'static/chemData/2D/benzenoanthracene.mol'
          },
        ]
      }
    },
  mounted() {
  
    },

  };
</script>
