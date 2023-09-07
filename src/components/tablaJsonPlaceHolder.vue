<template>
  <v-container>
      <v-row v-for="(userPost, index) in userPosts" :key="index">
        <v-col cols="4">
          <h2>Nombre de Usuario</h2>
          <p>{{ userPost.userName }}</p>
        </v-col>
        <v-col cols="4">
          <h2>Título del Post</h2>
          <p>{{ userPost.title }}</p>
        </v-col>
        <v-col cols="4">
          <h2>Contenido del Post</h2>
          <p>{{ userPost.body }}</p>
        </v-col>
      </v-row>
    </v-container>
  </template>
  
  <script>
  export default {
    data() {
      return {
        users: [],
        posts: [],
        userPosts: [], // Lista combinada de datos de usuarios y publicaciones
      };
    },
    created() {
      this.fetchUsers();
      this.fetchPosts();
    },
    methods: {
      async fetchUsers() {
        try {
          const response = await fetch('https://jsonplaceholder.typicode.com/users');
          const data = await response.json();
          this.users = data;
          this.combineUserData();
        } catch (error) {
          console.error('Error al obtener datos de usuarios:', error);
        }
      },
      async fetchPosts() {
        try {
          const response = await fetch('https://jsonplaceholder.typicode.com/posts');
          const data = await response.json();
          this.posts = data;
          this.combineUserData();
        } catch (error) {
          console.error('Error al obtener datos de publicaciones:', error);
        }
      },
      combineUserData() {
        // Combinar los datos de usuarios y publicaciones
        this.userPosts = this.users.map((user, index) => ({
          userName: user.name,
          title: this.posts[index] ? this.posts[index].title : '',
          body: this.posts[index] ? this.posts[index].body : '',
        }));
      },
    },
  };
  </script>
  