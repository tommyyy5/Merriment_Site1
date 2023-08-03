<script setup lang="ts">
defineProps<{
  content: any
}>()
</script>

<template>
   <!-- pricing component -->
   <div class="pricing">
      <div class="pricing-wrapper">
        <div v-for="(item, index) in content" :key="index" class="pricing-card">
          <span>{{ item.emoji }}</span>
          <h3>{{ item.title }}</h3>
          <h4>{{ item.price }}</h4>
          <h5>{{ item.description }}</h5>
          <hr>
          <div>
            <p v-for="(feature, index) in item.features" :key="index">{{ feature }}</p>
          </div>

          <button>
            {{ item.link.title }}
          </button>
        </div>  

      </div>
    </div> 
    <!-- pricing component end -->

</template>

<style scoped>
/* pricing */
.pricing {
  background-color: var(--bg-color-light-primary-container);
}

.pricing-wrapper {
  display: flex;
  flex-direction: column;
  padding: 2rem 1rem;
  max-width: 80rem;
  margin: 0 auto;
  gap: 1rem;
}

@media only screen and (min-width: 768px) {
  .pricing-wrapper { 
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    padding: 2rem 1rem 4rem;
  }
}

.pricing-wrapper .pricing-card {
  display: flex;
  flex-direction: column;
  padding: 2rem;
  border-radius: 1.75rem;
  background-color: var(--bg-color-light-surface-container-low)
}

.pricing-card span{
  font-size: 28px;
  line-height: 36px;
}

.pricing-card h3 {
  font-size: 22px;
  line-height: 28px;
  margin-top: .5rem;
  color: var(--font-color-light-on-surface-variant);
}

.pricing-card h4 {
  font-size: 32px;
  line-height: 40px;
  margin-top: .5rem;
}

.pricing-card h5 {
  font-size: 16px;
  line-height: 24px;
  margin-top: .5rem;
}

.pricing-card hr {
  margin: 1rem 0;
  border-top: 1px solid var(--outline-color-light-outline-variant);
}

.pricing-card > div {
  margin-bottom: 1rem;
}

.pricing-card p {
  font-weight: 500;
  font-size: 16px;
  line-height: 24px;
  margin-bottom: .25rem ;
}

.pricing-card button {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
	font-family: "Roboto", sans-serif;
	color: var(--color-light-primary);
	font-size: 14px;
	line-height: 20px;
	font-weight: 500;
	padding: .5rem;
  border: 1px solid var(--outline-color-light-outline);
  border-radius: 9999px;
}

@media only screen and (min-width: 768px) {
  .pricing-card button {
    margin-top: auto;
  }
}
/* pricing end*/
</style>