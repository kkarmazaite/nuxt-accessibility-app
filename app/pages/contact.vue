<script setup>
  const form = reactive({
    name: '',
    email: '',
    subject: '',
    message: ''
  })

  const errors = reactive({})
  const isSubmitted = ref(false)

  const validateForm = () => {
    errors.name = !form.name ? 'Please enter your name.' : ''
    errors.email = !form.email
      ? 'Please enter your email.'
      : !/^\S+@\S+\.\S+$/.test(form.email)
        ? 'Please enter a valid email address.'
        : ''

    return !errors.name && !errors.email
  }

  const handleSubmit = (e) => {
    e.preventDefault()
    isSubmitted.value = true

    if (validateForm()) {
      alert('Form submitted!')
    }
  }
</script>

<template>
  <div>
    <section>
      <Hero
        :is-homepage="false" 
        :headline="'Contact Us'" 
        :bg-image="'/img/contact-bg-img.jpg'"
      />
    </section>

    <section class="container py-14">
      <div class="flex flex-col gap-5 lg:gap-14">
          <div class="flex flex-col text-center gap-5 mb-14 text-gray-700">
            <h2 class="text-3xl font-serif lg:text-5xl">Stay updated with our journies</h2>
            <p>Proin gravida nibh vel velit auctor aliquet. Aenean sollicitudin, lorem quis bibendum auctor, nisi elit consequat ipsum, nec sagittis sem nibh id elit. Duis sed odio sit amet nibh vulputate cursus a sit amet mauris. Morbi accumsan ipsum velit. Duis sed odio sit amet nibh vulputate cursus a sit amet mauris. Morbi accumsan ipsum velit. Nam nec tellus a odio tincidunt auctor a ornare odio. </p>
          </div>

          <div>
            <h3 class="text-2xl font-serif lg:text-3xl text-center mb-10 text-gray-700">Send us a message</h3>

            <div
                v-if="isSubmitted && Object.values(errors).some(Boolean)"
                class="bg-red-100 border-l-4 border-red-600 text-red-700 p-3 mb-4"
                role="alert"
              >
                Please fix the errors below.
            </div>

            <form @submit="handleSubmit" novalidate class="flex flex-col gap-5" aria-describedby="contactDescription">
              <p id="contactDescription">
                Fill out the form below and we will get back to you as soon as possible.
              </p>

                <div>
                  <label for="name" class="font-medium">Your Name *</label>
                  <input
                    id="name"
                    v-model="form.name"
                    @input="isSubmitted && validateForm()"
                    :aria-invalid="!!errors.name"
                    :aria-describedby="errors.name ? 'name-error' : null"
                    required
                    class="bg-gray-100 border rounded w-full p-2"
                  >
                  <p
                    v-if="errors.name"
                    id="name-error"
                    class="text-red-600 text-sm mt-1"
                    role="alert"
                  >
                    {{ errors.name }}
                  </p>
              </div>

              <div>
                <label for="email" class="font-medium">Your Email *</label>
                <input
                  id="email"
                  type="email"
                  v-model="form.email"
                  @input="isSubmitted && validateForm()"
                  :aria-invalid="!!errors.email"
                  :aria-describedby="errors.email ? 'email-error' : null"
                  autocomplete="email"
                  required
                  class="bg-gray-100 border rounded w-full p-2"
                >
                <p
                  v-if="errors.email"
                  id="email-error"
                  class="text-red-600 text-sm mt-1"
                  role="alert"
                >
                  {{ errors.email }}
                </p>
              </div>

              <div>
                <label for="subject" class="font-medium">Subject</label>
                <input id="subject" type="text" v-model="form.subject" autocomplete="on"
                  class="bg-gray-100 border border-gray-300 rounded w-full p-2 text-gray-800 focus:outline focus:outline-2 focus:outline-blue-500">
              </div>

              <div>
                <label for="message" class="font-medium">Your Message</label>
                <textarea id="message" v-model="form.message" rows="4" class="bg-gray-100 border border-gray-300 rounded w-full p-2 text-gray-800 focus:outline focus:outline-2 focus:outline-blue-500"></textarea>
              </div>

              <button type="submit" class="bg-gray-700 text-white uppercase py-4 px-8 w-fit">
                Send Message
              </button>
            </form>
          </div>
        </div>
    </section>
  </div>
</template>
