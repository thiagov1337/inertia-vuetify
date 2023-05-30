<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import AppLayoutSideBar from '@/Layouts/AppLayoutSideBar.vue';
import { VDataTable } from 'vuetify/labs/VDataTable'

import { ref }from 'vue';

const search = ref();
const itemsPerPage = ref(5);
const headers = [
    {title: 'Id', align: 'center', key: 'id' },
    {title: 'Name', align: 'center', key: 'name' },
    {title: 'Email', align: 'center', key: 'email' },
    {title: 'Photo URL', align: 'center', key: 'profile_photo_url'},
];

defineProps({
    users: Object
});

</script>

<template>
   <AppLayoutSideBar>
            <v-card class="m-2 rounded-md">
                <v-card-title>
                Users
                <v-spacer></v-spacer>
                <v-text-field
                    v-model="search"
                    append-icon="mdi-magnify"
                    label="Search"
                    single-line
                    hide-details
                ></v-text-field>
                </v-card-title>
                <v-data-table
                    :headers="headers"
                    :items="users"
                    :search="search"
                    v-model:items-per-page="itemsPerPage" 
                    class="elevation-1 table-sm"
                ></v-data-table>
            </v-card>
    </AppLayoutSideBar>
</template>

<style scoped>

.table-sm{
    font-size: 0.875rem;
}
</style>