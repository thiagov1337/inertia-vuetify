<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import AppLayoutSideBar from '@/Layouts/AppLayoutSideBar.vue';

import { VTable } from 'vuetify/lib/components/index.mjs';

defineProps({
    users: Object
});

</script>

<template>
    <AppLayoutSideBar>
        <AppLayout>
            <div class="p-3 rounded-md">
                <v-table class="border table-small">
                    <template v-slot:default>
                        <thead>
                            <tr>
                                <th class="text-uppercase">
                                    ID
                                </th>
                                <th class="text-center text-uppercase">
                                    Name
                                </th>
                                <th class="text-center text-uppercase">
                                    Email
                                </th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr v-for="user in users" :key="user.id">
                                <td>{{ user.id }}</td>
                                <td class="text-center">
                                    {{ user.name }}
                                </td>
                                <td class="text-center">
                                    {{ user.email }}
                                </td>
                            </tr>
                        </tbody>
                    </template>
                </v-table>
            </div>
        </AppLayout>
    </AppLayoutSideBar>
</template>

<style scoped>
.table-small {
    font-size: 0.875rem;
}
</style>