<template>
    <v-app id="inspire">
        <v-content>
            <v-container fluid fill-height>
                <div class="d-flex justify-center">
                    <v-flex xs12 sm8 md4>

                        <v-card elevation="2" width="400" height="550" class="mt-7">
                            <v-toolbar dark color="warning">
                                <v-toolbar-title>REGISTER</v-toolbar-title>
                            </v-toolbar>
                            <v-card-text>
                                <v-text-field label="Nama Lengkap" v-model="form.nama" outline
                                    :error-messages="errors.nama"></v-text-field>
                                <v-text-field label="NIK" v-model="form.nik" :error-messages="errors.nik"
                                    outline></v-text-field>
                                <v-text-field label="Nomor Telepon" v-model="form.tlp" outline
                                    :error-messages="errors.tlp"></v-text-field>
                                <v-text-field label="Username" v-model="form.username" outline
                                    :error-messages="errors.username"></v-text-field>
                                <v-text-field label="Password" v-model="form.password" outline
                                    :error-messages="errors.password"></v-text-field>
                                <!-- <v-select v-model="form.level" :items="['admin', 'petugas', 'masyarakat']" label="Level" variant="outlined" :error-messages="errors.level"></v-select> -->

                                </v-card-text>
                                <v-card-actions>
                                <v-spacer></v-spacer>

                                <v-btn color="primary" small x-small @click="login">login</v-btn>
                                <v-btn color="warning" small x-small @click="register">register</v-btn>
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
                nama: "",
                nik: "",
                tlp: "",
                username: "",
                password: "",
            }
        }
    },
    methods: {
        login() {
            router.get('/');
        },
        register() {
            //     router.visit('/', {
            //         method: 'post',
            //         data: {
            //             id: this.form.id,
            //             nama: this.form.nama,
            //             nik: this.form.nik,
            //             username: this.form.username,
            //             tlp: this.form.tlp,
            //             password: this.form.password,
            //             level: this.form.level,
            //         },
            //         preserveState: false,
            //         preserveScroll: false,
            //         onSuccess: () => {
            //             this.login();
            //         }
            // });
            router.post('/register', this.form)
        }
    }
};
</script>

<style></style>
