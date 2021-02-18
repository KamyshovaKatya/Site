<template>
  <v-app>
   <div id="nav">
      <router-link to="/">Дом | </router-link>
      <router-link v-if="user == ''" to="/login">Вход | </router-link>
      <router-link v-else :to="`/users/${user.myId}`">{{user.name}} | </router-link>
      <router-link to="/register">Регистрация</router-link>
    </div>
    <v-main>
     <v-content class="px-12 py-3">
        <v-container fluid>
         <router-view :user="user" v-on:login="updateUser"/>
        </v-container>
     </v-content>
    </v-main>
  </v-app>
</template>

<script>
export default {
    name: 'App',
    data() {
        return {
            user: ''
        }
    },
    methods: {
        updateUser(data) {
            this.user = data;
        }
    }
};
</script>