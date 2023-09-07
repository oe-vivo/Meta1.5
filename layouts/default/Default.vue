<template>
  
        
  <SideBar />  
  
  <v-app>
    <default-view />
    
  </v-app>

</template>

<script setup>
    import SideBar from '@/components/sidebar.vue' 
    import DefaultBar from './AppBar.vue'
    import DefaultView from './View.vue'
</script>
