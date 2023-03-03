<template>
    <div class="
        bg-gray-50/[.5] 
        sticky top-0 z-50
        shadow-md
    ">
        <nav class="
            container
            px-6 py-4
            mx-auto
            md:flex md:justify-between md:items-center
        ">
            <!-- Left Title & Right Menu -->
            <div class="flex items-center justify-between">
                <router-link
                @click="closeNav"
                to="/"
                class="
                    text-xl
                    navbar-title
                    md:text-2xl
                    hover:text-gray-400
                    duration-150
                ">HOGE
                </router-link>
                <!-- Mobile menu button (width<768px)-->
                <div @click="toggleNav" class="flex md:hidden">
                    <button
                        type="button"
                        class="
                        navbar-title
                        hover:text-gray-400
                        focus:outline-none focus:text-indigo-200
                        duration-150
                    ">
                        <!-- Draw button by SVG -->
                        <svg viewBox="0 0 24 24" class="w-6 h-6 fill-current">
                        <path
                            fill-rule="evenodd"
                            d="M4 5h16a1 1 0 0 1 0 2H4a1 1 0 1 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2z"
                        ></path>
                        </svg>
                    </button>
                </div>
            </div>

            <!-- Mobile Menu open: "block", Menu closed: "hidden" -->
            <!-- :class="showMenu ? 'flex' : 'hidden'"  -->
            <!-- <ul
                :class="showMenu ? 'dispnav' : 'notdisp'" 
                class="
                md:flex md:space-y-0 md:flex-row md:items-center md:space-x-10 md:mt-0
                "
            > -->
            <ul
                :class="showMenu ? 'flex' : 'hidden'"
                class="
                flex-col
                mt-8
                space-y-4
                md:flex md:space-y-0 md:flex-row md:items-center md:space-x-10 md:mt-0
                "
            >
            <!-- <ul
                :class="showMenu ? 'flex' : 'hidden'"
                class="
                flex-col
                mt-8
                space-y-4
                md:flex md:space-y-0 md:flex-row md:items-center md:space-x-10 md:mt-0
                "
            > -->
                <li class="navbar-menu hover:text-gray-400"><NuxtLink @click="closeNav" to="/">TOP</NuxtLink></li>
                <li class="navbar-menu hover:text-gray-400 duration-150"><NuxtLink @click="closeNav" to="/about">ABOUT</NuxtLink></li>
                <li class="navbar-menu hover:text-gray-400 duration-150"><NuxtLink @click="closeNav" to="/info">INFO</NuxtLink></li>
                <li class="navbar-menu hover:text-gray-400 duration-150"><NuxtLink @click="closeNav" to="/contact">CONTACT</NuxtLink></li>
            </ul>
        </nav>
    </div>
</template>

<style scoped>
.dispnav {
    /*display: block;*/
    transition: 0.6s;
    visibility: visible;
    opacity: 1;

    display: flex;
    flex-direction: column;
    margin-top: 2rem;
    margin-top: 1rem;
}
.notdisp {
    /*display: none;*/
    transition: 0.6s;
    visibility: hidden;
    opacity: 0;
}
.dispnav2 {
    /*display: block;*/
    transition: 1.6s;
    visibility: visible;
    opacity: 1;
}
.notdisp2 {
    /*display: none;*/
    transition: 1.6s;
    visibility: hidden;
    opacity: 0;
}
</style>

<script>
import { ref } from 'vue';
export default {
  setup() {
    let showMenu = ref(false);
    const toggleNav = () => (showMenu.value = !showMenu.value);
    const closeNav = () => (showMenu.value = false);
    return { showMenu, toggleNav, closeNav};
  },
};
</script>