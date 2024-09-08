<template>
  <div class="home">
    <div class="aspect-ratio-box">
      <div class="relative-container">
        <img src="../assets/icons/front.png" alt="Bangsal Kencana" class="bg-image">
        <div class="benda">
          <div class="right-arrow">
            <img src="../assets/icons/right.png" alt="" @click="active('right')">
          </div>
          <div class="in-arrow">
            <img src="../assets/icons/in.png" alt="" @click="active('inside')">
          </div>
          <div class="tiang1">
            <img src="../assets/icons/tiang2.png" alt="Bangsal Kencana" class="w-[86%]" :class="{ 'hint': test }"
              @click="tiangLuar">
          </div>

          <div class="tiang2">
            <img src="../assets/icons/tiang2.png" alt="Bangsal Kencana" class="w-[86%]" :class="{ 'hint': test }"
              @click="tiangLuar">
          </div>
          <div class="tanaman1">
            <img src="../assets/icons/tanaman1.png" alt="Bangsal Kencana" class="w-[86%]" :class="{ 'hint': test }"
              @click="porce">
          </div>
          <div class="tanaman2">
            <img src="../assets/icons/tanaman1.png" alt="Bangsal Kencana" class="w-[86%]" :class="{ 'hint': test }"
              @click="porce">
          </div>
          <div class="lampu">
            <img src="../assets/icons/lampu1.png" alt="Bangsal Kencana" class="w-[86%]" :class="{ 'hint': test }"
              @click="lampuLuar">
          </div>
          <img src="../assets/icons/sun.png" alt="Toggle Button" @click="changeTest" class="sun-button"
            :class="{ 'hint': test }">
          <img src="../assets/icons/information-button.png" alt="Toggle Button" @click="info"
            class="information-button">
        </div>
        <div class="penjelasan" :class="{ 'z-10': isCard, 'z-[2]': !isCard }">
          <div :class="{ 'modal-overlay': isCard }">
          </div>
          <div class="rectangle1" @click="close" v-if="isInfo"></div>
          <div class="rectangle" @click="close" v-else></div>
          <div class="tiang-luar" v-if="isTiangLuar">
            <img src="../assets/icons/tiang-luar.png" alt="">
          </div>
          <div class="tiang-luar" v-if="isLampuLuar">
            <img src="../assets/icons/lampu-luar.png" alt="">
          </div>
          <div class="tiang-luar" v-if="isPorce">
            <img src="../assets/icons/porce.png" alt="">
          </div>
          <div class="inf" v-if="isInfo">
            <div class="info-box">
              <h1 class="text-center tnr text-4xl mb-10 mt-4">Bangsal Kencana</h1>
              <p class="info-text tnr mx-10">
                Bangsal Kencana adalah Bangunan utama Kraton Yogyakarta yang
                terletak ditengah-tengah plataran Kedhaton di sebelah timur Gedhung Prabayeksa dan menghadap ke timur.
                Bangunan Bangsal Kencana
                berbentuk Joglo Sinom Mangkurat. Bangsal kencana di bangun oleh Sultan Hamengku Buwono I pada tahun 1719
                tahun Jawa / 1792 Masehi.
                Bangsal Kencana sendiri memiliki arti bangsal keemasan karena sebagian struktur kayu dilapisi emas.
                Bangsal Kencana memiliki fungsi sebagai tempat singgasana sultan serta digelarnya berbagai upacara
                penting penting di lingkungan kraton.
              </p>
              <h1 class="text-center tnr text-4xl mb-10 mt-4">Credit</h1>
              <p class="info-text tnr mx-10">Web: Sofwan</p>
              <p class="info-text tnr mx-10">Perspektif Depan & Atas: Lubna</p>
              <p class="info-text tnr mx-10">Perspektif Kanan: Aruni</p>
              <p class="info-text tnr mx-10">Perspektif Dalam: Arsel & Aruni</p>
              <p class="info-text tnr mx-10">Misc. Art: Aruni</p>
              <p class="info-text tnr mx-10">Keterangan & Informasi: Erfa & Izzan</p>
              <p class="info-text tnr mx-10">Foto: Sofwan</p>
              <br>
              <a class="info-text tnr mx-10" href="https://www.flaticon.com/free-icons/information"
                title="information icons">Information icons created by Freepik - Flaticon</a>
              <p class="info-text1 tnr mx-10 mt-10 text-center text-blue-400">"Kalau Bandung Bondowoso bisa bikin candi
                dalam semalam, mas mbak ini tentu gabisa"</p>
              <div class="qr-container">
                <img src="../assets/icons/qr.png" alt="QR Code">
              </div>
            </div>
          </div>

        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { inject, ref } from 'vue';

