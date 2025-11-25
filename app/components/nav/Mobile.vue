<script setup lang="ts">
    const { menuItems } = defineProps(['menuItems'])
    const showMenu = ref(false)

    const toggleMenu = () => {
        showMenu.value = !showMenu.value
    }
</script>

<template>
    <nav class="relative">
        <button class="w-10 h-10 text-white bg-gray-500 flex items-center justify-center cursor-pointer" @click="toggleMenu">
            <Icon name="uil:bars" />
        </button>

        <ul class="absolute top-[calc(100%+15px)] right-0 bg-white w-[100vw] -mr-5" v-if="showMenu">
            <li class="group" v-for="menuItem in menuItems" :key="menuItem.id">
                <a class="block h-[56px] px-3 uppercase text-gray-500 flex items-center gap-2 border-b border-gray-2500" :href="menuItem.link">
                    <span>{{ menuItem.name }}</span>
                    <Icon v-if="menuItem.children.length > 0" name="uil:angle-down" />
                </a>
                <ul class="bg-gray-600 hidden group-hover:block" v-if="menuItem.children.length > 0">
                    <li v-for="subMenuItem in menuItem.children" :key="subMenuItem.id">
                        <a class="block h-[81px] w-[240px] px-3 uppercase text-white flex items-center" :href="subMenuItem.link">{{ subMenuItem.name }}</a>
                    </li>
                </ul>
            </li>
        </ul>
    </nav>
</template>