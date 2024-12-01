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
    
    const isActive = (item) => {
        if (item.to === '/') {
            // `route.path` がどの `to` にも一致しない、または "/" の場合に `Home` を強調
            return !items.some(i => i.to === route.path) || route.path === '/';
        }
        // 通常の一致チェック
        return item.to === route.path;
    };

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
                            :class="isActive(item) ? `text-blue` : `text-grey-darken-4`"
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
  