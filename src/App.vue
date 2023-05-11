<script setup>
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';
import Home from './views/Home.vue';
import Services from './views/Services.vue';
import Pricing from './views/Pricing.vue';
import About from './views/About.vue';
import Contact from './views/Contact.vue';
import DesignFooter from './components/DesignFooter.vue';
</script>

<template>
    <Header />
    <main>
        <Home id="home" />
        <Services id="services" />
        <Pricing id="pricing" />
        <About id="about" />
        <Contact id="contact" />
    </main>
    <Footer />
    <DesignFooter />
</template>