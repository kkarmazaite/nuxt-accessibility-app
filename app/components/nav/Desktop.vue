<script setup lang="ts">
    const { menuItems } = defineProps(['menuItems'])
    const openMenu = ref<string | null>(null)

    const toggleMenu = (id: string) => {
        openMenu.value = openMenu.value === id ? null : id
    }

    onMounted(() => {
        document.addEventListener('keydown', (e: KeyboardEvent) => {
            if (e.key === 'Escape') {
            openMenu.value = null
            }
        })
    })
</script>

<template>
  <nav class="flex items-center" aria-label="Main navigation">
    <ul class="flex" role="menubar">
      <li 
        v-for="menuItem in menuItems" 
        :key="menuItem.id" 
        class="relative group"
        role="none"
      >
        <button
          v-if="menuItem.children.length"
          class="block h-[56px] px-3 uppercase text-white flex items-center justify-center gap-2 focus:ring-2"
          role="menuitem"
          :aria-haspopup="true"
          :aria-expanded="openMenu === menuItem.id"
          @click="toggleMenu(menuItem.id)"
        >
          <span>{{ menuItem.name }}</span>
          <Icon name="uil:angle-down" />
        </button>

        <NuxtLink  
          v-else-if="menuItem.name === 'Contact'" 
          class="block h-[56px] px-3 uppercase text-white flex items-center justify-center gap-2 focus:ring-2"
          role="menuitem"
          to="/contact">
            {{ menuItem.name }}
        </NuxtLink>

        <a
          v-else
          class="block h-[56px] px-3 uppercase text-white flex items-center justify-center gap-2 focus:ring-2"
          role="menuitem"
          :href="menuItem.link"
        >
          {{ menuItem.name }}
        </a>

        <ul 
          v-if="menuItem.children.length"
          class="absolute top-full left-0 bg-gray-600"
          :class="{ 'hidden': openMenu !== menuItem.id }"
          role="menu"
        >
          <li 
            v-for="subMenuItem in menuItem.children" 
            :key="subMenuItem.id"
            role="none"
          >
            <a 
              class="block h-[81px] w-[240px] px-3 uppercase text-white flex items-center focus:ring-2"
              role="menuitem"
              :href="subMenuItem.link"
            >
              {{ subMenuItem.name }}
            </a>
          </li>
        </ul>
      </li>
    </ul>

    <button
      class="text-white pl-3 focus:ring-2"
      aria-label="Search"
    >
      <Icon name="uil:search" />
    </button>
  </nav>
</template>
