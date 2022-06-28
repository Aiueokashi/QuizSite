<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="10" md="8" lg="6" xl="5">
    <img src="/v.png" />
    <script id="サリチル酸" type="chemical/x-mdl-molfile" src="/chemData/2D/サリチル酸.mol"></script>
     <span id="viewer2D1" style="display:block" data-widget="Kekule.ChemWidget.Viewer2D"
      data-chem-obj="url(#サリチル酸)" data-predefined-setting="basic" data-auto-size="true"></span>
    </v-col>
  </v-row>
</template>

<script>


export default {
  name: "TestPage",
  mounted() {
  
    },

  };
</script>
