<template>
    <div class="min-h-screen bg-gradient-to-br from-[#97094c] via-pink-700 to-pink-900 text-white">

        <!-- Navbar -->
        <nav class="fixed top-0 w-full z-50 backdrop-blur-xl bg-white/10 border-b border-white/20">
            <div class="max-w-7xl mx-auto flex items-center justify-between px-6 py-4">
                <a href="/" aria-label="Go to Pehnava Home"
                    class="flex items-center gap-2 focus:outline-none focus:ring-2 focus:ring-pink-400 rounded-lg">
                    <img :src="logo" alt="Pehnava – Women's Fashion Store" class="h-auto w-30 object-contain" />
                </a>


                <!-- Desktop Menu -->
                <ul class="hidden md:flex items-center gap-8 text-sm">
                    <li><a href="/" class="hover:text-pink-200">Home</a></li>
                    <li><a href="#products" class="hover:text-pink-200">Collection</a></li>
                    <li><a href="#about" class="hover:text-pink-200">About</a></li>
                    <li><a href="#contact" class="hover:text-pink-200">Contact</a></li>
                </ul>

                <!-- Mobile Button -->
                <button class="md:hidden" @click="menuOpen = !menuOpen">☰</button>

                <a href="/"
                    class="hidden md:block bg-white text-[#97094c] px-5 py-2 rounded-full font-semibold hover:scale-105 transition">
                    Shop Now
                </a>
            </div>

            <!-- Mobile Menu -->
            <div v-if="menuOpen" class="md:hidden bg-[#97094c] text-center py-4 space-y-4">
                <a href="#home" @click="menuOpen = false" class="block">Home</a>
                <a href="#products" @click="menuOpen = false" class="block">Collection</a>
                <a href="#about" @click="menuOpen = false" class="block">About</a>
                <a href="#contact" @click="menuOpen = false" class="block">Contact</a>
            </div>
        </nav>

        <!-- Hero -->
        <section id="home" class="pt-36 pb-24">
            <div class="max-w-7xl mx-auto grid md:grid-cols-2 gap-12 items-center px-6">

                <!-- Left Content -->
                <div>
                    <h2 class="text-4xl md:text-5xl font-extrabold mb-6">
                        Redefine Your Style with
                        <span class="text-pink-200 font-['Cookie'] text-5xl md:text-6xl font-normal">
                            Pehnava
                        </span>
                    </h2>

                    <p class="text-white/80 mb-8">
                        Traditional elegance meets modern fashion. Discover premium ethnic & trendy wear crafted for
                        your personality.
                    </p>
                    <div class="flex flex-wrap gap-4">
                        <a href="#products" class="bg-white text-[#97094c] px-6 py-3 rounded-xl font-semibold">
                            Explore Collection
                        </a>
                        <a href="/" class="border border-white px-6 py-3 rounded-xl">
                            Visit Store
                        </a>
                    </div>
                </div>

                <!-- ✅ Right Side Carousel -->
                <div class="relative w-full h-[340px] rounded-3xl overflow-hidden shadow-2xl border border-white/20">

                    <transition name="fade" mode="out-in">
                        <img :key="currentSlide" :src="slides[currentSlide]" class="w-full h-full object-cover" />
                    </transition>

                    <!-- Dots -->
                    <div class="absolute bottom-4 left-1/2 -translate-x-1/2 flex gap-2">
                        <span v-for="(dot, i) in slides" :key="i" class="w-3 h-3 rounded-full cursor-pointer"
                            :class="currentSlide === i ? 'bg-white' : 'bg-white/40'" @click="currentSlide = i"></span>
                    </div>
                </div>

            </div>
        </section>


        <!-- Products -->
        <section id="products" class="py-20 bg-white text-gray-800 rounded-t-[3rem]">
            <div class="max-w-7xl mx-auto px-6">
                <h3 class="text-3xl font-bold text-center mb-12 text-[#97094c]">
                    Trending Products
                </h3>

                <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-8">

                    <div v-for="product in products" :key="product.id"
                        class="rounded-2xl shadow-xl overflow-hidden hover:scale-105 transition cursor-pointer"
                        @click="openPreview(product.image)">
                        <!-- ✅ Image Now Showing -->
                        <img :src="product.image" class="h-80 w-full object-cover" />

                        <div class="p-4 text-center">
                            <h4 class="font-semibold">{{ product.name }}</h4>
                            <p class="text-sm text-gray-500">₹{{ product.price }}</p>

                            <!-- ✅ Preview Button Instead of Buy -->
                            <button class="mt-3 w-full bg-[#97094c] text-white py-2 rounded-lg hover:opacity-90">
                                Preview
                            </button>
                        </div>
                    </div>

                </div>
            </div>
        </section>

        <!-- ✅ Image Preview Modal -->
        <div v-if="previewImage" class="fixed inset-0 bg-black/70 flex items-center justify-center z-50"
            @click="previewImage = null">
            <div class="bg-white p-4 rounded-xl max-w-md w-full" @click.stop>
                <img :src="previewImage" class="w-full rounded-xl" />
                <button class="mt-4 w-full bg-[#97094c] text-white py-2 rounded-lg" @click="previewImage = null">
                    Close
                </button>
            </div>
        </div>


        <!-- ✅ Pehnava Categories (Women Focused) -->
        <section class="py-20 bg-gray-50 text-gray-800">
            <div class="max-w-7xl mx-auto px-6 text-center">

                <h3 class="text-3xl font-bold mb-4 text-[#97094c]">Our Categories</h3>
                <p class="text-gray-600 mb-14">
                    Everything a woman needs for daily wear, festive looks & elegant styling.
                </p>

                <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-10">

                    <!-- Women's Clothing -->
                    <div class="bg-white rounded-3xl shadow-xl p-8 hover:-translate-y-2 transition">
                        <div
                            class="w-16 h-16 mx-auto mb-5 flex items-center justify-center rounded-full bg-pink-100 text-2xl">
                            👗
                        </div>
                        <h4 class="text-xl font-bold mb-2">Women’s Clothing</h4>
                        <p class="text-sm text-gray-600 mb-4">
                            Kurtis, dresses, coord sets, festive & daily wear collections.
                        </p>
                        <p class="text-xs font-semibold text-[#97094c]">
                            200+ Stylish Designs
                        </p>
                    </div>

                    <!-- Jewelry -->
                    <div class="bg-white rounded-3xl shadow-xl p-8 hover:-translate-y-2 transition">
                        <div
                            class="w-16 h-16 mx-auto mb-5 flex items-center justify-center rounded-full bg-pink-100 text-2xl">
                            💍
                        </div>
                        <h4 class="text-xl font-bold mb-2">Jewelry</h4>
                        <p class="text-sm text-gray-600 mb-4">
                            Imitation jewelry, bridal sets, earrings, bangles & more.
                        </p>
                        <p class="text-xs font-semibold text-[#97094c]">
                            150+ Trending Pieces
                        </p>
                    </div>

                    <!-- Accessories -->
                    <div class="bg-white rounded-3xl shadow-xl p-8 hover:-translate-y-2 transition">
                        <div
                            class="w-16 h-16 mx-auto mb-5 flex items-center justify-center rounded-full bg-pink-100 text-2xl">
                            👜
                        </div>
                        <h4 class="text-xl font-bold mb-2">Accessories</h4>
                        <p class="text-sm text-gray-600 mb-4">
                            Handbags, clutches, scarves, belts & fashion add-ons.
                        </p>
                        <p class="text-xs font-semibold text-[#97094c]">
                            100+ Must-Have Items
                        </p>
                    </div>

                    <!-- Boutique Items -->
                    <div class="bg-white rounded-3xl shadow-xl p-8 hover:-translate-y-2 transition">
                        <div
                            class="w-16 h-16 mx-auto mb-5 flex items-center justify-center rounded-full bg-pink-100 text-2xl">
                            🪡
                        </div>
                        <h4 class="text-xl font-bold mb-2">Boutique Collection</h4>
                        <p class="text-sm text-gray-600 mb-4">
                            Custom designs, handpicked boutique wear & exclusive styles.
                        </p>
                        <p class="text-xs font-semibold text-[#97094c]">
                            Limited Edition
                        </p>
                    </div>

                </div>

                <!-- Bottom CTA -->
                <div class="mt-16">
                    <a href="#products"
                        class="inline-block bg-[#97094c] text-white px-10 py-3 rounded-full font-semibold shadow-xl hover:scale-105 transition">
                        Explore Trending Products
                    </a>
                </div>

            </div>
        </section>

        <!-- About + Contact -->
        <section class="py-20 bg-white text-gray-800">
            <div class="max-w-7xl mx-auto grid md:grid-cols-2 gap-12 px-6">

                <!-- ✅ Enhanced About -->
                <div id="about">
                    <img :src="logo1" alt="Pehnava – Women's Fashion Store"
                        class="h-auto w-50 object-contain inline-block" />
                    <p class="mb-4 text-gray-700 leading-relaxed">
                        <strong>Pehnava</strong> is a dedicated women’s fashion destination based in
                        <strong>Surighat, Mungeli (C.G.)</strong>, offering a beautiful range of
                        <strong>clothing, accessories, jewelry, and exclusive boutique items</strong>.
                        We believe every woman deserves to feel confident, elegant, and stylish—every single day.
                    </p>

                    <p class="mb-4 text-gray-700 leading-relaxed">
                        Our collection includes everything from <strong>daily wear kurtis and festive outfits</strong>
                        to <strong>designer dresses, imitation jewelry, handbags, accessories, and custom boutique
                            pieces</strong>.
                        Each product is carefully selected to reflect modern trends while preserving traditional grace.
                    </p>

                    <ul class="space-y-3 text-gray-700">
                        <li>✅ Women’s Clothing – Daily, Party & Festive Wear</li>
                        <li>✅ Trendy Accessories & Handbags</li>
                        <li>✅ Stylish Imitation Jewelry Collection</li>
                        <li>✅ Boutique & Custom Fashion Items</li>
                        <li>✅ Affordable Prices with Premium Quality</li>
                    </ul>
                </div>

                <!-- Contact -->
                <div id="contact">
                    <h3 class="text-3xl font-bold mb-6 text-[#97094c]">Contact Us</h3>

                    <p class="mb-4 text-gray-700">
                        📍 Surighat, Mungeli (C.G.) – 495334
                        <br />📱 WhatsApp: 62618 17432
                        <br />📧 Email: newpehnava@gmail.com
                    </p>

                    <div class="grid gap-4">
                        <input class="border p-3 rounded-lg" placeholder="Your Name" />
                        <input class="border p-3 rounded-lg" placeholder="Mobile Number" />
                        <textarea class="border p-3 rounded-lg" rows="3" placeholder="Message"></textarea>
                        <button class="bg-[#97094c] text-white py-3 rounded-lg hover:opacity-90">
                            Send Message
                        </button>
                    </div>
                </div>

            </div>
        </section>


        <!-- Footer -->
        <footer class="py-10 text-center text-white/70 text-sm">
            <p>© 2025 Pehnava. All Rights Reserved.</p>
            <p>Designed & developed by <a href="https://canvasclick.in" target="_blank" class="underline">Canvas
                    Click</a></p>
        </footer>

        <!-- ✅ Minimal WhatsApp Floating Button (SVG Only) -->
        <a href="https://wa.me/916261817432" target="_blank" aria-label="Chat on WhatsApp"
            class="fixed bottom-6 right-3 bg-green-500 w-12 h-12 flex items-center justify-center rounded-full shadow-xl hover:scale-110 transition">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32" class="w-6 h-6 fill-white">
                <path
                    d="M16 .5C7.44.5.5 7.44.5 16c0 2.82.74 5.56 2.14 7.96L.5 31.5l7.8-2.04A15.94 15.94 0 0016 31.5c8.56 0 15.5-6.94 15.5-15.5C31.5 7.44 24.56.5 16 .5zm0 28.2a12.6 12.6 0 01-6.43-1.76l-.46-.27-4.61 1.22 1.23-4.49-.3-.47a12.59 12.59 0 01-1.93-6.63c0-6.96 5.67-12.63 12.63-12.63 6.96 0 12.63 5.67 12.63 12.63 0 6.96-5.67 12.63-12.63 12.63zm6.93-9.49c-.38-.19-2.24-1.11-2.59-1.24-.35-.13-.6-.19-.85.19-.25.38-.98 1.24-1.2 1.49-.22.25-.44.28-.82.09-.38-.19-1.58-.58-3.01-1.85-1.11-.99-1.86-2.22-2.08-2.6-.22-.38-.02-.59.17-.78.17-.17.38-.44.57-.66.19-.22.25-.38.38-.63.13-.25.06-.47-.03-.66-.09-.19-.85-2.05-1.17-2.81-.31-.74-.62-.64-.85-.65-.22-.01-.47-.01-.72-.01-.25 0-.66.09-1 .47-.35.38-1.32 1.29-1.32 3.14 0 1.85 1.35 3.64 1.54 3.89.19.25 2.66 4.06 6.45 5.69.9.39 1.6.62 2.14.79.9.29 1.72.25 2.37.15.72-.11 2.24-.91 2.56-1.79.31-.88.31-1.63.22-1.79-.1-.15-.35-.25-.72-.44z" />
            </svg>
        </a>

    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const menuOpen = ref(false)
