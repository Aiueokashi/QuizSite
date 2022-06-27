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
         <v-img :src="item.imgl" 
                :aspect-ratop="16/9" 
                height="9vw" 
                min-height="100px"
                width="16vw" 
                min-width="160px" 
                class="ma-0 pa-0"
        ></v-img>
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
        },
        { text: '化学式', value: 'formula' },
        { text: '別名', value: 'alias' },
        { text: '画像', value: 'img' },
      ],
      items: aromaticCompounds,
    }
  },
}
</script>
