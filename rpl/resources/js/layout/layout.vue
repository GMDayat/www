<template>
    <v-app id="inspire">
        <v-navigation-drawer v-model="drawer">
            <v-list density="compact">
                <v-list-subheader><b>ADU DECK?.app</b></v-list-subheader>
                <Link href="/admin" as="div">
                <v-list-item v-if="user.level== 'admin'" active-color="primary" to="/admin">
                    <template v-slot:prepend>
                        <v-icon icon="mdi-format-align-justify"></v-icon>
                    </template>

                    <v-list-item-title>Dashboard</v-list-item-title>
                </v-list-item>
                </Link>

                <Link href="/petugas" as="div">
                <v-list-item v-if="user.level== 'petugas'" active-color="primary" to="/petugas">
                    <template v-slot:prepend>
                        <v-icon icon="mdi-format-align-justify"></v-icon>
                    </template>

                    <v-list-item-title>Dashboard</v-list-item-title>
                </v-list-item>
                </Link>
                <Link v-if="user.level== 'admin'" href="/admin/user" as="div">
                <v-list-item active-color="primary" to="/admin/user">
                    <template v-slot:prepend>
                        <v-icon icon="mdi-account-group"></v-icon>
                    </template>

                    <v-list-item-title>All User</v-list-item-title>
                </v-list-item>
                </Link>
                <Link v-if="user.level == 'admin'" href="/admin/register" as="div">
                <v-list-item active-color="primary" to="/admin/user">
                    <template v-slot:prepend>
                        <v-icon icon="mdi-account"></v-icon>
                    </template>

                    <v-list-item-title>Add Masyarakat</v-list-item-title>
                </v-list-item>
                </Link>
            </v-list>
        </v-navigation-drawer>

        <v-app-bar>
            <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

            <v-toolbar-title>Halo {{ user.nama }}</v-toolbar-title>
            <v-spacer />
            <v-btn @click="logout">Logout</v-btn>
        </v-app-bar>

        <v-main>
            <v-container>
                <slot />
            </v-container>
        </v-main>
    </v-app>
</template>
<script>
import { router, Link } from '@inertiajs/vue3'
export default {
    components: {
        Link
    },
    data: () => ({ drawer: null }),
    computed:{
        user(){
            return this.$page.props.auth.user
        }
    },
    methods: {
        logout() {
            router.get('/logout');
        }
    }
}
</script>
<style>

</style>
