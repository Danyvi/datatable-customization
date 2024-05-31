<template>
  <v-data-table
    :headers="headers"
    :items="plants"
    density="compact"
    item-key="name"
    :row-props="rowProps"
  ></v-data-table>
</template>

<script setup>

import { ref } from 'vue'


const headers =  ref([
  { title: 'Plant', align: 'start', sortable: false, key: 'name' },
  { title: 'Light', align: 'end', key: 'light' },
  { title: 'Height', align: 'end', key: 'height' },
  { title: 'Pet Friendly', align: 'end', key: 'petFriendly' },
  { title: 'Price ($)', align: 'end', key: 'price' },
])

const plants = ref([
  {
    name: 'Fern',
    light: 'Low',
    height: '20cm',
    petFriendly: 'Yes',
    price: 20,
  },
  {
    name: 'Snake Plant',
    light: 'Low',
    height: '50cm',
    petFriendly: 'No',
    price: 35,
  },
  {
    name: 'Monstera',
    light: 'Medium',
    height: '60cm',
    petFriendly: 'No',
    price: 50,
  },
  {
    name: 'Pothos',
    light: 'Low to medium',
    height: '40cm',
    petFriendly: 'Yes',
    price: 25,
  },
  {
    name: 'ZZ Plant',
    light: 'Low to medium',
    height: '90cm',
    petFriendly: 'Yes',
    price: 30,
  },
  {
    name: 'Spider Plant',
    light: 'Bright, indirect',
    height: '30cm',
    petFriendly: 'Yes',
    price: 15,
  },
])

const rowProps = (data) => {
  return {
    style: {
      'background-color': getRowClass(data.item)
    }
  };
}

const getRowClass = (item) => {
  if (item.price < 20) {
    return 'rgba(255, 0, 0, 0.4)'
  } else if (item.price >= 20 && item.price <= 30) {
    return 'rgba(255, 255, 0, 0.4)'
  } else {
    return 'rgba(0, 255, 0, 0.4)'
  }
}
</script>

<style>
.v-data-table thead th {
  color: white;
  background-color: purple;
}
</style>