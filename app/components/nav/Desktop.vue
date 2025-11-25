<script setup lang="ts">
    const { menuItems } = defineProps(['menuItems'])
</script>

<template>
    <nav class="flex items-center">
        <ul class="flex">
            <li class="relative group" v-for="menuItem in menuItems" :key="menuItem.id">
                <a class="block h-[56px] px-3 uppercase text-white flex items-center justify-center gap-2" :href="menuItem.link">
                    <span>{{ menuItem.name }}</span>
                    <Icon v-if="menuItem.children.length > 0" name="uil:angle-down" />
                </a>
                <ul class="absolute top-full left-0 bg-gray-600 hidden group-hover:block" v-if="menuItem.children.length > 0">
                    <li v-for="subMenuItem in menuItem.children" :key="subMenuItem.id">
                        <a class="block h-[81px] w-[240px] px-3 uppercase text-white flex items-center" :href="subMenuItem.link">{{ subMenuItem.name }}</a>
                    </li>
                </ul>
            </li>
        </ul>
        <div class="text-white pl-3">
            <Icon name="uil:search" />
        </div>
    </nav>
</template>