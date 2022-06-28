<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="10" md="8" lg="6" xl="5">
    <span id="viewer2D1" style="display:block" data-widget="Kekule.ChemWidget.Viewer2D"
      data-chem-obj="../static/chemData/benzene.mol" data-predefined-setting="basic" data-auto-size="true"></span>
     <span id="viewer2D1" style="display:block" data-widget="Kekule.ChemWidget.Viewer2D"
      data-chem-obj="../static/chemData/2D/サリチル酸.mol" data-predefined-setting="basic" data-auto-size="true"></span>
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
