<script setup lang="ts">

import { ref } from 'vue';

const tabTitles = ref(['Title 1', 'Title 2', 'Title 3']);
const tabViews = ref([
  {
    subtitle: 'Subtitle #1',
    items: [
      { value: 'option1', label: 'Option 1' },
      { value: 'option1', label: 'Option 1' },
      { value: 'option1', label: 'Option 1' },
    ],
    type: 'radio',
  },
  {
    subtitle: 'Subtitle #2',
    items: [
      { value: 'check1', label: 'Check 1' },
      { value: 'check1', label: 'Check 1' },
      { value: 'check1', label: 'Check 1' },
      { value: 'check1', label: 'Check 1' },
    ],
    type: 'checkbox',
  },
  {
    subtitle: 'Subtitle #3',
    items: [
      { value: 'check1', label: 'Check 1' },
      { value: 'check1', label: 'Check 1' },
      { value: 'check1', label: 'Check 1' },
      { value: 'check1', label: 'Check 1' },
      { value: 'check1', label: 'Check 1' },
      { value: 'check1', label: 'Check 1' },
    ],
    type: 'checkbox',
  },
]);

const currentPageIndex = ref(0);

const changePage = (index: number) => {
  currentPageIndex.value = index;
};

const nextPage = () => {
  if (currentPageIndex.value < tabViews.value.length - 1) {
    currentPageIndex.value++;
  }
};
</script>

<template>
  <div class="custom-order">
    <div class="custom-order-wrapper">
      <div class="tab-header">
        <h3 v-for="(title, index) in tabTitles" :key="index" :class="{ active: currentPageIndex === index }" @click="changePage(index)">{{ title }}</h3>
      </div>
      
      <div class="tab-view-item" v-for="(view, index) in tabViews" :key="index" :class="{ active: currentPageIndex === index }">
        <h4>{{ view.subtitle }}</h4>
        <ul class="space-y-4">
          <li v-for="(item, itemIndex) in view.items" :key="itemIndex">
            <input :type="view.type" :name="`list${index}`" :value="item.value" />
            <label>{{ item.label }}</label>
          </li>
        </ul>
      </div>

      <button class="primary-cta w-full" @click="nextPage">Next</button>
    </div>
  </div>

</template>

<style scoped>
/* Custom order */
.custom-order {
    background-color: var(--bg-color-light-primary-container);
    padding: 2rem var(--section-hpadding);
}

.custom-order-wrapper {
    max-width: 22.5rem;
    margin: 0 auto;
}

.custom-order-wrapper > div:first-child {
    display: flex;
    overflow-x: auto;
    font-size: 28px;
    line-height: 36px;
    padding: 0 1rem;
    scrollbar-width: none; /* Firefox */
	-ms-overflow-style: none; /* Internet Explorer and Edge */
}

.custom-order-wrapper > div:first-child::-webkit-scrollbar {
	display: none; /* Chrome, Safari, and Opera */
}

.custom-order-wrapper > div:not(:first-child) {
    display: flex;
    flex-direction: column;
    margin-top: 2rem;
    transition: transform 0.3s ease-in-out;
}

.custom-order-wrapper > div:not(:first-child):not(.active) {
    display: none;
}

.custom-order-wrapper > div:not(:first-child).active {
    transform: translateX(0%);
}
  
.custom-order-wrapper > div:not(:first-child).next-page {
    transform: translateX(100%);
}
  
.custom-order-wrapper > div:not(:first-child).previous-page {
    transform: translateX(-100%);
}

.custom-order-wrapper h3 {
    opacity: .38;
    flex-shrink: 0;
}

.custom-order-wrapper h4 {
    font-size: 16px;
    line-height: 24px;
}

.custom-order-wrapper ul {
    font-size: 16px;
    line-height: 24px;
    margin: 2rem 0;
}

.custom-order-wrapper ul li{
    display: flex;
    align-items: center;
}

.custom-order-wrapper ul li input {
    margin-right: .5rem;
}

.custom-order-wrapper h3.active {
    color: var(--color-light-primary);
    opacity: 1;
}

.custom-order-wrapper > div > h3:not(:last-child)::after {
    content: "/";
    margin: 0 2rem;
}

input[type="radio"] {
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
    width: 25px;
    height: 25px;
    border-radius: 50%;
    border: 2px solid #999;
    outline: none;
}

/* Styling when the radio button is checked */
input[type="radio"]:checked {
    background-color: var(--color-light-primary);
}
/* Custom order end */
</style>