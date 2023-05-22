<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import AppLayoutSideBar from '@/Layouts/AppLayoutSideBar.vue';
import { VDataTable } from 'vuetify/labs/VDataTable'

import { ref }from 'vue';

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
        <AppLayout>
            <div class="p-3 rounded-md">
                <v-data-table 
                    v-model:items-per-page="itemsPerPage" 
                    :headers="headers" 
                    :items="users" 
                    item-value="name"
                    class="elevation-1 table-sm">
                </v-data-table>
            </div>
        </AppLayout>
    </AppLayoutSideBar>
</template>

<style scoped>

.table-sm{
    font-size: 0.875rem;
}
</style>