<script setup lang="ts">
const { data: page } = await useAsyncData('projects-page', () => {
  return queryCollection('pages').path('/projects').first()
})
if (!page.value) {
  throw createError({
    statusCode: 404,
    statusMessage: 'Page not found',
    fatal: true
  })
}

const { data: projects } = await useAsyncData('projects', () => {
  return queryCollection('projects').all()
})

const { global } = useAppConfig()

useSeoMeta({
  title: page.value?.seo?.title || page.value?.title,
  ogTitle: page.value?.seo?.title || page.value?.title,
  description: page.value?.seo?.description || page.value?.description,
  ogDescription: page.value?.seo?.description || page.value?.description
})
</script>

<template>
  <UPage v-if="page">
    <!-- Divider -->
    <div class="mt-20 mb-5 flex items-center justify-center gap-3 text-xs font-medium uppercase tracking-[0.2em] text-gray-400">
      <div class="h-px w-24 bg-gradient-to-r from-gray-200 to-transparent" />
      <span>Recent work</span>
      <div class="h-px w-24 bg-gradient-to-l from-gray-200 to-transparent" />
    </div>

    <!-- INVOICE APP -->
    <UPageSection
      class="-mt-28"
      description="A full-stack invoicing platform built with Nuxt 3, Supabase, and Postgres, focused on being fast, clean, and easy to use."
    >
      <template #title>
        <div>
          <h2 class="text-4xl font-semibold">Dueful</h2>
          <a
            href="https://dueful.digital"
            target="_blank"
            rel="noopener"
            class="text-primary text-sm font-medium hover:underline mt-3 block"
          >
            dueful.digital →
          </a>
        </div>
      </template>
      <div class="grid gap-8 lg:grid-cols-[minmax(0,2fr),minmax(0,3fr)] items-start -mt-2">
        <!-- MAIN DESCRIPTION -->
        <div class="space-y-6">
          <p class="text-sm text-muted">
           This is a lightweight invoicing software. The app handles multi-business accounts, customers, invoices with dynamic line items, due dates, notes, PDF exports, and a clean dashboard. I built it end-to-end: database schema, RLS rules, state management, and UI. Future roadmap includes email sending, reminder automation, and e-signature integration.
          </p>
          <div class="space-y-2">
            <h3 class="text-xs font-semibold tracking-wide uppercase text-muted">
              Core features
            </h3>
            <ul class="text-sm space-y-1 list-disc pl-4 text-muted">
              <li>Dashboard with revenue summaries and recent activity</li>
              <li>Customer management with search and quick actions</li>
              <li>Invoice creation flow with live totals and validation</li>
              <li>Status filtering: paid, unpaid, overdue, upcoming</li>
              <li>Print-ready PDF invoice generation</li>
              <li>Responsive UI optimized for mobile and desktop</li>
            </ul>
          </div>
          <!-- EXPANDABLE TECHNICAL DETAILS -->
          <details class="group rounded-lg border border-muted/60 bg-muted/10 px-4 py-3">
            <summary
              class="flex cursor-pointer items-center justify-between text-sm font-medium text-foreground list-none"
            >
              <span>Technical details</span>
              <UIcon
                name="i-lucide-chevron-down"
                class="size-4 transition-transform group-open:rotate-180"
              />
            </summary>

            <div class="mt-4 space-y-4 text-sm text-muted">

              <!-- Tech stack -->
              <div class="space-y-2">
                <h3 class="text-xs font-semibold tracking-wide uppercase text-muted">
                  Tech stack
                </h3>
                <ul class="text-sm space-y-1 list-disc pl-4 text-muted">
                  <li>Nuxt 3, Vue 3 (Composition API), Nuxt UI, Tailwind CSS</li>
                  <li>Supabase Auth, Postgres with Row-Level Security</li>
                  <li>Pinia for auth, invoices, customers, and business state</li>
                  <li>Puppeteer for server-side PDF generation</li>
                  <li>Email delivery via Postmark/SendGrid, Stripe for payments (planned)</li>
                </ul>
              </div>



      <!-- Architecture -->
