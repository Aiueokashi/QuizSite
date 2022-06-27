<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="10" md="8" lg="6" xl="5">
      <ChemistryTableComponent />
    </v-col>
  </v-row>
</template>

<script>
import ChemistryTableComponent from '../components/ChemistryTable'
export default {
  name: 'IndexPage',

  components: {
    ChemistryTableComponent,
  },
}
</script>
