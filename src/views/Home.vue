<template>
  <main
    class="relative h-screen w-screeen flex flex-col justify-center items-center gap-10 pb-40 ps-10 lg:gap-8 lg:pb-100 lg:ps-50 bg-[url('@/assets/images/Mobile/Mobile_MainPage_Background.png')] bg-cover bg-center overflow-hidden lg:bg-[url('@/assets/images/MaXing_Background_MainPage_Pic.webp')] transition-all duration-2000 ease-out"
  >
    <!-- Speak Bubble -->
    <div class="absolute w-full h-full top-0 left-0 z-50">
      <img
        src="@/assets/images/SpeakBubble.gif"
        class="hidden lg:block absolute w-full h-full top-0 left-0 object-cover object-center pointer-events-none select-none"
        alt="SpeakBubble"
      />
      <img
        src="@/assets/images/Mobile/Mobile_SpeakBubble.gif"
        class="block lg:hidden absolute w-full h-full top-0 left-0 object-cover object-center pointer-events-none select-none"
        alt="SpeakBubble_mobile"
      />
    </div>

    <!-- School Title -->
    <section class="z-50">
      <div
        :class="[
          'transition-all duration-3000 ease-out',
          isLoaded ? 'opacity-100' : 'opacity-0',
        ]"
        class="max-w-80 2xl:max-w-130 lg:max-w-150 h-auto flex items-center justify-center lg:justify-start"
      >
        <img
          src="@/assets/images/Web_logo.png"
          class="pointer-events-none select-none"
          alt="Changan_cover"
        />
      </div>
    </section>
    <!-- Menu Buttons -->
    <section class="flex items-center justify-center font-bold z-50">
      <div
        :class="[
          'transition-all duration-3000 ease-out',
          isLoaded ? 'opacity-100' : 'opacity-0',
        ]"
        class="flex flex-col gap-3 pt-5 ps-18 lg:flex-row lg:gap-0 lg:p-0 items-center justify-center text-2xl lg:text-4xl"
      >
        <router-link
          to="/about"
          class="relative"
          @mouseover="hoveredIndex = 0"
          @mouseleave="hoveredIndex = null"
        >
          <img
            :src="hoveredIndex === 0 ? buttonSelected : buttonUnselected"
            class="pointer-events-none select-none w-35 lg:w-60"
            alt="Button_1"
          />
          <span
            class="absolute inset-0 flex items-center justify-center lg:tracking-widest"
            >校園探索</span
          >
        </router-link>
        <router-link
          to="/actions"
          class="relative -translate-y-0 lg:translate-y-25"
          @mouseover="hoveredIndex = 1"
          @mouseleave="hoveredIndex = null"
          ><img
            :src="hoveredIndex === 1 ? buttonSelected : buttonUnselected"
            class="pointer-events-none select-none w-35 lg:w-60"
            alt="Button_2"
          />
          <span
            class="absolute inset-0 flex items-center justify-center lg:tracking-widest"
            >SDGs行動</span
          ></router-link
        >
        <router-link
          to="/sdgs"
          class="relative translate-x-0 lg:-translate-x-18"
          @mouseover="hoveredIndex = 2"
          @mouseleave="hoveredIndex = null"
          ><img
            :src="hoveredIndex === 2 ? buttonSelected : buttonUnselected"
            class="pointer-events-none select-none w-35 lg:w-60"
            alt="Button_3"
          />
          <span
            class="absolute inset-0 flex items-center justify-center lg:tracking-widest"
            >SDGs成果</span
          ></router-link
        >
      </div>
    </section>
  </main>
</template>
<script setup>
import { ref, onMounted, onUnmounted } from "vue";
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