const previewImage = ref(null)

const openPreview = (image) => {
    previewImage.value = image
}

import logo from '@/assets/images/pehnava.png'
import logo1 from '@/assets/images/pehnava1.png'


const products = [
    {
        id: 1,
        name: 'Designer Saree',
        price: 1299,
        image: 'https://static.wixstatic.com/media/faf1ba_ae8b854bea2341578f774c38bf1310f3~mv2.jpg'
    },
    {
        id: 2,
        name: 'Festive Lehenga',
        price: 2499,
        image: 'https://bombaysaree.in/cdn/shop/files/Beautiful_Ready_to_Wear_Lehenga_Saree_for_Festive_Occasions.jpg?v=1745586488'
    },
    {
        id: 3,
        name: 'Stylish Kurti',
        price: 999,
        image: 'https://images.jdmagicbox.com/quickquotes/images_main/stylish-green-georgette-long-front-slit-kurti-381685214-2pmdm.jpeg'
    },
    {
        id: 4,
        name: 'Ethnic Wear',
        price: 1799,
        image: 'https://ambraee.com/cdn/shop/files/JBL00753.jpg?v=1736766642&width=1080'
    }
]

const currentSlide = ref(0)

onMounted(() => {
    setInterval(() => {
        currentSlide.value = (currentSlide.value + 1) % slides.length
    }, 3000)
})


const slides = [
    'https://img.freepik.com/free-photo/young-woman-with-shopping-bags-beautiful-dress_1303-17550.jpg?semt=ais_hybrid&w=740&q=80',
    'https://media.istockphoto.com/id/1175412224/photo/woman-buying-clothes-at-department-store-stock-photo.jpg?s=612x612&w=0&k=20&c=A_UJwxOoGXChnbaxgJmY9STnQIyMSJqqBwCrAd_7zsg=',
    'https://img.freepik.com/free-photo/stylish-woman-spending-time-summer-field_1157-36073.jpg'
]

</script>

<style scoped>
* {
    scroll-behavior: smooth;
}
</style>