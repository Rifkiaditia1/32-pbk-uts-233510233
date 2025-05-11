<template>
    <button @click="klik">Klik Saya</button>
  </template>
  
  <script>
  export default {
    methods: {
      klik() {
        alert('Tombol diklik');
      }
    }
  }
  </script>
  
  <style>
  button {
    background-color: blue;
    color: white;
  }
  </style>