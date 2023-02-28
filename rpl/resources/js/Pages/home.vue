<template>
    <v-app id="inspire">
        <v-content>
            <v-container fluid fill-height>
                <div class="d-flex justify-center">
                    <v-flex xs12 sm8 md4>

                        <v-card elevation="2" width="400" height="315" class="mt-15">
                            <v-toolbar dark color="primary">
                                <v-toolbar-title>LOGIN</v-toolbar-title>
                            </v-toolbar>
                            <v-card-text>
                                <v-form>
                                    <v-text-field label="Username" outline v-model="form.username"
                                        :error-messages="errors.username"></v-text-field>
                                    <v-text-field label="Password" type="password" v-model="form.password" outline
                                        :error-messages="errors.password"></v-text-field>
                                </v-form>
                            </v-card-text>
                            <v-card-actions>
                                <v-spacer></v-spacer>
                                <v-btn color="warning" small x-small @click="register">register</v-btn>
                                <v-btn color="primary" small x-small @click="login">login</v-btn>
                            </v-card-actions>
                        </v-card>

                    </v-flex>
                </div>
            </v-container>
        </v-content>
    </v-app>
</template>

<script>
import { router } from '@inertiajs/vue3'
export default {
    props: {
        errors: Object
    },
    data() {
        return {
            form: {
                username: "",
                password: ""
            }
        };
    },
    methods: {
        login() {
            router.post('/login', this.form);
        },
        register() {
            router.get('/register');
        }
    },
};
</script>
