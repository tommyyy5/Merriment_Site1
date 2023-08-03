<script setup lang="ts">
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Pagination, Autoplay } from 'swiper/modules'
import 'swiper/css'
import 'swiper/css/pagination';

defineProps<{
  content: any
}>()
</script>

<template>
    <!-- card collection component -->
    <div class="card-collection">
        <div class="card-collection-wrapper">
            <div> 
                <swiper :modules="[Pagination, Autoplay]" :slides-per-view="1" :autoplay="{ delay: 2500 }" :pagination="{ clickable: true }">
                    <swiper-slide v-for="(item, index) in content.card_testimonial.testimonials" :key="index">
                        <span>{{ item.emoji }}</span>
                        <h3>{{ item.title }}</h3>
                        <p>{{ item.feedback }}</p>
                        <h5> - {{ item.name }}</h5>
                    </swiper-slide>
                </swiper>
                <div class="h-10"></div>
                <router-link class="secondary-cta" :to="content.card_testimonial.link.url">
                    <img src="/icons/arrow_outward.svg" :alt="content.card_testimonial.link.url">
                    {{ content.card_testimonial.link.title }}
                </router-link>
            </div>

            <!-- card item -->
            <div> 
                <div>
                    <span>{{ content.card_feature.emoji }}</span>
                    <h3>{{ content.card_feature.title }}</h3>
                    <p>{{ content.card_feature.content }}</p>
                </div>
                <div class="h-16"></div>
                <router-link :to="content.card_feature.link.url" class="secondary-cta">
                    <img src="/icons/arrow_outward.svg" alt="Button Icon">
                    {{ content.card_feature.link.title }}
                </router-link>
            </div>

            <!-- card item -->
            <div> 
                <swiper :modules="[Pagination, Autoplay]" :slides-per-view="1" :autoplay="{ delay: 3500 }" :pagination="{ clickable: true }">
                    <swiper-slide v-for="(item, index) in content.card_order_step.galleries" :key="index">
                        <img :src="item.kv" :alt="item.title">
                    </swiper-slide>
                </swiper>
                <div >
                    <span>{{ content.card_order_step.emoji }}</span>
                    <h3>{{ content.card_order_step.title }}</h3>
                    <p>{{ content.card_order_step.content }}</p>
                    <div class="h-10"></div>
                    <router-link :to="content.card_order_step.link.url" class="secondary-cta">
                        <img src="/icons/arrow_outward.svg" alt="Button Icon">
                        {{ content.card_order_step.link.title }}
                    </router-link>
                </div>
            </div>
        </div>
    </div>
    <!-- card collection component end -->
</template>

<style scoped>
/* Card Collection */
.card-collection {
    padding: 3rem 0;
}

@media only screen and (min-width: 768px) {
    .card-collection {
        padding: 5rem 0;
    }
}

.card-collection-wrapper {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    padding: 0 var(--section-hpadding);
    max-width: var(--section-max-width);
    margin: 0 auto;
}

@media only screen and (min-width: 768px) {
    .card-collection-wrapper {
        flex-direction: row;
        gap: 2rem;
    }
}

.card-collection-wrapper > div {
    background-color: var(--bg-color-light-surface-container-low);
    border-radius: 1.75rem;
    padding: 2rem;
    min-height: 20rem;
}
.card-collection-wrapper > div:first-child,
.card-collection-wrapper > div:nth-child(2) {
    width: 100%;
}

.card-collection-wrapper > div:last-child {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    gap: 1.5rem;
}

@media only screen and (min-width: 768px) {
    .card-collection-wrapper > div:first-child,
    .card-collection-wrapper > div:nth-child(2) {
        width: calc(30% - 2rem);
    }
    
    .card-collection-wrapper > div:last-child {
        width: 40%;
        display: flex;
        flex-direction: row-reverse;
    }
}

.card-collection-wrapper > div:last-child > div {
    width: 100%;
}

@media only screen and (min-width: 768px) {
    .card-collection-wrapper > div:last-child > div {
        width: 50%;
    }
}

.card-collection-wrapper span,
.card-collection-wrapper h3 {
    font-size: 22px;
    font-weight: 500;
    line-height: 28px;
    margin-top: .5rem;
}

.card-collection-wrapper p {
    font-size: 14px;
    line-height: 20px;
    margin-top: .5rem;
}

.card-collection-wrapper h5 {
    font-size: 16px;
    line-height: 24px;
    margin-top: 2rem;
}
/* Card Collection end */


</style>