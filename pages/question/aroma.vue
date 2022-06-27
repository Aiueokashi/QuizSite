<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="10" md="8" lg="6" xl="5">
      <QuizStepperComponent
        :quiz-name="quizName"
        :quiz-all-questions="quizAllQuestions"
      />
    </v-col>
  </v-row>
</template>

<script>
import QuizStepperComponent from '../../components/AromaQuizStepper'
import aromatic from '@/static/chemistry/aromatic_compounds.json'
export default {
  components: {
    QuizStepperComponent,
  },
  data() {
    return {
      restartQuiz: false,
    }
  },
  computed: {
    quizName() {
      let quizName = null
      quizName = "芳香族化合物"
      return quizName
    },
    quizAllQuestions() {
      let verbs = null
        verbs = aromatic.map(({ img, name }) => {
          return {
            img,
            correctAnswer: name,
          }
        })
      return verbs
    },
  },
}
</script>
