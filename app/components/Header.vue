<script setup lang="ts">
    const menuItems = [
        { 
            id: 1,
            name: "Africa",
            link: '#',
            children: []
        },
        { 
            id: 2,
            name: "Asia",
            link: '#',
            children: []
        },
        { 
            id: 3,
            name: "Americas",
            link: '#',
            children: [
                { 
                    id: 1,
                    name: "North America",
                    link: '#',
                    children: []
                },
                { 
                    id: 2,
                    name: "South America",
                    link: '#',
                    children: []
                },
            ]
        },
        { 
            id: 4,
            name: "Europe",
            link: '#',
            children: []
        },
        { 
            id: 5,
            name: "About Us",
            link: '#',
            children: []
        },
        { 
            id: 6,
            name: "Contact",
            link: '#',
            children: []
        }
    ]
</script>

<template>
  <header class="absolute top-0 left-0 z-10 w-full flex justify-center px-5">
    <div class="flex flex-col items-center justify-between flex-row w-full lg:flex-col lg:justify-center">
        <div class="py-4 w-[120px] lg:w-fit">
            <NuxtLink to="/">
                <img
                    src="/img/logo.png"
                    alt="Logo"
                >
            </NuxtLink>
        </div>
        <NavDesktop class="hidden lg:flex" :menu-items="menuItems" />
        <NavMobile class="flex lg:hidden" :menu-items="menuItems" />
    </div>
  </header>
</template>