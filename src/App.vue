<script setup>
import { onMounted, ref } from 'vue';

const CLIENT_ID = '938435001813-29ojlvuikjs5k2qffbbsaqnpaar4s9bp.apps.googleusercontent.com'
const API_KEY = 'AIzaSyCni9woxa4LM2u2OIZsnIciLGFCxE9NbxA'
const DISCOVERY_DOC = '1nflz2pA9pOFTyZ28DY63KJ8RBZNZht-Wwjg-cemeAvU';

const menu = ref()

onMounted(() => {
  fetch(`https://sheets.googleapis.com/v4/spreadsheets/${DISCOVERY_DOC}/values/${'aguachingones'}?key=${API_KEY}`)
    .then(response => response.json())
    .then(data => {
      menu.value = data.values
    })
    .catch(error => console.error('Error:', error));
})

</script>

<template>
  {{ JSON.stringify(menu) }}
</template>