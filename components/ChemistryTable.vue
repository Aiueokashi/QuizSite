<template>
  <v-card>
    <v-card-title>
      <v-text-field
        v-model="search"
        append-icon="mdi-magnify"
        label="Search"
        single-line
        hide-details
      ></v-text-field>
      <v-data-table
        :headers="headers"
        :items="items"
        :search="search"
        :items-per-page="10"
        :footer-props="footerProps"
        class="elevation-1"
      ><template v-slot:item.img="{ item }" >
        <script :id="item.name.split('/')[0]" type="chemical/x-mdl-molfile" :src="'/chemData/2D/' + item.name.split('/')[0] + '.mol'"></script>
       <span id="viewer2D1" style="display:block" data-widget="Kekule.ChemWidget.Viewer2D"
        :data-chem-obj="'url(#' + item.name.split('/')[0] + ')'" data-predefined-setting="basic" data-auto-size="true"></span>
    </template>
      </v-data-table>
    </v-card-title>
  </v-card>
</template>

<script>
import aromaticCompounds from '@/static/chemistry/aromatic_compounds.json'
export default {
  data() {
    return {
      search: '',
      footerProps: {
        'items-per-page-options': [10, 25, 50, 75, { text: 'All', value: -1 }],
      },
      headers: [
        {
          text: '化合物名',
          align: 'start',
          value: 'name',
          width: '30%'
        },
        { text: '化学式', value: 'formula', width: '20%' },
        { text: '構造式', value: 'img', width: '50%' },
      ],
      items: aromaticCompounds,
    }
  },
}
</script>
