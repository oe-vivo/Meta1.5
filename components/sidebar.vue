<template>
    <div>
      <v-layout>
        <v-navigation-drawer
          expand-on-hover
          rail
          style="z-index: 1000;"
        >
          <v-list>
            <v-list-item
              
              title="Octavio Vivo"
              subtitle="octavio.vivo@uabc.edu.mx"
            ></v-list-item>
          </v-list>
  
          <v-divider></v-divider>
  
          <v-list density="compact" nav>
            <router-link to="/">
              <v-list-item prepend-icon="mdi-home-circle" title="Pagina Principal" value="myfiles"></v-list-item>
            </router-link>
            <router-link to="/tabla">
              <v-list-item prepend-icon="mdi-table" title="Tabla" value="shared"></v-list-item>
            </router-link>
          </v-list>
        </v-navigation-drawer>
  
        <v-main style="height: 300px"></v-main>
      </v-layout>
    </div>
  </template>