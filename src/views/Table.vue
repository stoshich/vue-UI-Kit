<script setup>
  import { computed, ref } from 'vue';
  import BaseTable from '../components/Table/BaseTable.vue';
  import TableRow from '../components/Table/TableRow.vue';
  import TableColumn from '../components/Table/TableColumn.vue';
  import Button from '@/components/Button.vue'



  const tableHead = ['Id', 'Author', 'Title', 'Cover', '']
  const tableSizeColumns = '50px 1fr 2fr 150px 140px'

  const sortField = ref('id')
  const typeSort = ref('asc')

  const books = ref([
  {
    id: 1,
    author: 'Dmitry Glukhovsky',
    title: 'Metro 2033',
    image: 'https://m.media-amazon.com/images/W/IMAGERENDERING_521856-T2/images/I/81pNKLAG-cL._AC_UY436_FMwebp_QL65_.jpg',
    bg: '#FFA26B'
  },
  {
    id: 12,
    author: 'James Clear',
    title: 'Atomic Habits: An Easy',
    image: 'https://m.media-amazon.com/images/P/0735211299.01._SCLZZZZZZZ_SX500_.jpg',
    bg: '#00C48C'
  },
  {
    id: 2,
    author: 'J. K. Rowling',
    title: 'Harry Potter and the Order of the Phoenix',
    image: 'https://m.media-amazon.com/images/W/IMAGERENDERING_521856-T2/images/I/51bZujlJxlL._SX218_BO1,204,203,200_QL40_FMwebp_.jpg',
    bg: '#00C48C'
  }
])

const booksSorting = computed(() => {
  return books.value.sort((a, b) => {
    let modifier = 1
    if(typeSort.value === 'desc') modifier = -1
    if(a[sortField.value] < b[sortField.value]) return -1 * modifier
    if(a[sortField.value] > b[sortField.value]) return 1 * modifier
    return 0

  })
})

const setSort = (name) => {
  if(sortField.value === name) {
    if(typeSort.value === 'asc') {
      typeSort.value = 'desc'
    } else {
      typeSort.value = 'asc'
    }
  } else {
    sortField.value = name
  }
}
</script>

<template>
  <div class="heading-1">Table</div>
  <base-table
    :head="tableHead"
    :column-templates="tableSizeColumns"
    @sorting="setSort"
  >
  <table-row
    v-for="book in booksSorting"
    :key="book.id"
    :column-templates="tableSizeColumns"
    :bg-row="book.bg"
  >
    <table-column :column-title="tableHead[0]">
      {{ book.id }}
    </table-column>
    <table-column :column-title="tableHead[1]">
      {{ book.author }}
    </table-column>
    <table-column :column-title="tableHead[2]">
      {{ book.title }}
    </table-column>
    <table-column :image="true" :src-image="book.image"/>
    <table-column>
      <Button label="Read online"></Button>
    </table-column>
  </table-row>
  </base-table>
</template>