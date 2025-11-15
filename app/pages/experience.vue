<script setup lang="ts">
useSeoMeta({
  title: 'My Experience – Luc Dumas',
  ogTitle: 'My Experience – Luc Dumas',
  description: 'My experience as a freelance full-stack engineer and software engineer at WeVideo.',
  ogDescription: 'My experience as a freelance full-stack engineer and software engineer at WeVideo.'
})
</script>

<template>
  <UPage>
    <UPageSection :ui="{ container: 'max-w-4xl mx-auto' }">
      <!-- Title -->
      <header class="text-center">
        <h1 class="text-3xl font-semibold">
          My Experience
        </h1>
      </header>


      <!-- Experience entries -->
      <div class="mt-12 space-y-10">
        <!-- Union Web Solutions -->
        <section>
          <div class="flex flex-col sm:flex-row sm:items-baseline sm:justify-between gap-1">
            <h2 class="text-base font-semibold">
              Union Web Solutions, Freelance Full-Stack Engineer
            </h2>
            <p class="text-sm text-muted">
              August 2025 - Present
            </p>
          </div>

          <ul class="mt-3 list-disc pl-5 text-sm text-muted space-y-1">
            <li>
              Develop custom web applications and sites using React, Next.js, TypeScript, and Postgres, with headless CMSs for content management.
            </li>
            <li>
              Implement features including authentication, payments, and content workflows tailored to small and medium-sized businesses.
            </li>
          </ul>
        </section>

        <!-- WeVideo / PlayPosit -->
        <section>
          <div class="flex flex-col sm:flex-row sm:items-baseline sm:justify-between gap-1">
            <h2 class="text-base font-semibold">
              WeVideo, Software Engineer
            </h2>
            <p class="text-sm text-muted">
              August 2022 - July 2025
            </p>
          </div>

          <ul class="mt-3 list-disc pl-5 text-sm text-muted space-y-1">
            <li>
              Built and maintained full-stack features across a Vue + Node.js/Express/MySQL stack, contributing to several core microservices.
            </li>
            <li>
              Upgraded PlayPosit from Vue 2 → Vue 3, a large-scale migration across multiple microservices that improved maintainability and stability.
            </li>
            <li>
              Integrated PlayPosit into the WeVideo ecosystem by rewriting the standalone app into WeVideo’s suite and assisting in the migration of backend services from Express/MySQL to Java/Oracle, collaborating with backend teams.
            </li>
            <li>
              Contributed to the full rewrite of the PlayPosit app in React, building the combined WeVideo + PlayPosit platform and enabling seamless integration with WeVideo’s video editor.
            </li>
            <li>
              Implemented and maintained LTI integrations with external learning management systems, enabling wide adoption by schools and enterprises.
            </li>
            <li>
              Developed and maintained 10+ video player integrations on top of video.js, supporting diverse media workflows and use cases.
            </li>
            <li>
              Integrated AI-powered features using the ChatGPT API to enhance client interactions and automate workflows.
            </li>
          </ul>
        </section>
      </div>
    </UPageSection>
  </UPage>
</template>

<style scoped>
@keyframes experience-line {
  0% {
    width: 0%;
  }
  100% {
    width: 100%;
  }
}

.animate-experience-line {
  animation: experience-line 2.5s ease-in-out infinite alternate;
}
</style>
