<script setup lang="ts">
defineProps<{
  content: any
}>()
</script>

<template>
    <!-- testimonial collection component -->
    <div class="testimonial-collection">
        <div class="testimonial-wrapper">
            <!-- testimonial item -->
            <div v-for="(item, index) in content" :key="index"> 
                <img class="avatar" :src="item.avatar" :alt="item.name">
                <div>
                    <h3>{{ item.name }}</h3>
                    <p>{{ item.feedback }}</p>
                    <div>
                        <div class="rating">
                            <img src="/icons/star.svg" alt="Rating">
                            <img src="/icons/star.svg" alt="Rating">
                            <img src="/icons/star.svg" alt="Rating">
                            <img src="/icons/star.svg" alt="Rating">
                            <img src="/icons/star.svg" alt="Rating">
                        </div>
                        <p class="created-at">{{ item.created_at }}</p>
                    </div>
                </div>
            </div>
            
        </div>
    </div>
    <!-- testimonial collection component end -->
</template>

<style scoped>
/* testimonials collection */
.testimonial-collection {
    background-color: var(--bg-color-light-primary-container);
}

.testimonial-wrapper {
    display: flex;
    overflow-x: auto;
    padding: 3rem var(--section-hpadding);
    scrollbar-width: none; /* Firefox */
	-ms-overflow-style: none; /* Internet Explorer and Edge */
}

.testimonial-wrapper::-webkit-scrollbar {
	display: none; /* Chrome, Safari, and Opera */
}

@media only screen and (min-width: 768px) {
    .testimonial-wrapper {
        padding: 4rem var(--section-hpadding);
    }
}

@media only screen and (min-width: 768px) {
    .testimonial-wrapper {
        padding-left: calc(50% - 39rem);
    }
}


.testimonial-wrapper > div {
    background-color: var(--bg-color-light-surface-container-low);
    display: flex;
    flex-shrink: 0;
    border-radius: .75rem;
    width: 22rem;
    padding: 1rem;
    margin-right: 1rem;
}

@media only screen and (min-width: 768px) {
    .testimonial-wrapper > div {
        margin-right: 2rem;
    }
}

.testimonial-wrapper img.avatar {
    height: 3rem;
    width: auto;
    margin-right: 1rem;
}

.testimonial-wrapper h3 {
    font-size: 16px;
    line-height: 24px;
    font-weight: 500;
}

.testimonial-wrapper p {
    font-size: 14px;
    line-height: 20px;
}

.testimonial-wrapper > div img {
    height: 1rem;
    width: auto;
}

.testimonial-wrapper > div > div > div {
    display: flex;
    align-items: flex-end;
    justify-content: space-between;
    margin-top: 1rem;
}

.testimonial-wrapper > div > div > p {
    width: 80%;
}

.testimonial-wrapper .rating {
    display: flex;
}

.testimonial-wrapper .rating > img {
    margin-right: .25rem;
}

.testimonial-wrapper .created-at {
    font-size: 11px;
    line-height: 16px;
}
/* testimonials collection end */
</style>