<template>
  <main class="flex h-screen items-center justify-center bg-gray-100">
    <div class="bg-wite container shadow-lg rounded-lg px-12 py-6">
      <!-- score container -->

      <div class="text-right text-gray-800">
        <p class="text-sm leading-3">score</p>
        <p class="front-bold">60</p>
      </div>

      <!-- timer counter  -->
      <div class="bg-white shadow-lg p-2 rounded-full w-full h-5">
        <div class="bg-blue-700 rounded-full w-11/12 h-full"></div>
      </div>
      <div class="rounded-lg bg-gray-100 p-2 nevmorph-1 text-center font-bold text-gray-800 mt-8">
        <div class="bg-white p-5">{{currentQuestion.question}}</div>
      </div>

      <!-- option answer  -->

      <div>
        <div class="mt-8">
          <div v-for="(choice,index) in currentQuestion.choices" :key="index">
            <div class="nevmorph-1 option-default bg-gray-100 p-2 rounded-lg mb-3 relative">
              <div
                class="bg-blue-700 p-1 transform rotate-45 rounded-md h-10 w-10 text-white font-bold absolute right-0 top-2"
              >
                <p class="transform -rotate-45">+10</p>
              </div>
              <div class="rounded-lg font-bold flex p-2">
                <div class="p-3 rounded-lg">{{index}}</div>
                <div class="flex items-center pl-6">{{choice}}</div>
              </div>
            </div>
          </div>
        </div>
        <div class="mt-8 text-center">
          <div class="h-1 w-12 rounded-full bg-gray-800 mx-auto"></div>
          <p class="font-bold text-gray-800">2/10</p>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
// @ is an alias to /src

import { onMounted,ref} from "vue";
export default {

  setup() {
    let questionCounter = ref(0);
    const currentQuestion = ref({
      question: "",
      answer: 1,
      choices: [],
    });

    const questions = [
      {
        question: "which programming language shares its name with an island",
        answer: 1,
        choices: ["java", "python", "c", "jakrta"],
      },
      {
        question: "who The Best Player in 2020",
        answer: 2,
        choices: ["Messi", "ronaldo", "juan", "locaco"],
      },
      {
        question: "What The name Of joker In anime Hunter X Hunter ",
        answer: 1,
        choices: ["Hisuka", "Goan", "Kilowa", "Elimo"],
      },
    ];

    let onQuizStart = ()=>{
      currentQuestion.value = questions[questionCounter.value];
    };
     

    onMounted(() => {
      onQuizStart();
    });
    return { currentQuestion, questions, questionCounter, onQuizStart };
  },
};
</script>

<style scoped>

.nevmorph-1 {
  box-shadow:6px 6px 18px rgba(0,0,0,0.09), -6px -6px 18px #ffffff; 
}
.container {
  width: 400px;
}
</style>
