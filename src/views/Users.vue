<template>
  <div class="home">
        <v-row class="text-left">
            <v-col cols="10">
                <h1 class="green--text text--darken-2">
                    <v-icon large color="green darken-2">mdi-account-outline</v-icon>
                    {{user.name}}
                </h1>
            </v-col>
        </v-row>
        <v-row class="text-left">
            <v-col cols="2">
                <img :src="photo" style="max-width: 100%">
            </v-col>
            <v-col cols="10" class="text-left">
                <p>
                    Website: <a href="..." target="_blank">{{user.website}}</a>
                </p>
                <p>
                    E-mail: <a href="mailto:...">{{user.email}}</a>
                </p>
                <p>
                    City: {{user.city}}
                </p>
                <p>
                    Workplace: {{user.company}}
                </p>
            </v-col>
        </v-row>
  </div>
</template>

<script>
export default {
    props: [
        'user'
    ],
    mounted() {
        if (this.user == '') this.$router.push('/login');
    }
};
</script>