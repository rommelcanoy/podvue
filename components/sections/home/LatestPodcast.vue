<template>
    <section class="pt-20 md:pt-24 relative">
        <AtomsContainer>
            <div class="flex justify-between items-center pb-6">
                <div class="">
                    <AtomsTitle texte="Latest Podcast" />
                </div>
                <div class="flex items-center min-w-max relative">
                    <AtomsLinkBtn href="#" variant="primary">
                        Explore more
                    </AtomsLinkBtn>
                </div>
            </div>
            <div class="relative">
                <!--  -->
                <div 
                    class="flex absolute top-1/2 -left-5 -translate-y-1/2 z-10 transition duration-300 ease-linear" 
                    :class="prevIsVisible?'visible opacity-100':'insisible opacity-0'" 
                    
                    >
                    <AtomsSwiperNavButton @click="scrollToLeft()">
                        <IconsPrevIco />
                    </AtomsSwiperNavButton>
                </div><!--  -->
                <div  
                    class="flex absolute top-1/2 -right-5 -translate-y-1/2 z-10 transition duration-300 ease-linear" 
                    :class="nextIsVisible?'visible opacity-100':'insisible opacity-0'">
                    <AtomsSwiperNavButton @click="scrollToRight()">
                        <IconsNextIco />
                    </AtomsSwiperNavButton>
                </div>

                <!-- <div data-slide-recent @scroll="initScroll()"
                    class="flex items-stretch gap-5 overflow-hidden overflow-x-auto invisible-scroll">
                    <div
                        class=" w-11/12 min-w-[91.666667%] xs:w-80 xs:min-w-[20rem] md:w-1/3 md:min-w-[33.333333%] lg:w-1/4 lg:min-w-[25%]">
                        <CardsRecentPod title="How to hack a website with Html in simple way" duration="23min" href="#"
                            cover-image="/images/sidebiew.webp" />
                    </div>

                    <div
                        class=" w-11/12 min-w-[91.666667%] xs:w-80 xs:min-w-[20rem] md:w-1/3 md:min-w-[33.333333%] lg:w-1/4 lg:min-w-[25%]">
                        <CardsRecentPod title="5 Principales you must know for writting clear code" duration="1h:22min" href="#"
                            cover-image="/images/podCast.webp" />
                    </div>

                    <div
                        class=" w-11/12 min-w-[91.666667%] xs:w-80 xs:min-w-[20rem] md:w-1/3 md:min-w-[33.333333%] lg:w-1/4 lg:min-w-[25%]">
                        <CardsRecentPod title="Make you website request secure than you could mind" duration="12min" href="#"
                            cover-image="/images/sidebiew.webp" />
                    </div>

                    <div
                        class=" w-11/12 min-w-[91.666667%] xs:w-80 xs:min-w-[20rem] md:w-1/3 md:min-w-[33.333333%] lg:w-1/4 lg:min-w-[25%]">
                        <CardsRecentPod title="How to get started with desktop developpement" duration="50min" href="#"
                            cover-image="/images/sidebiew.webp" />
                    </div>
                </div> -->

                <div data-slide-recent @scroll="initScroll()"
                    class="flex items-stretch gap-5 overflow-hidden overflow-x-auto invisible-scroll">
                <div v-for="(recentPod, index) in recentPods" :key="index"
                    class=" w-11/12 min-w-[91.666667%] xs:w-80 xs:min-w-[20rem] md:w-1/3 md:min-w-[33.333333%] lg:w-1/4 lg:min-w-[25%]">
                    <CardsRecentPod 
                    :title="recentPod.title" 
                    :duration="recentPod.duration" 
                    :href="recentPod.href"
                    :cover-image="recentPod.coverImage" 
                    />
                </div>
                </div>
            </div>
        </AtomsContainer>
    </section>
</template>

<script lang="ts" setup>


// const scrollLeft = useState('scrollLeft', ()=> 0)
const nextIsVisible = useState('nextIsVisible', () => false)
const prevIsVisible = useState('prevIsVisible', () => false)
import { ref } from 'vue';

let element:HTMLDivElement
if (typeof document !== "undefined") {
    element = document.querySelector("[data-slide-recent]") as HTMLDivElement
}
function initScroll(): void {
    if (typeof element === "undefined" || element === null) {
        return
    }
    prevIsVisible.value = element.scrollLeft <= 0 ? false : true
    nextIsVisible.value = element.scrollLeft >= element.scrollWidth - element.offsetWidth - 1?false:true
}

function scrollToLeft():void{
    if (typeof element === "undefined" || element === null) {
        return
    }
    element.scrollLeft -= element.clientWidth
}

function scrollToRight():void{
    if (typeof element === "undefined" || element === null) {
        return
    }
    element.scrollLeft += element.clientWidth
}

onMounted(() => {
    if (window !== null) {
        initScroll()
    }
})


const podcasts = ref([
  {
    title: "Unlocking SEO Secrets",
    href: "#",
    duration: "24min",
    coverImage: "/images/podCast.webp",
    category: "SEO",
    createdAt: "2024-08-07",
    description: "Discover the hidden tactics that can boost your website's search engine rankings."
  },
  {
    title: "SEO Basics for Beginners",
    href: "#",
    duration: "30min",
    coverImage: "/images/podCast.webp",
    category: "SEO",
    createdAt: "2024-08-07",
    description: "Learn the fundamentals of SEO and start improving your site's visibility today."
  },
  {
    title: "Advanced SEO Strategies",
    href: "#",
    duration: "45min",
    coverImage: "/images/podCast.webp",
    category: "SEO",
    createdAt: "2024-08-07",
    description: "Take your SEO game to the next level with these advanced strategies."
  },
  {
    title: "SEO Myths Busted",
    href: "#",
    duration: "20min",
    coverImage: "/images/podCast.webp",
    category: "SEO",
    createdAt: "2024-08-07",
    description: "We debunk common SEO myths and provide you with the facts."
  },
  {
    title: "Local SEO Tips",
    href: "#",
    duration: "25min",
    coverImage: "/images/podCast.webp",
    category: "SEO",
    createdAt: "2024-08-07",
    description: "Optimize your website for local search with these effective tips."
  },
  {
    title: "SEO for E-commerce",
    href: "#",
    duration: "35min",
    coverImage: "/images/podCast.webp",
    category: "SEO",
    createdAt: "2024-08-07",
    description: "Boost your online store's visibility and sales with our SEO guide."
  },
  {
    title: "Mobile SEO Essentials",
    href: "#",
    duration: "28min",
    coverImage: "/images/podCast.webp",
    category: "SEO",
    createdAt: "2024-08-07",
    description: "Ensure your website is optimized for mobile users with these essentials."
  },
  {
    title: "Content Marketing and SEO",
    href: "#",
    duration: "40min",
    coverImage: "/images/podCast.webp",
    category: "SEO",
    createdAt: "2024-08-07",
    description: "Learn how to integrate content marketing with SEO to drive traffic."
  }
]);

const recentPods = ref([
  {
    title: "How to hack a website with HTML in a simple way",
    duration: "23min",
    href: "#",
    coverImage: "/images/2.webp"
  },
  {
    title: "5 Principles you must know for writing clear code",
    duration: "1h:22min",
    href: "#",
    coverImage: "/images/3.webp"
  },
  {
    title: "Make your website requests secure beyond your imagination",
    duration: "12min",
    href: "#",
    coverImage: "/images/4.webp"
  },
  {
    title: "How to get started with desktop development",
    duration: "50min",
    href: "#",
    coverImage: "/images/5.webp"
  }
]);

</script>
