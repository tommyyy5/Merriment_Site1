<script setup lang="ts">
defineProps<{
  content: any
}>()
</script>

<template>
    <!-- reach us component -->
    <div class="reach-us">
      <div>
        <h3>{{ content.notes }}</h3>
        <!-- Reusable Button (Use slot)-->
        <button class="primary-cta px-8">
          {{ content.link.title }}
        </button>
      </div>
    </div>
    <!-- reach us component end -->

</template>

<style scoped>
/* Reach Us */
.reach-us {
    background-color: var(--bg-color-light-primary-container);
}

.reach-us > div:only-child {
    display: flex;
    align-items: center;
    padding: 1rem 1rem 3rem;
}

@media only screen and (min-width: 768px) {
    .reach-us > div:only-child {
        margin: 1rem 1rem 4rem;
        justify-content: center;
    }
}

.reach-us > div:only-child h3 {
    font-size: 14px;
    line-height: 20px;
    margin-right: 1rem;
}

@media only screen and (min-width: 768px) {
    .reach-us > div:last-child h3 {
        margin-right: 2rem;
    }
}
/* Reach Us end */
</style>\