<script lang="ts" setup>
import InvolveHubTextLogo from '../components/logos/InvolveHubTextLogo.vue';
import IsotypeLogo from '../components/logos/IsotypeLogo.vue';
import { IconBuildingLine } from '@iconify-prerendered/vue-clarity';

const menuItems = [
    {
        item: 1,
        text: 'Dashboard',
        route: '/dashboard',
    },
    {
        item: 2,
        text: 'Companies',
        route: '/companies',
    },
    {
        item: 3,
        text: 'Account',
        route: '/account',
    },
    {
        item: 4,
        text: 'Logout',
        route: '/logout',
    },
];
</script>
<template>
    <div class="grid grid-cols-[22rem,1fr] grid-rows-[1fr] w-full h-full">
        <nav
            class="sidebar-menu shadow-uniform-xs dark:shadow-surface-50/20 p-3 flex flex-col justify-between"
        >
            <div class="w-full flex justify-center items-center p-6">
                <InvolveHubTextLogo class="w-56 h-auto max-w-full" />
            </div>
            <div
                class="w-full rounded-xl shadow-uniform-xs dark:shadow-surface-50/20 flex flex-row items-center gap-4 py-2 px-8"
            >
                <div class="w-20 h-20 p-3">
                    <IsotypeLogo class="w-full h-auto" />
                </div>
                <span class="text-base font-normal">SuperAdmin User 1</span>
            </div>
            <div
                class="w-full text-center p-2 rounded-md bg-primary-50 dark:bg-primary-300/10 text-primary dark:text-primaryDim-300 font-semibold mt-6 flex items-center justify-center gap-3"
            >
                <IconBuildingLine class="w-auto h-5" />
                <span>Super Admin</span>
            </div>
            <div class="w-full mt-6">
                <ul class="flex flex-col gap-4">
                    <li
                        class="w-full relative"
                        v-for="item in menuItems"
                        :key="item.item"
                    >
                        <RouterLink
                            :to="item.route"
                            class="block w-full py-2 px-9 rounded-lg font-normal border-l-4 border-transparent"
                            active-class="bg-surface-500/10 text-primary dark:text-primaryDim-300 !border-primary"
                            >{{ item.text }}</RouterLink
                        >
                    </li>
                </ul>
            </div>
            <div class="grow"></div>
            <div class="w-full flex flex-col my-4">
                <button class="btn-contrast">Add company</button>
            </div>
        </nav>
        <header class="mobile-header sm:hidden"></header>
        <main class="main-content col-span-1 p-6">
            <RouterView v-slot="{ Component, route }">
                <Transition
                    enter-active-class="duration-300 ease-in-out"
                    enter-from-class="transform opacity-0"
                    enter-to-class="opacity-100"
                    leave-active-class="duration-300 ease-in-out"
                    leave-from-class="opacity-100"
                    leave-to-class="transform opacity-0"
                    mode="out-in"
                    appear
                >
                    <div class="w-full" :key="route.path">
                        <component :is="Component" />
                    </div>
                </Transition>
            </RouterView>
        </main>
    </div>
</template>
<style lang="css" scoped>
</style>
