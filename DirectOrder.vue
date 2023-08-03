<script setup lang="ts">
defineProps<{
  content: any
}>()
</script>

<template>
   <!-- direct order component -->
   <div class="direct-order">
      <div class="direct-order-wrapper"> 
        <div v-for="(item, index) in content" :key="index">
          <img :src="item.image" alt="">
          <h3>{{ item.title }}</h3>
          <h4>{{ item.content }}</h4>
        </div>
      </div>
    </div>
    <!-- order component end -->
</template>

<style scoped>
/* Direct Order */
.direct-order {
    background-color: var(--bg-color-light-primary-container);
}

.direct-order-wrapper {
    max-width: var(--section-max-width);
    margin: 0 auto;
    padding: 2rem var(--section-hpadding);
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
}

@media only screen and (min-width: 768px) {
    .direct-order-wrapper {
        padding: 3rem 1rem;
        flex-direction: row;
        overflow-x: auto;
        gap: 20rem;
    }
}

.direct-order-wrapper > div {
    padding: .5rem 0;
}

.direct-order-wrapper > div img {
    height: 3rem;
    width: auto;
}

@media only screen and (min-width: 768px) {
    .direct-order-wrapper > div img {
        height: 4rem;
    }
}

.direct-order-wrapper > div h3 {
    font-size: 16px;
    line-height: 24px;
    margin-top: 1rem;
}

@media only screen and (min-width: 768px) {
    .direct-order-wrapper > div h3 {
        font-size: 22px;
        line-height: 28px;
    }
}

.direct-order-wrapper > div h4 {
    font-size: 14px;
    line-height: 20px;
}

@media only screen and (min-width: 768px) {
    .direct-order-wrapper > div h4 {
        font-size: 16px;
        line-height: 24px;
        margin-top: .25rem;
    }
}
/* Direct Order end */
</style>\