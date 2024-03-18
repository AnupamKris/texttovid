<template>
  <div class="home">
    <section v-if="currentStep == 0">
      <input type="text" v-model="topic" placeholder="Write something...">
      <button @click="nextStep" :class="{ visible: topic.length }">Continue</button>
    </section>
    <section v-else-if="currentStep == 1">
      <h1>{{ sentences[currentSentence].text }}</h1>
      <div class="images">
        <img :class="{ selected: sentences[currentSentence].selectedImage == 0 }"
          :src="sentences[currentSentence].images[0]" @click="sentences[currentSentence].selectedImage = 0" alt="1" />
        <img :class="{ selected: sentences[currentSentence].selectedImage == 1 }"
          :src="sentences[currentSentence].images[1]" @click="sentences[currentSentence].selectedImage = 1" alt="2" />
        <img :class="{ selected: sentences[currentSentence].selectedImage == 2 }"
          :src="sentences[currentSentence].images[2]" @click="sentences[currentSentence].selectedImage = 2" alt="3" />
        <img :class="{ selected: sentences[currentSentence].selectedImage == 3 }"
          :src="sentences[currentSentence].images[3]" @click="sentences[currentSentence].selectedImage = 3" alt="4" />
      </div>
      <div class="btns">
        <button class="visible" @click="currentSentence == 0 ? prevStep : currentSentence--">Prev</button>
        <button class="visible"
          @click="currentSentence == sentences.length - 1 ? nextStep() : currentSentence++">Next</button>
      </div>
    </section>
  </div>
</template>

<script setup>
const currentStep = ref(0)

// step 1
const topic = ref("")

// step 2
const sentences = ref([
  {
    text: "This is the first sentence",
    images: [
      "https://picsum.photos/200/300",
      "https://picsum.photos/200/300",
      "https://picsum.photos/200/300",
      "https://picsum.photos/200/300"
    ],
    selectedImage: null
  },
  {
    text: "This is the second sentence",
    images: [
      "https://picsum.photos/200/300",
      "https://picsum.photos/200/300",
      "https://picsum.photos/200/300",
      "https://picsum.photos/200/300"
    ],
    selectedImage: null
  },
  {
    text: "This is the third sentence",
    images: [
      "https://picsum.photos/200/300",
      "https://picsum.photos/200/300",
      "https://picsum.photos/200/300",
      "https://picsum.photos/200/300"
    ],
    selectedImage: null
  },
  {
    text: "This is the fourth sentence",
    images: [
      "https://picsum.photos/200/300",
      "https://picsum.photos/200/300",
      "https://picsum.photos/200/300",
      "https://picsum.photos/200/300"
    ],
    selectedImage: null
  }

])
const currentSentence = ref(0)


const nextStep = () => {
  // if (topic.value.length) {
  //   router.push({ name: "Chat", params: { topic: topic.value } })
  // }
  console.log("NEXT STEP");
  currentStep.value++
}

const prevStep = () => {
  currentStep.value--
}


</script>

<style lang="scss" scoped>
.home {
  height: 100%;
  width: 100%;


  display: flex;
  justify-content: center;
  align-items: center;
  background: #131519;

  section {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;

    height: 100%;
    width: 100%;
    color: #abb2bf;


    input {
      width: 70%;
      height: 70px;
      border-radius: 5px;
      border: 1px solid #353a44;
      background: #21252b;
      outline: none;
      font-size: 18px;
      text-align: center;
    }

    button {
      height: 50px;
      background: #ffffff;
      border: none;
      font-weight: 600;
      padding: 0 15px;
      border-radius: 25px;
      margin-top: 10px;
      opacity: 0;
      height: 0;
      transition: 0.3s;
    }

    .visible {
      opacity: 1;
      height: 50px;
    }

    .images {
      display: flex;
      justify-content: space-between;
      width: 80%;
      margin-top: 20px;

      img {
        border-radius: 5px;
        // transition: 0.3s;
      }

      .selected {
        border: 2px solid #abb2bf;
        border-spacing: 2px;
      }
    }

    .btns {
      display: flex;
      justify-content: space-between;
      width: 200px;
      margin-top: 20px;

      button {
        width: 90px;
      }

    }
  }
}
</style>