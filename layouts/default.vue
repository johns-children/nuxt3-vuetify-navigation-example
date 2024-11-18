<script setup>
    const items = [
        {
        text: 'Home',
        to: '/',
        },
        {
        text: 'Test',
        to: '/test',
        }
    ]

    const route = useRoute()
    const isActive = (path) => route.path === path

</script>
<template>
    <div>
        <v-layout>
            <v-app-bar class="px-3">
                <template v-slot:prepend>
                    <v-app-bar-title>Application</v-app-bar-title>
                    <div class="pl-10">
                        <NuxtLink
                            v-for="(item, i) in items"
                            :key="i"
                            :to="item.to"
                            class="mx-2 text-body-1 text-decoration-none"
                            :class="isActive(item.to) ? `text-blue` : `text-grey-darken-4`"
                        >
                            {{ item.text }}
                        </NuxtLink>
                    </div>
                </template>
            </v-app-bar>
            <v-main>
                <slot />
            </v-main>
        </v-layout>
    </div>
</template>
  