<script setup lang="ts">
defineProps<{
  content: any
}>()
</script>

<template>
    <!-- galleries component -->
    <div class="galleries">
      <div class="galleries-container">
        <!-- images -->
        <div class="galleries-wrapper">
          <div v-for="(item, index) in content.images" :key="index">
            <img :src="item.image" :alt="item.title">
          </div>
        </div>
        <!-- notes -->
        <p>{{ content.notes }}</p>

        <!-- link -->
        <div>
          <!-- Reusable Button (Use slot)-->
          <button class="primary-cta">
            {{ content.link.title }}
          </button>
        </div>
      </div>
    </div>
    <!-- galleries component end -->
</template>

<style scoped>
/* Galleries */
.galleries {
    background-color: var(--bg-color-light-primary-container);
}

.galleries-container {
    padding: 2rem 0;
}

@media only screen and (min-width: 768px) {
    .galleries-container {
        padding: 4rem 0;
    }
}
.galleries-wrapper {
    display: flex;
    overflow-x: auto;
    padding: 0 1rem;
    gap: 1rem;
    scrollbar-width: none; /* Firefox */
	  -ms-overflow-style: none; /* Internet Explorer and Edge */
}

.galleries-wrapper::-webkit-scrollbar {
	display: none; /* Chrome, Safari, and Opera */
}

@media only screen and (min-width: 80rem) {
  .galleries-wrapper {
    padding-left: calc(50% - 39rem);
  }
}

.galleries-wrapper > div {
    flex-shrink: 0;
    width: 20rem;
    height: auto;
}

.galleries-wrapper img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.galleries-container p {
    font-size: 12px;
    font-weight: 500;
    line-height: 16px;
    margin-top: 1rem;
    padding: 0 1rem;
}

@media only screen and (min-width: 768px) {
    .galleries-container p {
        font-size: 14px;
        line-height: 20px;
        text-align: center;
        margin-top: 4rem;
    }
}

.galleries-container > div:last-child {
    display: flex;
    justify-content: center;
    margin-top: 3rem;
    padding: 0 var(--section-hpadding);
}

@media only screen and (min-width: 768px) {
    .galleries-container > div:last-child {
        margin-top: 4rem;
    }
}

.galleries-container > div:last-child button {
    padding-left: 4rem;
    padding-right: 4rem;
}

@media only screen and (max-width: 768px) {
    .galleries-container > div:last-child button {
        width: 100%;
    }
}
/* Galleries end */
</style>