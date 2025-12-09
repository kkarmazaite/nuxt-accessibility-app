<template>
  <div>
    <section>
      <Hero 
        :is-homepage="true" 
        :headline="'Wanderlust Travel Blog'" 
        :text="'Better to see something once than hear about it a thousand times!'"  
        :bg-image="'/img/hero-bg-img.jpg'"
        :buttons="['explore', 'journies']"/>
    </section>

    <section>
      <TextBlock />
    </section>
  </div>
</template>
