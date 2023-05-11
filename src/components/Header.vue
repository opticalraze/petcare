<script setup>
import { onMounted, ref } from 'vue';
import MenuIcon from './MenuIcon.vue';

let topOfPage = true;

const navbar = ref(null);

onMounted(() => {
    document.onscroll = () => {
        if (window.pageYOffset>0) {
            navbar.value.classList.add('colored');
        } else {
            navbar.value.classList.remove('colored');
        }
        var current = "";

        const sections = document.querySelectorAll('section');
        const navLi = document.querySelectorAll('li');

        sections.forEach((section) => {
            const sectionTop = section.offsetTop;
            if (pageYOffset >= sectionTop ) {
                current = section.getAttribute("id"); 
            }
        });

        navLi.forEach((li) => {
            li.classList.remove("active");
            if (li.classList.contains(current)) {
                li.classList.add("active");
            }
        });
    };
})

const mobileNav = ref(false);

</script>

<template>
    <header ref="navbar" class="navbar">
        <div class="w-48 text-left">
            <a href="#" class="text-3xl font-black hover:text-opacity-75 transition-all duration-300">PetCare</a>
        </div>
        <nav class="hidden md:block text-lg">
            <ul class="flex">
                <li class="active home">
                    <a href="#" class="mx-4">Home</a>
                </li>
                <li class="services">
                    <a href="#services" class="mx-4">Services</a>
                </li>
                <li class="pricing">
                    <a href="#pricing" class="mx-4">Pricing</a>
                </li>
                <li class="about">
                    <a href="#about" class="mx-4">About</a>
                </li>
            </ul>
        </nav>
        <div class="w-48 text-right">
            <a href="#contact" class="button">CONTACT US</a>
            <button @click="mobileNav = true" class="mobileNavButton"><MenuIcon class="h-6 w-6" /></button>
        </div>
    </header>
    <nav v-if="mobileNav" class="z-50 fixed top-0 left-0 w-full h-screen bg-blue-500 bg-opacity-75 backdrop-blur-lg text-center pt-32">
        <button @click="mobileNav = false" class="absolute top-4 right-8 border border-white p-2 rounded-xl"><MenuIcon class="h-6 w-6" /></button>
        <a @click="mobileNav = false" href="#" class="block w-full font-black text-6xl mb-8">Home</a>
        <a @click="mobileNav = false" href="#services" class="block w-full font-black text-6xl mb-8">Services</a>
        <a @click="mobileNav = false" href="#pricing" class="block w-full font-black text-6xl mb-8">Pricing</a>
        <a @click="mobileNav = false" href="#about" class="block w-full font-black text-6xl mb-8">About</a>
        <a @click="mobileNav = false" href="#contact" class="block w-full font-black text-6xl mb-8">Contact</a>
    </nav>
</template>

<style scoped>
.navbar {
    @apply fixed z-10 top-0 left-0 w-full px-8 py-4 border-b border-white border-opacity-20 transition-all duration-300 flex items-center justify-between;
}
.navbar a {
    @apply text-white;
}

.navbar .active a {
    @apply font-bold pb-6 border-b-2 border-white;
}

.navbar .button {
    @apply hidden md:inline-block px-6 py-2 bg-white !text-black font-bold rounded-full hover:scale-110 transition-all duration-300;
}

.navbar.colored {
    @apply bg-white border-gray-200;
}

.navbar.colored a {
    @apply text-black;
}

.navbar.colored .active a {
    @apply border-black;
}

.navbar.colored .button {
    @apply bg-black !text-white;
}

.mobileNavButton {
    @apply md:hidden border border-white p-2 rounded-xl;
}

.navbar.colored .mobileNavButton {
    @apply border-black text-black;
}
</style>