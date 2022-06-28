<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="10" md="8" lg="6" xl="5">
    <script id="chem2" type="chemical/x-mdl-molfile" src="../static/chemData/2D/benzenoanthracene.mol"></script>
    <script id="chem1" type="chemical/x-mdl-molfile">
tetraene.mol
  ChemDraw03051520032D

 20 24  0  0  0  0  0  0  0  0999 V2000
   -0.0768   -1.4017    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
   -0.9213   -1.6654    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
   -0.4893   -1.0167    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    0.3858   -0.6301    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
   -0.0768   -0.3260    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    0.3858    0.2855    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    1.0652   -1.0151    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    0.6365   -1.7204    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    1.2318   -2.1264    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    1.9598   -2.1264    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    2.4046   -1.4793    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    1.8902   -1.0151    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
   -1.3532   -0.9148    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
   -2.0002   -1.1574    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
   -2.4046   -1.7204    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
   -1.6767   -1.9646    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
   -0.4246    0.5007    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
   -0.2629    1.5101    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    0.3357    2.1264    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    0.5864    1.2270    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
  1  2  1  0      
  2  3  2  0      
  3  4  1  0      
  1  5  1  0      
  5  6  2  0      
  4  6  1  0      
  4  7  1  0      
  1  8  1  0      
  7  8  2  0      
  8  9  1  0      
  9 10  2  0      
 10 11  1  0      
 11 12  2  0      
  7 12  1  0      
  3 13  1  0      
 13 14  2  0      
 14 15  1  0      
 15 16  2  0      
  2 16  1  0      
  5 17  1  0      
 17 18  2  0      
 18 19  1  0      
 19 20  2  0      
  6 20  1  0      
M  END
</script>
    <span id="viewer2D1" style="display:block" data-widget="Kekule.ChemWidget.Viewer2D"
      data-chem-obj="url(#chem1)" data-predefined-setting="basic" data-auto-size="true"></span>
     <span id="viewer2D1" style="display:block" data-widget="Kekule.ChemWidget.Viewer2D"
      data-chem-obj="url(#chem2)" data-predefined-setting="basic" data-auto-size="true"></span>
     <span id="viewer2D1" style="display:block" data-widget="Kekule.ChemWidget.Viewer2D"
      data-chem-obj="url(#benzene)" data-predefined-setting="basic" data-auto-size="true"></span>
    </v-col>
  </v-row>
</template>

<script>


export default {
  name: "TestPage",
  head() {
      return {
        script: [
        {
          src: '../static/chemData/2D/benzenoanthracene.mol',
          body: true,
          defer: true,
          hid: 'benzene',
          id: 'benzene'
          callback: () => {
            console.log('example js loaded');
          },
        },
      ],
      }
    },
  mounted() {
  
    },

  };
</script>
