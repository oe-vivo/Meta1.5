<template>
    <v-card
      class="mx-auto"
      max-width="344"
      
    >
      <v-img
        :src="url"
        cover
      ></v-img>
  
      <v-card-title>
        Lugares Random
      </v-card-title>
  
      <v-card-subtitle>
        No creeras el numero 2
      </v-card-subtitle>
  
      <v-card-actions>
        <v-btn
          color="orange-lighten-2"
          variant="text"
          @click="cambiarImagen"
        >
          Siguiente
        </v-btn>
  
        <v-spacer></v-spacer>
  
        <v-btn
          :icon="show ? 'mdi-chevron-up' : 'mdi-chevron-down'"
          @click="show = !show"
        ></v-btn>
      </v-card-actions>
  
      <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>
  
          <v-card-text>
            A poco no tilin
          </v-card-text>
        </div>
      </v-expand-transition>
    </v-card>
  </template>
  <script setup>
    import { ref } from 'vue';
    const show =ref(false);
    const imagenesUrl=ref("https://random.imagecdn.app/300/400");
    const url=ref(imagenesUrl.value);
    async function cambiarImagen(){
      const response= await fetch(imagenesUrl.value,{
        method:"GET",
        headers: {
          "Content-type": "application/json"
        }
      });
      //const data=await response.json();
      console.log("Cambiando Imagen");
      console.log(response.url);
      url.value=response.url;
    }
  </script>