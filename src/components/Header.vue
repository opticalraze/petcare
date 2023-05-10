<script setup>
import { onMounted, ref } from 'vue';


let topOfPage = true;

const navbar = ref(null);

onMounted(() => {
    document.onscroll = () => {
        if (window.pageYOffset>0) {
            navbar.value.classList.add('colored');
        } else {
            navbar.value.classList.remove('colored');
        }
    }
})

</script>

<template>
    <header ref="navbar" class="navbar">
        <div class="w-48 text-left">
            <a href="#" class="text-3xl font-black hover:text-opacity-75 transition-all duration-300">PetCare</a>
        </div>
        <nav class="text-lg">
            <a href="#" class="mx-4 active">Home</a>
            <a href="#" class="mx-4">Services</a>
            <a href="#" class="mx-4">Pricing</a>
            <a href="#" class="mx-4">About</a>
        </nav>
        <div class="w-48 text-right">
            <a href="#" class="button">CONTACT US</a>
        </div>
    </header>
</template>

<style scoped>
.navbar {
    @apply fixed z-10 top-0 left-0 w-full px-8 py-4 border-b border-white border-opacity-20 transition-all duration-300 flex items-center justify-between;
}
.navbar a {
    @apply text-white;
}

.navbar a.active {
    @apply font-bold pb-6 border-b-2 border-white;
}

.navbar .button {
    @apply inline-block px-6 py-2 bg-white !text-black font-bold rounded-full hover:scale-110 transition-all duration-300;
}

.navbar.colored {
    @apply bg-white;
}

.navbar.colored a {
    @apply text-black;
}

.navbar.colored a.active {
    @apply border-black;
}

.navbar.colored .button {
    @apply bg-black !text-white;
}
</style>