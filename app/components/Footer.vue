<template>
  <footer class="bg-black text-white text-sm font-light py-10">
    <div class="container">
      <div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-4 gap-10 mb-20 xl:mb-40 xl:gap-20">
        <div class="flex flex-col gap-10">
           <img
                src="/img/logo.png"
                class="self-start"
                alt="Logo"
            >
            <p>Nullam ac urna eu felis dapibus condimentum sit amet a augue. Sed non neque elit. Sed ut imperdiet nisi.</p>
        </div>

        <div class="flex flex-col gap-10">
          <h3 class="text-xl font-medium font-serif">Categories</h3>
          <ul class="flex flex-col gap-2">
            <li><a href="#">Africa (3)</a></li>
            <li><a href="#">Asia (5)</a></li>
            <li><a href="#">Europe (5)</a></li>
            <li><a href="#">North America (2)</a></li>
            <li><a href="#">South America (2)</a></li>
          </ul>
        </div>

        <div class="flex flex-col gap-10">
          <h3 class="text-xl font-medium font-serif">Recent Posts</h3>
          <ul class="flex flex-col gap-2">
            <li><a href="#">African Wildlife</a></li>
            <li><a href="#">Great Pyramids of Giza</a></li>
            <li><a href="#">Desert Safari in UAE</a></li>
            <li><a href="#">A day on the mountains</a></li>
            <li><a href="#">Christ The Savior – Rio de Janeiro</a></li>
            <li><a href="#">The City on Water – Venice</a></li>
          </ul>
        </div>

        <div class="flex flex-col gap-10">
          <h3 class="text-xl font-medium font-serif">Gallery</h3>
          <div class="grid grid-cols-3 gap-4">
            <img
                v-for="col in 6" :key="col"
                src="/img/footer-gallery-img.jpg"
                class="self-start border border-white"
                alt="Logo"
            >
          </div>
        </div>
      </div>

      <div class="flex flex-col md:flex-row gap-5 items-center justify-between">
        <div>Copyright © 2025 Wanderlust Travel Diary</div>
        <div>Powered by Wanderlust Travel Diary</div>
      </div>
    </div>
  </footer>
</template>