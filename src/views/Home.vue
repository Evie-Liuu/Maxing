<template>
  <main
    class="
      relative h-screen w-screeen flex flex-col justify-center items-center lg:gap-8 lg:pb-95 lg:ps-40 bg-[url('@/assets/images/Mobile/Mobile_MainPage_Background.png')] bg-cover bg-center overflow-hidden lg:bg-[url('@/assets/images/MaXing_MainPage_Pic.webp'),_url('@/assets/images/MaXing_Background.webp')] lg:[background-repeat:no-repeat,no-repeat] lg:[background-position:center,center] lg:[background-size:cover,cover]
      transition-all duration-2000 ease-out
    "
  >
    <!-- School Logo -->
    <!-- <div class="absolute w-full h-full top-0 left-0">
      <img
        src="@/assets/images/Web_ChangAn_Logo.png"
        class="hidden lg:block absolute w-full h-full top-0 left-0 object-cover object-center pointer-events-none select-none"
        alt="Changan_logo"
      />
      <img
        src="@/assets/images/Mobile/Mobile_ChangAn_Logo.png"
        class="block lg:hidden absolute w-full h-full top-0 left-0 object-cover object-center pointer-events-none select-none"
        alt="Changan_logo"
      />
    </div> -->

    <!-- Cover -->
    <!-- <section class="flex-shrink-0 z-50">
      <div
        :class="[
          'transition-all duration-3000 ease-out',
          isLoaded ? 'opacity-100' : 'opacity-0',
        ]"
        class="flex items-center justify-center lg:pt-8 lg:max-w-290 lg:-translate-y-35"
      >
        <img
          :src="IceCreamMelting"
          class="pointer-events-none select-none"
          alt="Changan_cover"
        />
      </div>
    </section> -->
    <!-- School Title -->
    <section class="">
      <div
        :class="[
          'transition-all duration-3000 ease-out',
          isLoaded ? 'opacity-100' : 'opacity-0',
        ]"
        class="lg:max-w-140 h-auto flex items-center justify-center lg:justify-start"
      >
        <img
          src="@/assets/images/Web_logo.png"
          class="pointer-events-none select-none"
          alt="Changan_cover"
        />
      </div>
    </section>
    <!-- Menu Buttons -->
    <section
      class="flex items-center justify-center font-bold"
    >
      <div
        :class="[
          'transition-all duration-3000 ease-out',
          isLoaded ? 'opacity-100' : 'opacity-0',
        ]"
        class="flex flex-col gap-5 pt-4 lg:flex-row lg:gap-15 items-center justify-center text-xl lg:text-3xl"
      >
        <router-link
          to="/about"
          class="relative"
          @mouseover="hoveredIndex = 0"
          @mouseleave="hoveredIndex = null"
        >
          <img
            :src="hoveredIndex === 0 ? buttonSelected : buttonUnselected"
            class="pointer-events-none select-none w-48 lg:w-60"
            alt="Button_1"
          />
          <span
            class="absolute inset-0 flex items-center justify-center tracking-widest"
            >校園探索</span
          >
        </router-link>
        <router-link
          to="/actions"
          class="relative -translate-y-5 lg:translate-y-0"
          @mouseover="hoveredIndex = 1"
          @mouseleave="hoveredIndex = null"
          ><img
            :src="hoveredIndex === 1 ? buttonSelected : buttonUnselected"
            class="pointer-events-none select-none w-48 lg:w-60"
            alt="Button_2"
          />
          <span
            class="absolute inset-0 flex items-center justify-center tracking-widest"
            >SDGs行動</span
          ></router-link
        >
        <router-link
          to="/sdgs"
          class="relative -translate-y-10 lg:translate-y-0"
          @mouseover="hoveredIndex = 2"
          @mouseleave="hoveredIndex = null"
          ><img
            :src="hoveredIndex === 2 ? buttonSelected : buttonUnselected"
            class="pointer-events-none select-none w-48 lg:w-60"
            alt="Button_3"
          />
          <span
            class="absolute inset-0 flex items-center justify-center tracking-widest"
            >SDGs成果</span
          ></router-link
        >
      </div>
    </section>
    <!-- <section class="h-70"></section> -->
  </main>
</template>
<script setup>
import { ref, onMounted } from "vue";
import buttonUnselected from "@/assets/images/Bar_Unselected.png";
import buttonSelected from "@/assets/images/Bar_Selected.png";

const hoveredIndex = ref(null);
const isLoaded = ref(false);

onMounted(() => {
  setTimeout(() => {
    isLoaded.value = true;
  }, 100);
});
</script>
<style scoped>
</style>
