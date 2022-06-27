<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="10" md="8" lg="6" xl="5">
      <div id="chemViewer" style="width:100px;height:60px"
		  data-widget="Kekule.ChemWidget.Viewer2D" data-enable-toolbar="true" data-auto-size="false" data-padding="20"
		  data-toolbar-evoke-modes="[0]"
		  data-chem-obj="url(#)"></div>
    </v-col>
  </v-row>
</template>

<script>


export default {
  name: "TestPage",
  head () {
    return {
      link: [
        { id: 'サリチル酸', type: 'chemical/x-mdl-molfile', href: 'chemData/2D/サリチル酸.mol'}
      ]
    }
  }
  mounted() {
    var resId = 'url(#サリチル酸)';
      Kekule.IO.loadResourceData(resId, function(mol, success)
      {
        if (success)
        {
          console.log('Loading from ' + resId + ' Successful');
        }
        else
        {
          console.log('Loading from ' + resId + ' Failed');
        }
      });
    },

  };
</script>
