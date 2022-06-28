<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="10" md="8" lg="6" xl="5">
    <link id="benzene" type="chemical/x-mdl-molfile" href="static/chemData/benzene.mol" />
    <link id="サリチル酸" type="chemical/x-mdl-molfile" href="static/chemData/2D/サリチル酸.mol" />
    <span id="viewer2D1" style="display:block" data-widget="Kekule.ChemWidget.Viewer2D"
      data-chem-obj="url(#benzene)" data-predefined-setting="basic" data-auto-size="true"></span>
     <span id="viewer2D1" style="display:block" data-widget="Kekule.ChemWidget.Viewer2D"
      data-chem-obj="url(#サリチル酸)" data-predefined-setting="basic" data-auto-size="true"></span>
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
            href: '../static/chemData/2D/サリチル酸.mol'
          },{
            hid: 'benzene',
            id: 'benzene',
            type: 'chemical/x-mdl-molfile',
            href: '../static/chemData/benzene.mol'
          },
        ]
      }
    },
  mounted() {
  
    },

  };
</script>
