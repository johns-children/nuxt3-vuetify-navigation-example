<script setup>
    const drawer = ref(true)

    const items = ref([
        {
            title: 'Dashboard',
            prependIcon: 'mdi-view-dashboard-outline',
            link: true,
        },
        {
            title: 'Team',
            prependIcon: 'mdi-account-group',
            link: true,
        },
        {
            title: 'Projects',
            prependIcon: 'mdi-briefcase-outline',
            link: true,
        },
        {
            title: 'Calendar',
            prependIcon: 'mdi-calendar',
            link: true,
        },
        {
            title: 'Reports',
            prependIcon: 'mdi-file-chart-outline',
            link: true,
        },
    ]);

    function controlDrawer(drawerStatus) {
        drawer.value = drawerStatus;
    }

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
                <v-list density="compact" item-props :items="items" nav />
            </v-navigation-drawer>
            <v-main>
                <v-sheet>
                    <div class="pa-2" style="height: 64px">
                        <v-btn v-show="!drawer" icon="$vuetify" density="comfortable" variant="text" @click="controlDrawer(true)" />
                    </div>
                    <div>main main main</div>
                </v-sheet>
            </v-main>
        </v-layout>
    </v-app>
</template>