<template>
  <div class="home">
    <div class="aspect-ratio-box">
      <div class="relative-container">
        <img src="../assets/icons/inside.png" alt="Bangsal Kencana" class="bg-image">
        <div class="benda">
          <div class="in-arrow">
            <img src="../assets/icons/left.png" alt="" @click="active('front')">
          </div>
          <div class="tiang-right">
            <img src="../assets/icons/tiang_b1.png" alt="Bangsal Kencana" class="w-[86%]" :class="{ 'hint': test }"
              @click="sakaGuru">
          </div>
          <div class="tiang-left">
            <img src="../assets/icons/tiang_b1.png" alt="Bangsal Kencana" class="w-[86%]" :class="{ 'hint': test }"
              @click="sakaGuru">
          </div>

          <div class="tiang3 oren">
            <img src="../assets/icons/tiang3.png" alt="Bangsal Kencana" class="w-[86%]" :class="{ 'hint': test }"
              @click="tiangDalam">
          </div>

          <div class="gong">
            <img src="../assets/icons/gong.png" alt="Bangsal Kencana" class="w-[86%]" :class="{ 'hint': test }"
              @click="gong">
          </div>

          <div class="lampu2 oren">
            <img src="../assets/icons/lampu2.png" alt="Bangsal Kencana" class="w-[86%]" :class="{ 'hint': test }"
              @click="lampuDalam">
          </div>


          <div class="pigura-group">
            <div class="oren pigura1">
              <img src="../assets/icons/pigura1.png" alt="Bangsal Kencana" class="w-[86%]" @click="pigura" :class="{ 'hint': test }">>
            </div>
            <div class="oren pigura2">
              <img src="../assets/icons/pigura2.png" alt="Bangsal Kencana" class="w-[86%]" @click="pigura" :class="{ 'hint': test }">>
            </div>
          </div>
          <img src="../assets/icons/sun.png" alt="Toggle Button" @click="changeTest" class="sun-button"
            :class="{ 'hint': test }">
        </div>
        <div class="penjelasan" :class="{ 'z-10': isCard, 'z-[2]': !isCard }">
          <div :class="{ 'modal-overlay': isCard }">
          </div>
          <div class="rectangle" @click="close"></div>
          <div class="isi" v-if="isTiangLuar">
            <img src="../assets/icons/tiang-luar.png" alt="">
          </div>
          <div class="isi" v-if="isGong">
            <img src="../assets/icons/gong-p.png" alt="">
          </div>
          <div class="isi" v-if="isSakaGuru">
            <img src="../assets/icons/saka-guru.png" alt="">
          </div>
          <div class="isi" v-if="isLampuDalam">
            <img src="../assets/icons/lampu-dalam.png" alt="">
          </div>
          <div class="isi" v-if="isTiangDalam">
            <img src="../assets/icons/tiang-dalam-p.png" alt="">
          </div>
          <div class="isi" v-if="isPigura">
            <img src="../assets/icons/pigura-p.png" alt="">
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

    const active = (a) => {
      if (a = 'front') {
        activeView.value = 0;
      }
    }

    const isCard = ref(false);
    const isTiangLuar = ref(false);
    const isGong = ref(false);
    const isSakaGuru = ref(false);
    const isLampuDalam = ref(false);
    const isTiangDalam = ref(false);
    const isPigura = ref(false);

    const tiangLuar = () => {
      isCard.value = !isCard.value;
      isTiangLuar.value = !isTiangLuar.value;
    };
    const gong = () => {
      isCard.value = !isCard.value;
      isGong.value = !isGong.value;
    };
    const sakaGuru = () => {
      isCard.value = !isCard.value;
      isSakaGuru.value = !isSakaGuru.value;
    };
    const lampuDalam = () => {
      isCard.value = !isCard.value;
      isLampuDalam.value = !isSakaGuru.value;
    };
    const tiangDalam = () => {
      isCard.value = !isCard.value;
      isTiangDalam.value = !isSakaGuru.value;
    };

    const pigura = () => {
      isCard.value = !isCard.value;
      isPigura.value = !isPigura.value;
    };

    const close = () => {
      isCard.value = false;
      isTiangLuar.value = false;
      isGong.value = false;
      isSakaGuru.value=false;
      isLampuDalam.value=false;
      isTiangDalam.value=false;
      isPigura.value=false;
    };

    return {
      close,
      tiangLuar,
      isCard,
      test,
      active,
      changeTest,
      isTiangLuar,
      gong,
      isGong,
      isSakaGuru,
      sakaGuru,
      isLampuDalam,
      lampuDalam,
      isTiangDalam,
      tiangDalam,
      isPigura,
      pigura
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
  height: 56.25vw;
  /* 16:9 aspect ratio (9/16 = 0.5625) in terms of width */
  max-height: 100vh;
  /* Ensure it doesn't exceed viewport height */
  max-width: 177.78vh;
  /* 16:9 aspect ratio in terms of height */
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

.gong {
  position: absolute;
  width: 16.7%;
  top: 45%;
  /* Relative to the box */
  left: 79.75%;
  /* Relative to the box */
  cursor: pointer;
}

.lampu2 {
  position: absolute;
  width: 11.7%;
  top: -1%;
  /* Relative to the box */
  left: 43%;
  /* Relative to the box */
  cursor: pointer;
}

.pigura1 {
  position: absolute;
  width: 34.7%;
  top: 30%;
  /* Relative to the box */
  left: 27.75%;
  /* Relative to the box */
  cursor: pointer;
}

.pigura2 {
  position: absolute;
  width: 15.2%;
  top: 30%;
  /* Relative to the box */
  left: 10.75%;
  /* Relative to the box */
  cursor: pointer;
}


.tiang-left {
  position: absolute;
  width: 5.9%;
  top: 2%;
  /* Relative to the box */
  left: 22.75%;
  /* Relative to the box */
  cursor: pointer;
  z-index: 1;
}

.tiang3 {
  position: absolute;
  width: 3.65%;
  top: 36%;
  /* Relative to the box */
  left: 0.5%;
  /* Relative to the box */
  cursor: pointer;
}

.tiang-right {
  position: absolute;
  width: 5.9%;
  top: 2%;
  /* Relative to the box */
  left: 72%;
  /* Relative to the box */
  cursor: pointer;
}


.tanaman1 {
  position: absolute;
  width: 6%;
  top: 69%;
  /* Relative to the box */
  left: 55%;
  /* Relative to the box */
  cursor: pointer;
}

.gong:hover,
.tiang-right:hover,
.tiang-left:hover,
.in-arrow:hover,
.oren:hover {
  filter: drop-shadow(1.5px 0 0 #ffff) drop-shadow(0 1.5px 0 #ffff) drop-shadow(-1.5px 0 0 #ffff) drop-shadow(0 -1.5px 0 #ffff)
}

.pigura-group:hover .oren {
  filter: drop-shadow(1.5px 0 0 #ffff) drop-shadow(0 1.5px 0 #ffff) drop-shadow(-1.5px 0 0 #ffff) drop-shadow(0 -1.5px 0 #ffff)
}

.tanaman2 {
  position: absolute;
  width: 6%;
  top: 69%;
  /* Relative to the box */
  left: 39.5%;
  /* Relative to the box */
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
  width: 5%;
  /* Relative to the box */
  top: 4%;
  /* Relative to the box */
  left: 3%;
  /* Relative to the box */
  transform: translate(-50%, -50%);
  cursor: pointer;
}

.hint {
  filter: drop-shadow(1.5px 0 0 #ffffff) drop-shadow(0 1.5px 0 #ffffff) drop-shadow(-1.5px 0 0 #ffffff) drop-shadow(0 -1.5px 0 #ffffff)
}

.in-arrow {
  position: absolute;
  width: 6%;
  top: 85%;
  /* Relative to the box */
  left: 3%;
  /* Relative to the box */
  cursor: pointer;
}

.isi {
  position: absolute;
  width: 30%;
  top: 20%;
  left: 35%;
  z-index: 11;
}
</style>
