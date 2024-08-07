<template>
  <section class="pt-16 relative">
    <div aria-hidden="true" class="absolute inset-y-0 w-44 left-0 hidden dark:flex">
      <div
        class="h-full md:h-1/2 lg:h-full w-full bg-gradient-to-tr opacity-40 dark:blur-2xl dark:from-[#570cac] dark:opacity-20">
      </div>
    </div>
    <div class="absolute top-14 inset-x-0 h-64 flex items-start">
      <div
        class="h-24 w-2/3 bg-gradient-to-br from-primary opacity-20 blur-2xl dark:from-[#570cac] dark:invisible dark:opacity-40">
      </div>
      <div
        class="h-20 w-3/5 bg-gradient-to-r from-[#8cd66a] opacity-40 blur-2xl dark:from-[#670ccf] dark:opacity-40">
      </div>
    </div>
    <AtomsContainer class-name="relative">
      <div class="flex justify-between pb-6 relative">
        <div class="">
          <AtomsTitle texte="Popular podcast" />
        </div>
        <div class="flex items-center min-w-max gap-5">
          <AtomsLinkBtn href="#" variant="primary">
            See all
          </AtomsLinkBtn>
        </div>
      </div>
      <div
        class="grid grid-cols-2 items-stretch sm:grid-cols-3 lg:grid-cols-4 gap-x-3 gap-y-10 sm:gap-x-5 sm:gap-y-8">
        <CardsPodCast 
          v-for="(podcast, index) in podcasts" 
          :key="index"
          :title="podcast.title"
          :href="podcast.href"
          :duration="podcast.duration"
          :cover-image="podcast.coverImage"
          :category="podcast.category"
          :created-at="podcast.createdAt"
          :description="podcast.description" 
        />
      </div>
    </AtomsContainer>
  </section>
</template>
<script>
export default {
  data() {
    return {
      podcasts: [
        {
          title: "Unlocking SEO Secrets",
          href: "#",
          duration: "24min",
          coverImage: "/images/8.webp",
          category: "SEO",
          createdAt: "2024-08-07",
          description: "Discover the hidden tactics that can boost your website's search engine rankings."
        },
        {
          title: "SEO Basics for Beginners",
          href: "#",
          duration: "30min",
          coverImage: "/images/7.webp",
          category: "SEO",
          createdAt: "2024-08-07",
          description: "Learn the fundamentals of SEO and start improving your site's visibility today."
        },
        {
          title: "Advanced SEO Strategies",
          href: "#",
          duration: "45min",
          coverImage: "/images/6.webp",
          category: "SEO",
          createdAt: "2024-08-07",
          description: "Take your SEO game to the next level with these advanced strategies."
        },
        {
          title: "SEO Myths Busted",
          href: "#",
          duration: "20min",
          coverImage: "/images/5.webp",
          category: "SEO",
          createdAt: "2024-08-07",
          description: "We debunk common SEO myths and provide you with the facts."
        },
        {
          title: "Local SEO Tips",
          href: "#",
          duration: "25min",
          coverImage: "/images/4.webp",
          category: "SEO",
          createdAt: "2024-08-07",
          description: "Optimize your website for local search with these effective tips."
        },
        {
          title: "SEO for E-commerce",
          href: "#",
          duration: "35min",
          coverImage: "/images/3.webp",
          category: "SEO",
          createdAt: "2024-08-07",
          description: "Boost your online store's visibility and sales with our SEO guide."
        },
        {
          title: "Mobile SEO Essentials",
          href: "#",
          duration: "28min",
          coverImage: "/images/2.webp",
          category: "SEO",
          createdAt: "2024-08-07",
          description: "Ensure your website is optimized for mobile users with these essentials."
        },
        {
          title: "Content Marketing and SEO",
          href: "#",
          duration: "40min",
          coverImage: "/images/1.webp",
          category: "SEO",
          createdAt: "2024-08-07",
          description: "Learn how to integrate content marketing with SEO to drive traffic."
        }
      ]
    }
  }
}
</script>