<div class="space-y-2">
  <h3 class="text-xs font-semibold tracking-wide uppercase text-muted">
    Architecture
  </h3>
  <ul class="text-sm space-y-1 list-disc pl-4 text-muted">
    <li>Postgres relational schema (businesses, customers, invoices, items)</li>
    <li>Multi-tenant structure with strict RLS by <code class="font-mono text-xs">business_id</code></li>
    <li>Supabase Auth for identity + policy enforcement</li>
    <li>Pinia store for cross-page state and active business context</li>
    <li>Nuxt 3 server routes for secure actions (PDF generation, DB ops)</li>
    <li>Component-driven UI using Nuxt UI</li>
    <li>Puppeteer-based PDF generator with a dedicated template</li>
    <li>Clean folder architecture with composables, stores, and API routes</li>
  </ul>
</div>


            </div>
          </details>
        </div>

        <!-- RIGHT SIDE -->
        <div class="space-y-4">

          <img
            src="assets/images/invoice.gif"
            alt="Invoice app dashboard"
            class="rounded-xl border object-cover w-full aspect-video"
          >
        </div>
      </div>
    </UPageSection>

<!-- ART PORTFOLIO / PAYLOAD CMS STYLE -->
<UPageSection
  description="A content-driven art site built with Next.js and a custom TypeScript CMS, designed for fast publishing and clean presentation."
  class="-mt-20"
>
  <template #title>
    <div>
      <h2 class="text-4xl font-semibold">Artwork CMS + Portfolio</h2>
      <a
        href="https://henridumas.art"
        target="_blank"
        rel="noopener"
        class="text-primary text-sm font-medium hover:underline mt-3 block"

      >
        henridumas.art →
      </a>
    </div>
  </template>

  <div class="grid gap-8 lg:grid-cols-[minmax(0,2fr),minmax(0,3fr)] items-start">
    <!-- LEFT -->
    <div class="space-y-6">
      <p class="text-sm text-muted">
        A fast, minimal art portfolio built with Next.js and a structured content backend. New artworks, series, and pages can be added without touching code, keeping publishing simple and efficient.
      </p>

      <!-- Core features -->
      <div class="space-y-2">
        <h3 class="text-xs font-semibold tracking-wide uppercase text-muted">
          Core features
        </h3>
        <ul class="text-sm space-y-1 list-disc pl-4 text-muted">
          <li>Custom content types for artworks, series, and pages</li>
          <li>Rich text and media field support</li>
          <li>Responsive gallery rendering</li>
          <li>SEO-friendly routing</li>
        </ul>
      </div>

      <!-- EXPANDABLE TECHNICAL DETAILS -->
      <details class="group rounded-lg border border-muted/60 bg-muted/10 px-4 py-3">
        <summary
          class="flex cursor-pointer items-center justify-between text-sm font-medium text-foreground list-none"
        >
          <span>Technical details</span>
          <UIcon
            name="i-lucide-chevron-down"
            class="size-4 transition-transform group-open:rotate-180"
          />
        </summary>

        <div class="mt-4 space-y-4 text-sm text-muted">

          <!-- Tech stack -->
          <div class="space-y-2">
            <h3 class="text-xs font-semibold tracking-wide uppercase text-muted">
              Tech stack
            </h3>
            <ul class="text-sm space-y-1 list-disc pl-4 text-muted">
              <li>Next.js, React, TypeScript</li>
              <li>Custom CMS (Node.js + Express)</li>
              <li>Tailwind CSS for layout and typography</li>
              <li>API-driven content (REST/JSON)</li>
            </ul>
          </div>

          <!-- Architecture -->
          <div class="space-y-2">
            <h3 class="text-xs font-semibold tracking-wide uppercase text-muted">
              Architecture
            </h3>
            <ul class="text-sm space-y-1 list-disc pl-4 text-muted">
              <li>CMS defines structured schema</li>
              <li>Next.js statically generates public pages</li>
              <li>Incremental revalidation on content change</li>
            </ul>
          </div>

        </div>
      </details>
    </div>

    <!-- RIGHT SIDE -->
    <div class="space-y-4">
      <img
        src="assets/images/payload.gif"
        alt="Artwork CMS and portfolio preview"
        class="rounded-xl border object-cover w-full aspect-video"
      >
    </div>
  </div>
</UPageSection>


  </UPage>
</template>
