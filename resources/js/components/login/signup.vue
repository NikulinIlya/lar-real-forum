<template>
    <v-container>
        <v-form @submit.prevent="signup">
            <v-text-field
                    v-model="form.name"
                    type="Name"
                    label="text"
                    required
            ></v-text-field>

            <v-text-field
                    v-model="form.email"
                    type="email"
                    label="E-mail"
                    required
            ></v-text-field>

            <v-text-field
                    label="Password"
                    v-model="form.password"
                    type="password"
                    required
            ></v-text-field>

            <v-text-field
                    label="Password"
                    v-model="form.password_confirmation"
                    type="password"
                    required
            ></v-text-field>

            <v-btn color="green" type="submit">
                Sign Up
            </v-btn>

            <router-link to="/login">
                <v-btn color="blue">Login</v-btn>
            </router-link>
        </v-form>
    </v-container>
</template>

<script>
    export default {
        data() {
            return {
                form: {
                    name: null,
                    email: null,
                    password: null,
                    password_confirmation: null
                }
            }
        },
        methods: {
            signup() {
                axios.post('/api/auth/signup', this.form)
                    .then(res => User.responseAfterLogin(res))
                    .catch(error => console.log(error.response.data))
            }
        }
    }
</script>