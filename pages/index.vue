<script setup>
    definePageMeta({
        path: "/:id?",
        keepalive: true,
    });

    const drawer = ref(true)

    const items = ref([
        {
            text: 'Dashboard',
            icon: 'mdi-view-dashboard-outline',
            to: '/dashboard',
        },
        {
            text: 'Team',
            icon: 'mdi-account-group',
            to: `/team`,
        },
        {
            text: 'Projects',
            icon: 'mdi-briefcase-outline',
            to: '/projects',
        },
    ]);

    function controlDrawer(drawerStatus) {
        drawer.value = drawerStatus;
    }

    const route = useRoute();
    const isActive = (path) => route.path === path


</script>

<template>
    <v-app>
        <v-layout>
            <v-navigation-drawer
                v-model="drawer"
                permanent
            >
                <div class="pa-2">
                    <v-btn icon="$vuetify" density="comfortable" variant="text" @click="controlDrawer(false)" />
                </div>
                <v-list density="compact" item-props nav >
                    <v-list-item
                        v-for="(item, i) in items"
                        :key="i"
                        :to="item.to"
                        :active="isActive(item.to)"
                    >
                        {{ item.text }}
                    </v-list-item>
                </v-list>
            </v-navigation-drawer>
            <v-main>
                <v-sheet>
                    <div class="pa-2" style="height: 64px">
                        <v-btn v-show="!drawer" icon="$vuetify" density="comfortable" variant="text" @click="controlDrawer(true)" />
                    </div>
                    <v-card class="mx-3 pa-3">
                        route: {{ route.path }}
                    </v-card>
                </v-sheet>
            </v-main>
        </v-layout>
    </v-app>
</template>