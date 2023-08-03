<script setup lang="ts">
import { ref } from 'vue';

const isMenuOpen = ref(false);

function toggleMenu() {
  isMenuOpen.value = !isMenuOpen.value;
}
</script>

<template>
    <!-- header component -->
    <header>
        <div class="navbar">
            <div>
                <router-link to="/">
                    <img src="/images/brand_logo.png" alt="Logo">
                </router-link>
                <button @click="toggleMenu">
                    <img src="/icons/three-dots.svg" alt="Menu Icon">
                </button>
            </div>
        </div>
        <div class="h-16"></div>
        <!-- Modal -->
        <div id="menuModal" class="menu-modal" :class="{ active: isMenuOpen }">
            <!-- Close button -->
            <div>
                <router-link to="/">
                    <img src="/images/brand_logo.png" alt="Logo">
                </router-link>
                <button @click="toggleMenu">
                    <img src="/icons/close.svg" alt="Close Icon">
                </button>   
            </div>
            <!-- Navigation -->
            <div>
                <nav class="space-y-12">
                    <router-link to="/testimonial" @click="toggleMenu">What they said about us</router-link>
                    <router-link to="/features" @click="toggleMenu">What we offer</router-link>
                    <router-link to="/orders" @click="toggleMenu">Our Catalogue & Order Step</router-link>
                </nav>
                <div>
                    <!-- Reusable Button -->
                    <button class="primary-cta">
                        <img src="/icons/whatsapp.svg" alt="">
                        Hubungi Kami Sekarang!
                    </button>
                </div>
            </div>
            <div class="copyright">
                <p>© 2023 Merriment. Muda Berkarya Teknologi, CV</p>
                <div>
                    <p>More about</p>
                    <a href="#">
                        <img src="/images/company_logo.png" alt="Button Icon"  class="h-6 w-auto">
                    </a>
                </div>
            </div>
        </div>
    </header>      
    <!-- header component end -->
</template>

<style scoped>
/* Header component*/
.navbar {
    background-color: var(--bg-color-light-primary-container);
    position: fixed;
    right: 0;
    left: 0;
    top: 0;
    width: 100%;
    z-index: 99;
}

.navbar > div:only-child {
    padding: 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    max-width: var(--section-max-width);
    margin: 0 auto;
}

.navbar img{
    height: 1.5rem;
    width: auto;
}   

.navbar button {
    border-radius: .75rem;
    padding: .5rem 1rem;
}   

.navbar button img {
    height: 1rem;
    width: auto;
}
/* Header component end */

/* Menu Modal */
.menu-modal {
    background-color: var(--bg-color-light-primary-container);
    display: flex;
    flex-direction: column;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 999;
    visibility: hidden;
    opacity: 0;
    transition: opacity 0.3s ease-in-out;
}

.menu-modal.active {
	visibility: visible;
	opacity: 1;
}

.menu-modal > div {
    max-width: 80rem;
    margin: 0 auto;
    padding: 1rem;
    width: 100%;
}

.menu-modal > div:first-child {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.menu-modal > div:first-child button {
    padding: .5rem;
    border-radius: .5rem;   
}

.menu-modal > div:first-child img{
    height: 1.5rem;
    width: auto;
}

.menu-modal > div:first-child button img{
    height: 1rem;
    width: auto;
}

.menu-modal > div:nth-child(2) {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-around;
    padding: 2rem 1rem;
    margin-bottom: auto;
}

@media only screen and (min-width: 768px) {
    .menu-modal > div:nth-child(2) {
        padding: 4.5rem 1rem;
    }
}

.menu-modal > div:nth-child(2) nav{
	font-family: "Roboto", sans-serif;
    display: flex;
    flex-direction: column;
    justify-content: center;
    color: var(--color-light-primary);
    font-size: 14px;
    line-height: 20px;
    font-weight: 500;
    text-align: center;
}

.menu-modal > div:nth-child(2) > div:last-child {
    display: flex;
    justify-content: center;
    width: 100%;
    margin-top: 5rem;
}

.menu-modal > div:nth-child(2) > div:last-child button {
    width: 100%;
}

@media only screen and (min-width: 768px) {
    .menu-modal > div:nth-child(2) > div:last-child {
        width: 100%;
    }
    
    .menu-modal > div:nth-child(2) > div:last-child button {
        width: unset;
        padding-left: 4rem;
        padding-right: 4rem;
    }
}
/* Menu Modal end */
</style>