<script setup lang="ts">
</script>

<template>
    <!-- footer component -->
    <footer class="footer">
        <div class="footer-wrapper">
            <div class="copyright">
                <p>© 2023 Merriment. Muda Berkarya Teknologi, CV</p>
                <div>
                    <p>More about</p>
                    <a href="#">
                        <img src="/images/company_logo.png" alt="Button Icon">
                    </a>
                </div>
            </div>
        </div>
    </footer>
    <!-- footer component end -->
</template>

<style scoped>
/* Footer */
.footer {
	background-color: var(--bg-color-light-primary-container);
    padding: 3rem 0;
	overflow: hidden; /* Prevent scrolling */
}

@media only screen and (min-width: 768px) {
	.footer {
		padding: 0;
	}
}

.footer-wrapper {
	max-width: var(--section-max-width);
	margin: 0 auto;
}

@media only screen and (min-width: 768px) {
	.footer-wrapper {
		padding: 0 var(--section-hpadding);
	}
}
/* Footer end */
</style>