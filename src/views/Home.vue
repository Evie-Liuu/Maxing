<template>
  <main
    class="relative h-screen w-screeen flex flex-col justify-center items-center lg:gap-8 lg:pb-95 lg:ps-40 bg-[url('@/assets/images/Mobile/Mobile_MainPage_Background.png')] bg-cover bg-center overflow-hidden lg:bg-[url('@/assets/images/MaXing_MainPage_Pic.webp'),_url('@/assets/images/MaXing_Background.webp')] lg:[background-repeat:no-repeat,no-repeat] lg:[background-position:center,center] lg:[background-size:cover,cover] transition-all duration-2000 ease-out"
  >
    <!-- School Logo -->
    <section>
      <div class="hidden lg:block absolute w-full h-full top-0 left-0">
        <img
          :src="speakImages[currentLanguage][currentIndex - 1]"
          :class="[
            'absolute w-full h-full top-0 left-0 object-cover object-center pointer-events-none select-none transition-all duration-500',
            isAnimating ? 'scale-110 opacity-80' : 'scale-100 opacity-100',
          ]"
          alt="speakBubble"
        />
        <div
          class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-full h-full  overflow-hidden"
        >
          <!-- <img src="/example.jpg" class="w-full h-full object-cover" /> -->
          <div
            class="absolute inset-0 flex items-center justify-center -translate-x-[1vw] text-4xl w-[1920px] h-[1080px] aspect-video"
          >
            Hello
          </div>
        </div>
        <div class="absolute inset-0 w-full h-full">
          <p class="absolute inset-0 w-full h-full">你好</p>
        </div>
      </div>
      <div class="block lg:hidden absolute w-full h-full top-0 left-0">
        <img
          :src="speakImages.chinese[currentIndex - 1]"
          :class="[
            'absolute w-full h-full top-0 left-0 object-cover object-center pointer-events-none select-none transition-all duration-500',
            isAnimating ? 'scale-110 opacity-80' : 'scale-100 opacity-100',
          ]"
          alt="Changan_logo"
        />
      </div>
    </section>

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
    <section class="flex items-center justify-center font-bold">
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
import { ref, onMounted, onUnmounted } from "vue";
import buttonUnselected from "@/assets/images/Bar_Unselected.png";
import buttonSelected from "@/assets/images/Bar_Selected.png";
import Speak_Chinese1 from "@/assets/images/Speak_Chinese1.png";
import Speak_Chinese2 from "@/assets/images/Speak_Chinese2.png";
import Speak_Chinese3 from "@/assets/images/Speak_Chinese3.png";
import Speak_Chinese4 from "@/assets/images/Speak_Chinese4.png";
import Speak_English1 from "@/assets/images/Speak_English1.png";
import Speak_English2 from "@/assets/images/Speak_English2.png";
import Speak_English3 from "@/assets/images/Speak_English3.png";
import Speak_English4 from "@/assets/images/Speak_English4.png";

const hoveredIndex = ref(null);
const isLoaded = ref(false);
const currentLanguage = ref("english");
const currentIndex = ref(1);
const isAnimating = ref(false);
let timer = null;

const speakImages = {
  english: [Speak_English1, Speak_English2, Speak_English3, Speak_English4],
  chinese: [Speak_Chinese1, Speak_Chinese2, Speak_Chinese3, Speak_Chinese4],
};
const speakText = {
  english: ["Hello", "Grass", "Sky", "Cloud"],
  chinese: ["你好", "草", "天空", "雲朵"],
};

const switchImage = () => {
  isAnimating.value = true;
  setTimeout(() => {
    if (currentLanguage.value === "chinese") {
      currentLanguage.value = "english";
      currentIndex.value = (currentIndex.value % 4) + 1;
    } else {
      currentLanguage.value = "chinese";
    }
    setTimeout(() => {
      isAnimating.value = false;
    }, 500);
  }, 500);
};

onMounted(() => {
  setTimeout(() => {
    isLoaded.value = true;
  }, 100);
  // timer = setInterval(switchImage, 3000);
});

onUnmounted(() => {
  if (timer) {
    clearInterval(timer);
  }
});
</script>
<style scoped>
</style>
