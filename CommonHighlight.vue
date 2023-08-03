<script setup lang="ts">
defineProps<{
  content: any
}>()
</script>

<template>
    <!-- common highlights component-->
    <div class="common-highlight">
      <div>
          <span v-if="content.icon">{{ content.icon }}</span>
          <h2>{{ content.title }}</h2>
          <p>{{ content.description }}</p>
      </div>
    </div>
    <!-- common highlights component end -->
</template>

<style scoped>
/* Common Highlight */
.common-highlight {
    background-color: var(--bg-color-light-primary-container);
}

.common-highlight > div:only-child {
    max-width: var(--section-max-width);
    padding: 2rem var(--section-hpadding);
    margin: 0 auto;
    text-align: center;
}

@media only screen and (min-width: 768px) {
    .common-highlight > div:only-child {
        padding: 3rem 1rem;
    }
}

.common-highlight span,
.common-highlight h2 {
    font-size: 36px;
    line-height: 44px;
}

.common-highlight p {
    font-size: 16px;
    line-height: 24px;
    margin-top: 1rem;
}

@media only screen and (min-width: 768px) {
    .common-highlight span,
    .common-highlight h2 {
        font-size: 57px;
        line-height: 64px;
    }

    .common-highlight p {
        font-size: 24px;
        line-height: 32px;
        width: 40%;
        margin: 1rem auto;
    }
}
/* Common Highlight end*/
</style>