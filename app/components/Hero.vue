<template>
  <div class="h-[574px] lg:h-[890px] relative">
    <img
        class="w-full h-full object-cover"
        src="/img/hero-bg-img.jpg"
        alt="Hero"
    >
    <div class="absolute top-0 left-0 w-full h-full bg-gray-900 opacity-50"></div>
    <div class="absolute top-0 left-0 w-full h-full flex justify-center items-center">
        <div class="text-white text-center flex flex-col gap-5">
            <h1 class="text-4xl font-serif lg:text-8xl">Wanderlust Travel Blog</h1>
            <p class="text-base font-normal lg:text-2xl">Better to see something once than hear about it a thousand times!</p>

            <div class="flex gap-3 justify-center flex-col mt-20 lg:flex-row">
                <button class="py-4 px-6 text-gray-500 bg-white uppercase">Explore</button>
                <button class="py-4 px-6 text-gray-500 border border-white text-white uppercase">Journies</button>
            </div>
        </div>
    </div>
  </div>
</template>