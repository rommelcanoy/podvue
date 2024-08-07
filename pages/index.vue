<script setup lang="ts">
useHead({
  title: 'Podvue - Home',
  meta: [
    { name: 'description', content: 'Podvue Podcast landing page website.' },
  ],
  link: [
    { rel: 'icon', type: 'image/png', href: '/logo.png' }
  ],
})
</script>
<template>
    <div>
        <SectionsHomeHeroSection/>
        <SectionsHomeLatestPodcast/>
        <SectionsHomePopularPodcasts/>
        <SectionsAboutPodux/>
        <SectionsWhyUs/>
        <SectionsCallToAction/>
    </div>
</template>