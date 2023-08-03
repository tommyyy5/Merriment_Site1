<script setup lang="ts">
import { ref, onMounted } from 'vue';

const tabTitles = ref(['Tab Pertama', 'Tab Kedua']);
const tabViews = ref([
  { images: [
    { src: '/images/image1.png', alt: 'Gambar 1' },
    { src: '/images/image1.png', alt: 'Gambar 1' },
    { src: '/images/image1.png', alt: 'Gambar 1' },
    { src: '/images/image1.png', alt: 'Gambar 3' },
    { src: '/images/image1.png', alt: 'Gambar 4' }
  ] },
  { images: [
    { src: '/images/image1.png', alt: 'Gambar 6' },
    { src: '/images/image1.png', alt: 'Gambar 7' },
    { src: '/images/image1.png', alt: 'Gambar 8' }
  ] }
]);
const currentPageIndex = ref(0);

const changeTab = (index: any) => {
  currentPageIndex.value = index;
};

const getTabClass = (index: any) => {
  if (index === currentPageIndex.value) {
    return 'active';
  } else if (index === currentPageIndex.value + 1) {
    return 'next-page';
  } else if (index === currentPageIndex.value - 1) {
    return 'previous-page';
  } else {
    return '';
  }
};

onMounted(() => {
  showCurrentPage();
});

const showCurrentPage = () => {
  const tabViews = document.querySelectorAll('.galleries-wrapper .tab-view');
  const tabTitles = document.querySelectorAll('.galleries-wrapper .tabs > div');

  tabViews.forEach((tabView, index) => {
    tabView.classList.remove('active', 'next-page', 'previous-page');
    if (index === currentPageIndex.value) {
      tabView.classList.add('active');
    } else if (index === currentPageIndex.value + 1) {
      tabView.classList.add('next-page');
    } else if (index === currentPageIndex.value - 1) {
      tabView.classList.add('previous-page');
    }
  });

  tabTitles.forEach((tabTitle, index) => {
    tabTitle.classList.toggle('active', index === currentPageIndex.value);
  });
};
</script>

<template>
  <div class="galleries">
    <div class="galleries-wrapper">

      <div class="tabs">
        <div
          v-for="(tab, index) in tabTitles"
          :key="index"
          :class="{ active: currentPageIndex === index }"
          @click="changeTab(index)"
        >
          {{ tab }}
        </div>
      </div>

      <div class="tab-view" v-for="(tabView, index) in tabViews" :key="index" :class="getTabClass(index)">
        <img v-for="image in tabView.images" :key="image.alt" :src="image.src" :alt="image.alt">
      </div>

      <div>
        <p>*Klik foto untuk melihat detil katalog</p>
        <button class="primary-cta">
          Order Sekarang
        </button>
      </div>
    </div>
  </div>
</template>


<style scoped>
/* galleries */
   
.galleries {
  background-color: var(--bg-color-light-primary-container);
}

.galleries-wrapper {
  max-width: 80rem;
  margin: 0 auto;
  padding: 1rem;
}

.galleries-wrapper .tabs {
  font-family: 'Roboto';
  display: flex;
  margin-bottom: 20px;
  font-size: 14px;
  line-height: 20px;
  font-weight: 500;
}
    
.galleries-wrapper .tabs > div {
  flex: 1;
  padding: 1rem 0;
  text-align: center;
  cursor: pointer;
  position: relative;
}

.galleries-wrapper .tabs > div.active {
  color: var(--color-light-primary);
}

.galleries-wrapper .tabs > div.active::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  width: 2rem;
  height: 3px;
  margin: auto;
  background-color: var(--color-light-primary);
  border-radius: 100px 100px 0px 0px;
}
    
.galleries-wrapper .tab-view {
  display: none;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 1rem;
  border-radius: .75rem;
}

.galleries-wrapper .tab-view.active {
  display: grid;
}

@media only screen and (min-width: 768px) {
  .galleries-wrapper .tab-view {
    grid-template-columns: repeat(5, minmax(0, 1fr));
    gap: 2rem;
  } 
}

.galleries-wrapper .tab-view img{
  border-radius: .75rem;
}

.galleries-wrapper > div:last-child {
  display: flex;
  flex-direction: column;
  margin-top: 1rem;
}

@media only screen and (min-width: 768px) {
  .galleries-wrapper > div:last-child {
    align-items: center;
    margin-top: 2rem;
  }
}

.galleries-wrapper > div:last-child button{
  width: 100%;
  margin-top: 1rem;
}

@media only screen and (min-width: 768px) {
  .galleries-wrapper > div:last-child button{
    width: 30%;
    margin-top: 2rem;
  }  
}

/* galleries end */
</style>