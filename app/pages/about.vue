<script setup lang="ts">
const { data: page } = await useAsyncData('about', () => {
  return queryCollection('about').first()
})
if (!page.value) {
  throw createError({
    statusCode: 404,
    statusMessage: 'Page not found',
    fatal: true
  })
}

const { global } = useAppConfig()

useSeoMeta({
  title: page.value?.seo?.title || page.value?.title,
  ogTitle: page.value?.seo?.title || page.value?.title,
  description: page.value?.seo?.description || page.value?.description,
  ogDescription: page.value?.seo?.description || page.value?.description
})
</script>

<template>
  <UPage v-if="page" class="-mt-15 -pb-20">
    <!-- slightly narrower like a centered card -->
    <UPageSection :ui="{ container: 'max-w-3xl mx-auto' }">
      <!-- Header -->
      <header
        class="flex flex-col md:flex-row items-center justify-center gap-4 py-6"
      >
        <div class="text-center md:text-left">
          <h1 class="text-3xl font-semibold">
            {{ page.title }}
          </h1>
          <p class="mt-2 text-sm text-muted max-w-xl">
            {{ page.description }}
          </p>
        </div>

        <img
          :src="global.picture?.light"
          :alt="global.picture?.alt"
          class="w-24 h-24 sm:w-28 sm:h-28 rounded-full object-cover shadow-md ring ring-default ring-offset-3 ring-offset-(--ui-bg)"
        />
      </header>

      <!-- Your markdown content -->
      <div class="-mt-7 text-sm text-muted">
        <MDC :value="page.content" unwrap="p" />
      </div>

      <!-- Your carousel -->
      <div class="mt-10">
        <UCarousel
          v-slot="{ item }"
          dots
          arrows
          :items="page.images"
          :ui="{ item: 'basis-1/2 sm:basis-1/3 md:basis-1/4 px-2' }"
        >
          <img
            :src="item.src"
            :alt="item.alt"
            width="360"
            height="360"
            class="rounded-lg object-cover h-48 w-48 mx-auto"
          >
        </UCarousel>
      </div>
    </UPageSection>
  </UPage>
</template>

<style scoped>
</style>
