<template>
  <div class="quiz-container">
    <b-jumbotron>
      <template v-slot:lead>
        {{ currentQuestion.question }}
      </template>

      <hr class="my-4" />

      <p v-for="(answer, index) in answers" :key="index">
        {{ answer }}
      </p>
      <span><b-button variant="primary" href="#">Submit</b-button></span>
      <span>
        <b-button @click="next" variant="success" href="#">Next</b-button>
      </span>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  props: {
    currentQuestion: Object,
    next: Function
  },
  // computed: {
  //   answers() {
  //     let answers = [];
  //     answers = [...this.currentQuestion.incorrect_answer];
  //     answers.push(this.currentQuestion.correct_answer);
  //     return answers;
  //   }
  // },
  mounted() {
    console.log(this.currentQuestion);
  }
};
</script>
