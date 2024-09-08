<template>
  <div class="home">
    <div class="aspect-ratio-box">
      <div class="relative-container">
        <img src="../assets/icons/rightview.png" alt="Bangsal Kencana" class="bg-image">
        <div class="benda">
          <div class="left-arrow">
            <img src="../assets/icons/left.png" alt=""  @click="active('front')">
          </div>
          <div class="tiang-right">
            <img src="../assets/icons/right-tiang.png" alt="Bangsal Kencana" class="w-[86%]" :class="{ 'hint': test }" @click="tiangLuar">
          </div>
          <img 
            src="../assets/icons/sun.png" 
            alt="Toggle Button" 
            @click="changeTest" 
            class="sun-button"
            :class="{'hint': test}"
          >
        </div>
        <div class="penjelasan" :class="{'z-10': isCard, 'z-[2]': !isCard}">
          <div :class="{'modal-overlay': isCard}">
          </div>
          <div class="rectangle" @click="close"></div>
            <div class="tiang-luar" v-if="isTiangLuar">
              <img src="../assets/icons/tiang-luar.png" alt="">
            </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, inject } from 'vue';

export default {
  setup() {
    const test = ref(false);
    const activeView = inject('activeView');

    const changeTest = () => {
      test.value = !test.value;
    };

    const active=(a)=>{
      if(a='front') {
        activeView.value=0;
      }
    }

    const isCard = ref(false);
    const isTiangLuar = ref(false);

    const tiangLuar = () => {
      isCard.value = !isCard.value;
      isTiangLuar.value = !isTiangLuar.value;
    };

    const close = () => {
      isCard.value = false;
      isTiangLuar.value = false;
    };

    return {
      close,
      tiangLuar,
      isCard,
      test,
      active,
      changeTest,
      isTiangLuar
    };
  },
};
</script>

<style scoped>
.home {
  @apply w-screen h-screen flex justify-center items-center bg-black overflow-hidden;
}

.aspect-ratio-box {
  position: relative;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.relative-container {
  position: relative;
  width: 100%;
  height: 56.25vw; /* 16:9 aspect ratio (9/16 = 0.5625) in terms of width */
  max-height: 100vh; /* Ensure it doesn't exceed viewport height */
  max-width: 177.78vh; /* 16:9 aspect ratio in terms of height */
}

.modal-overlay {
    @apply fixed inset-0 bg-black bg-opacity-40;
    z-index: 4;
}

.bg-image {
  @apply absolute top-0 left-0 w-full h-full object-contain;
  z-index: 1;
}

.benda {
  @apply absolute top-0 left-0 w-full h-full;
  z-index: 3;
}

.tiang1 {
  position: absolute;
  width: 3%;
  top: 55%;
  left: 58.4%;
  cursor: pointer;
}

.tiang-right {
  position: absolute;
  width: 4.6%;
  top: 49%; /* Relative to the box */
  left: 46.25%; /* Relative to the box */
  cursor: pointer;
}

.tanaman1 {
  position: absolute;
  width: 6%;
  top: 69%; /* Relative to the box */
  left: 55%; /* Relative to the box */
  cursor: pointer;
}

.tiang-right:hover, .left-arrow:hover {
  filter: drop-shadow(1.5px 0 0 #eca868) drop-shadow(0 1.5px 0 #f0c22e) drop-shadow(-1.5px 0 0 #cae557) drop-shadow(0 -1.5px 0 #bb6016)
}

.tanaman2 {
  position: absolute;
  width: 6%;
  top: 69%; /* Relative to the box */
  left: 39.5%; /* Relative to the box */
  cursor: pointer;
}

.rectangle {
  @apply bg-gray-600 opacity-0;
  position: absolute;
  width: 5%;
  height: 4%;
  top: 20.5%;
  left: 59%;
  z-index: 12;
  cursor: pointer;
}

.penjelasan {
  @apply absolute top-0 left-0 w-full h-full;
}

.sun-button {
  position: absolute;
  width: 5%; /* Relative to the box */
  top: 4%; /* Relative to the box */
  left: 3%; /* Relative to the box */
  transform: translate(-50%, -50%);
  cursor: pointer;
}

.hint {
    filter: drop-shadow(1.5px 0 0 #eca868) drop-shadow(0 1.5px 0 #f0c22e) drop-shadow(-1.5px 0 0 #cae557) drop-shadow(0 -1.5px 0 #bb6016)
}

.left-arrow {
  position: absolute;
  width: 6%;
  top: 85%;
  /* Relative to the box */
  left: 3%;
  /* Relative to the box */
  cursor: pointer;
}

.tiang-luar {
  position: absolute;
  width: 30%;
  top: 20%;
  left: 35%;
  z-index: 11;
}
</style>
