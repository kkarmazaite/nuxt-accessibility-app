<script setup lang="ts">
    const { menuItems } = defineProps(['menuItems'])
    const showMenu = ref(false)
    const openSubmenu = ref<string | null>(null)

    const toggleMenu = () => {
    showMenu.value = !showMenu.value
    if (!showMenu.value) openSubmenu.value = null
    }

    const toggleSubmenu = (id: string) => {
    openSubmenu.value = openSubmenu.value === id ? null : id
    }

    const handleEscape = (e: KeyboardEvent) => {
    if (e.key === 'Escape') {
        showMenu.value = false
        openSubmenu.value = null
    }
    }

    onMounted(() => document.addEventListener('keydown', handleEscape))
    onUnmounted(() => document.removeEventListener('keydown', handleEscape))
</script>

<template>
  <nav aria-label="Mobile navigation" class="relative">
    <button
      class="w-10 h-10 text-white bg-gray-500 flex items-center justify-center cursor-pointer focus:ring-2"
      @click="toggleMenu"
      :aria-expanded="showMenu ? 'true' : 'false'"
      aria-controls="mobile-nav"
      aria-label="Open menu"
    >
      <Icon name="uil:bars" />
    </button>

    <ul
      v-if="showMenu"
      id="mobile-nav"
      role="menu"
      class="absolute top-[calc(100%+15px)] right-0 bg-white w-[100vw] -mr-5"
    >
      <li
        v-for="menuItem in menuItems"
        :key="menuItem.id"
        role="none"
      >
        <template v-if="menuItem.children.length">
          <button
            class="w-full flex justify-between items-center h-[56px] px-3 uppercase text-gray-700 border-b focus:ring-2"
            role="menuitem"
            @click="toggleSubmenu(menuItem.id)"
            :aria-expanded="openSubmenu === menuItem.id"
            aria-haspopup="true"
          >
            {{ menuItem.name }}
            <Icon name="uil:angle-down" />
          </button>

          <ul
            v-if="openSubmenu === menuItem.id"
            role="menu"
            class="bg-gray-600"
          >
            <li
              v-for="subMenuItem in menuItem.children"
              :key="subMenuItem.id"
              role="none"
            >
              <a
                class="block h-[56px] px-3 uppercase text-white flex items-center border-b focus:ring-2"
                role="menuitem"
                :href="subMenuItem.link"
              >
                {{ subMenuItem.name }}
              </a>
            </li>
          </ul>
        </template>

        <template v-else>
          <a
            class="block h-[56px] px-3 uppercase text-gray-700 flex items-center border-b focus:ring-2"
            role="menuitem"
            :href="menuItem.link"
          >
            {{ menuItem.name }}
          </a>
        </template>
      </li>
    </ul>
  </nav>
</template>
