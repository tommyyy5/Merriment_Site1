<script setup lang="ts">
defineProps<{
  content: any
}>()
</script>

<template>
    <!-- main masthead component -->
    <div class="main-masthead playfair-display">
        <div class="main-masthead-wrapper">
            <div>
                <h1>{{ content.title }}</h1>
                <p>{{ content.description }}</p>
                <button class="primary-cta">
                    <img :src="content.link.icon" :alt="content.link.title">
                    {{ content.link.title }}
                </button>
            </div>
            <div>
                <img :src="content.image.mobile" class="block md:hidden" alt="">
                <img :src="content.image.desktop" class="hidden md:block" alt="">
            </div>
        </div>
    </div>
    <!-- main masthead component end -->
</template>

<style scoped>
/* Main masthead */
.main-masthead {
    background-color: var(--bg-color-light-primary-container);
    padding: 1rem 0;
}

.main-masthead-wrapper {
    max-width: var(--section-max-width);
    margin: 0 auto;
    padding: 0 var(--section-hpadding);
    min-height: 30rem;
    position: relative;
    z-index: 1;
}

@media only screen and (min-width: 768px) {
    .main-masthead {
        padding: 2rem 2rem 0;
    }
}

.main-masthead-wrapper > div:first-child {
    position: relative;
    z-index: 9;
}

.main-masthead-wrapper > div:last-child {
    position: absolute;
    width: 100%;
    height: auto;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 10;
}

.main-masthead-wrapper > div:last-child img {
    height: 100%;
    width: 100%;
    object-fit: contain;
}

.main-masthead h1 {
    font-size: 36px;
    line-height: 44px;
    font-weight: 500;
}

.main-masthead p {
    font-size: 16px;
    line-height: 24px;
    font-weight: normal;
    margin-top: 1rem;
}

.main-masthead button {
    margin-top: 1rem;
}

@media only screen and (min-width: 768px) {
    .main-masthead h1 {
        font-size: 36px;
        line-height: 44px;
        font-weight: 500;
    }
    
    .main-masthead p {
        font-size: 16px;
        line-height: 24px;
        font-weight: normal;
        margin-top: 1rem;
    }
}
/* Main masthead end */
</style>