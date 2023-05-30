<script setup>
import { ref } from 'vue';
import SideBarLink from '@/Components/SideBarLink.vue';

const drawer = ref(true);
const rail = ref(true);
const items = ref([
    { title: 'Home', icon: 'mdi-home-city' },
    { title: 'My Account', icon: 'mdi-account' },
    { title: 'Users', icon: 'mdi-account-group-outline' },
]);
</script>

<template>
    <v-card>
        <div class="min-h-screen bg-gray-100">
            <v-layout>
                <link href="https://cdn.jsdelivr.net/npm/@mdi/font@5.x/css/materialdesignicons.min.css" rel="stylesheet">

                <v-navigation-drawer v-model="drawer" :rail="rail" permanent @click="rail = false">
                    <v-list-item :prepend-avatar="$page.props.auth.user.profile_photo_url" :title="$page.props.auth.name"
                        nav>
                        <template v-slot:append>
                            <v-btn variant="text" icon="mdi-chevron-left" @click.stop="rail = !rail"></v-btn>
                        </template>
                    </v-list-item>

                    <v-divider></v-divider>

                    <v-list density="compact" nav>
                        <SideBarLink :href="route('home')" :active="route().current('home')">
                            <v-list-item prepend-icon="mdi-home-city" title="Home" value="home"></v-list-item>
                        </SideBarLink>

                        <SideBarLink :href="route('account')" :active="route().current('account')">
                            <v-list-item prepend-icon="mdi-account" title="My Account" value="account"></v-list-item>
                        </SideBarLink>

                        <SideBarLink :href="route('users')" :active="route().current('users')">
                            <v-list-item prepend-icon="mdi-account-group-outline" title="Users" value="users"></v-list-item>
                        </SideBarLink>
                    </v-list>
                </v-navigation-drawer>

                <v-main>
                    <slot />
                </v-main>
            </v-layout>
        </div>
    </v-card>
</template>
