<template>
    <div class="d-flex justify-center">
        <v-card width="600px" class="mt-12 pa-10">
            <v-card-title>
                Регистрация аккаунта
            </v-card-title>

            <v-text-field
                label="Введите логин"
                v-model="login"
                outlined
            ></v-text-field>

            <v-text-field
                label="Введите пароль"
                v-model="password"
                outlined
            ></v-text-field>
            
            <v-text-field
                label="Введите имя"
                v-model="name"
                outlined
            ></v-text-field>

            <v-text-field
                label="Введите сайт"
                v-model="website"
                outlined
            ></v-text-field>
            
            <v-text-field
                label="Введите почту"
                v-model="email"
                outlined
            ></v-text-field>

            <v-text-field
                label="Введите город"
                v-model="city"
                outlined
            ></v-text-field>
            
            <v-text-field
                label="Введите компанию"
                v-model="company"
                outlined
            ></v-text-field>

            <v-text-field
                label="Введите ссылку на фото"
                v-model="photo"
                outlined
            ></v-text-field>

            <v-btn @click="authenticate">
                Зарегистрироваться
            </v-btn>
        </v-card>
    </div>
</template>

<script>
// @ is an alias to /src
export default {
    data() {
        return {
            login: undefined,
            password: undefined,
            name: undefined,
            website: undefined,
            email: undefined,
            city: undefined,
            company: undefined,
            photo: undefined,
            storage: ''
        }
    },
    methods: {
        authenticate() {
            this.axios.get('http://37.77.104.246/api/jsonstorage/?id=18f2178656fc4c2c60fc48d7272de6dd')
                .then (
                    (response) => {
                        let users = response.data;
                        let user = {
                            login: this.login,
                            password: this.password,
                            name: this.name,
                            website: this.website,
                            email: this.email,
                            city: this.city,
                            company: this.company,
                            photo: this.photo,
                            myId: users.length + 1
                        };
                        users.push(user);
                        this.axios.put('http://37.77.104.246/api/jsonstorage/?id=18f2178656fc4c2c60fc48d7272de6dd', users);
                        this.$router.push('home')
                    }
                )
        }
    }
}
</script>