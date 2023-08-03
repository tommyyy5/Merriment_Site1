<script setup lang="ts">
defineProps<{
  content: any
}>()
</script>

<template>
   <!-- features component -->
   <div class="features">
        <div class="features-wrapper">
            <a v-for="(item, index) in content" :key="index" href="#">
              <span>{{ item.icon }}</span>
              <h3>{{ item.title }}</h3>
            </a>
        </div>
    </div>
    <!-- features component end -->
</template>

<style scoped>
/*  features*/
.features {
  background-color: var(--bg-color-light-primary-container);
}

.features-wrapper {
  display: grid;
  max-width: var(--section-max-width);
  margin: 0 auto;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 3rem/* 48px */;
  padding: 3rem var(--section-hpadding);
}

@media only screen and (min-width: 768px) {
  .features-wrapper {
    grid-template-columns: repeat(5, minmax(0, 1fr));
  }
}

.features-wrapper > a {
  display: flex;
  flex-direction: column;
  text-align: center;
}

@media only screen and (min-width: 768px) {
  /* .features-wrapper > a:nth-child(-n+5) {
    width: 20%;  
  }
  .features-wrapper > a:nth-child(n+6):nth-child(-n+11) {
    width: calc(100%/6);    
  }
  .features-wrapper > a:nth-child(n+12) {
    width: calc(100%/4);   
  } */
}

.features-wrapper a span {
  font-size: 4rem;
}

.features-wrapper a h3 {
  margin-top: 0.5rem/* 8px */;
  font-size: 16px;
  line-height: 24px;
}
/* features end*/
</style>