export default {
  setup() {
    const test = ref(false);
    const isTiangLuar = ref(false);
    const isLampuLuar = ref(false);
    const isPorce = ref(false);
    const isCard = ref(false);
    const isInfo = ref(false);
    const activeView = inject('activeView');

    const changeTest = () => {
      test.value = !test.value;
    };

    const tiangLuar = () => {
      isCard.value = !isCard.value;
      isTiangLuar.value = !isTiangLuar.value;
    };

    const info = () => {
      isCard.value = !isCard.value;
      isInfo.value = !isInfo.value;
    };

    const lampuLuar = () => {
      isCard.value = !isCard.value;
      isLampuLuar.value = !isLampuLuar.value;
    };
    const porce = () => {
      isCard.value = !isCard.value;
      isPorce.value = !isPorce.value;
    };

    const active = (a) => {
      if (a === 'right') {
        activeView.value = 1;
      }
      else if (a == 'inside') {
        activeView.value = 2;
      }
    }

    const close = () => {
      isCard.value = false;
      isTiangLuar.value = false;
      isLampuLuar.value = false;
      isPorce.value = false;
      isInfo.value = false;
    };

    return {
      test,
      active,
      changeTest,
      isCard,
      isTiangLuar,
      tiangLuar,
      close,
      lampuLuar,
      isLampuLuar,
      porce,
      isPorce,
      info,
      isInfo
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

.modal-overlay {
  @apply fixed inset-0 bg-black bg-opacity-40;
  z-index: 4;
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

.bg-image {
  @apply absolute top-0 left-0 w-full h-full object-contain;
  z-index: 1;
}

.benda {
  @apply absolute top-0 left-0 w-full h-full;
  z-index: 3;
}

.penjelasan {
  @apply absolute top-0 left-0 w-full h-full;
}

.tiang1 {
  position: absolute;
  width: 3%;
  top: 55%;
  left: 58.4%;
  cursor: pointer;
}

.tiang2 {
  position: absolute;
  width: 3%;
  top: 55%;
  /* Relative to the box */
  left: 39.1%;
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

.tiang-luar {
  position: absolute;
  width: 30%;
  top: 20%;
  left: 35%;
  z-index: 11;
}

.inf {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 3%;
  left: 0%;
  z-index: 11;
}

.tanaman1:hover,
.tanaman2:hover,
.tiang1:hover,
.tiang2:hover,
.right-arrow:hover,
.in-arrow:hover,
.lampu:hover {
  filter: drop-shadow(1.5px 0 0 #eca868) drop-shadow(0 1.5px 0 #f0c22e) drop-shadow(-1.5px 0 0 #cae557) drop-shadow(0 -1.5px 0 #bb6016)
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

.lampu {
  position: absolute;
  width: 6%;
  top: 54%;
  /* Relative to the box */
  left: 47.5%;
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

.rectangle1 {
  @apply bg-red-600;
  position: absolute;
  width: 5%;
  height: 4%;
  top: 3%;
  left: 94%;
  z-index: 12;
  cursor: pointer;
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

.information-button {
  position: absolute;
  width: 3%;
  /* Relative to the box */
  top: 4%;
  /* Relative to the box */
  left: 97%;
  /* Relative to the box */
  transform: translate(-50%, -50%);
  cursor: pointer;
}

.hint {
  filter: drop-shadow(1.5px 0 0 #eca868) drop-shadow(0 1.5px 0 #f0c22e) drop-shadow(-1.5px 0 0 #cae557) drop-shadow(0 -1.5px 0 #bb6016)
}

.right-arrow {
  position: absolute;
  width: 6%;
  top: 85%;
  /* Relative to the box */
  left: 89%;
  /* Relative to the box */
  cursor: pointer;
}

.in-arrow {
  position: absolute;
  width: 6%;
  top: 85%;
  /* Relative to the box */
  left: 48%;
  /* Relative to the box */
  cursor: pointer;
}

.info-box {
  position: absolute;
  width: 80%;
  /* Increase width to 80% */
  height: 80%;
  /* Increase height to 80% */
  top: 10%;
  /* Adjust positioning from the top */
  left: 10%;
  /* Adjust positioning from the left */
  background-color: rgba(255, 255, 255, 0.9);
  /* Semi-transparent background */
  padding: 30px;
  /* Padding for space around the text */
  border-radius: 10px;
  /* Rounded corners */
  z-index: 12;
  /* Layering on top */
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
  /* Shadow for the box */
  overflow-y: auto;
  /* Enable vertical scrolling if content exceeds box height */
}

.info-text {
  color: #333;
  /* Text color */
  font-size: 1.2rem;
  /* Font size */
  text-align: justify;
  /* Justify the text */
  line-height: 1.6;
  /* Line height for readability */
  word-wrap: break-word;
  /* Break long words if necessary */
}

.info-text1 {
  /* Text color */
  font-size: 1.2rem;
  /* Font size */
  text-align: center;
  /* Justify the text */
  line-height: 1.6;
  /* Line height for readability */
  word-wrap: break-word;
  /* Break long words if necessary */
}

.tnr {
  font-family: "Lucida Console", "Courier New", monospace;
}

.qr-container {
  display: flex;       /* Flexbox layout */
  justify-content: center; /* Center QR code horizontally */
  width: 100%;         /* Ensure the QR code container takes full width */
}

.qr-container img {
  @apply mt-10;
  max-width: 200px;    /* Restrict the size of the QR code */
  width: 50%;          /* Set QR code width to 50% of the container */
  height: auto;        /* Maintain the aspect ratio */
}
</style>
