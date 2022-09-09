<template>
  <v-stepper v-model="step">
    <v-stepper-header>
      <v-stepper-step :complete="step > 1" step="1"> </v-stepper-step>

      <v-divider></v-divider>

      <v-stepper-step :complete="step > 2" step="2"> </v-stepper-step>

      <v-divider></v-divider>

      <v-stepper-step step="3"> </v-stepper-step>
    </v-stepper-header>

    <v-stepper-items>
      <v-stepper-content step="1">
        <div v-if="step === 1">
          <h1>{{ quizName }}</h1>
          <v-select
            v-model.trim="numberOfQuestions"
            :items="[5, 10, 20, 30, 40, 50, 60, 70, 80, 90, 'All']"
            label="設問数を指定してください"
          ></v-select>
          <v-switch v-model="shuffleMode" label="Random mode"></v-switch>
          <v-btn
            color="primary"
            :disabled="!numberOfQuestions"
            @click="startQuiz"
          >
            Start quiz
          </v-btn>
          <v-alert class="mt-10" type="info">
            ランダムモードをオフにすると、化合物の辞書順で出題されます。
          </v-alert>
        </div>
      </v-stepper-content>

      <v-stepper-content step="2">
        <div v-if="step === 2">
          <StopwatchComponent @timer-changed="onTimerChanged" />
          <h2>
            {{ currentIndex + 1 }}/{{ numberOfQuestions }} {{ quizName }} 次の化合物の名前を答えなさい:
          </h2>
      <script id="viewer2Dscript" type="chemical/x-mdl-molfile" :src="'/chemData/2D/' + quizQuestions[currentIndex].name.split('/')[0] + '.mol'"></script>
       <span id="viewer2D" style="display:block" data-widget="Kekule.ChemWidget.Viewer2D"
        :data-chem-obj="'url(#' + quizQuestions[currentIndex].name.split('/')[0] + ')'" data-predefined-setting="basic" data-auto-size="true"></span>
          <v-form @submit.prevent="nextQuestion">
            <v-text-field
              v-model="currentAnswer"
              label="回答"
              placeholder="化合物名を打ち込んでください"
            ></v-text-field>
            <v-btn color="primary" :disabled="!currentAnswer" type="submit">
              次へ
            </v-btn>
          </v-form>
        </div>
      </v-stepper-content>

      <v-stepper-content step="3">
        <div v-if="step === 3">
          <h2>スコア: {{ score }}/{{ numberOfQuestions }}</h2>
          <h3 class="text-right">
            回答にかかった時間:
            {{ timer.hours }} : {{ timer.minutes }} : {{ timer.seconds }}
          </h3>
          <v-simple-table class="my-2">
            <template #default>
              <thead>
                <tr>
                  <th class="text-left">化合物</th>
                  <th class="text-left">正解</th>
                  <th class="text-left">あなたの回答</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="verb in quizQuestions" :key="verb.name">
                  <td><script :id="verb.correctAnswer.split('/')[0]" type="chemical/x-mdl-molfile" :src="'/chemData/2D/' + verb.correctAnswer.name.split('/')[0] + '.mol'"></script>
                      <span :id="'viewer2D' + name" style="display:block" data-widget="Kekule.ChemWidget.Viewer2D"
                      :data-chem-obj="'url(#' + verb.correctAnswer.name.split('/')[0] + ')'" data-predefined-setting="basic" data-auto-size="true"></span></td>
                  <td>{{ verb.correctAnswer }}</td>
                  <td :class="verb.isCorrect ? 'green--text' : 'red--text'">
                    {{ verb.yourAnswer }}
                  </td>
                </tr>
              </tbody>
            </template>
          </v-simple-table>
          <v-btn class="mt-2" color="primary" @click="startNewQuiz">
            再挑戦
          </v-btn>
        </div>
      </v-stepper-content>
    </v-stepper-items>
  </v-stepper>
</template>

<script>
import StopwatchComponent from './StopwatchComponent'
export default {
  components: {
    StopwatchComponent,
  },
  props: {
    quizName: {
      type: String,
      required: true,
    },
    quizAllQuestions: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      shuffleMode: true,
      quizQuestions: [],
      numberOfQuestions: null,
      currentIndex: 0,
      currentAnswer: null,
      score: 0,
      step: 1,
      timer: {
        hours: 0,
        minutes: 0,
        seconds: 0,
      },
    }
  },
  computed: {
  
  },
  watch: {
    numberOfQuestions() {
      this.initQuizQuestions()
    },
    shuffleMode() {
      this.initQuizQuestions()
    },
  },
  methods: {
    initQuizQuestions() {
      this.quizQuestions = this.quizAllQuestions
      this.numberOfQuestions =
        this.numberOfQuestions === 'All'
          ? this.quizAllQuestions.length
          : this.numberOfQuestions
      if (this.shuffleMode) {
        this.quizQuestions = this.quizQuestions
          .sort(() => Math.random() - Math.random())
          .slice(0, this.numberOfQuestions)
      } else {
        this.quizQuestions = this.quizQuestions
          .sort((a, b) => a.name.localeCompare(b.name))
          .slice(0, this.numberOfQuestions)
      }
    },
    startQuiz() {
      this.step = 2
    },
    nextQuestion() {
      this.currentAnswer = this.currentAnswer.toLowerCase()
      this.quizQuestions[this.currentIndex].yourAnswer = this.currentAnswer
      this.calculateScore()
      if (this.currentIndex < this.quizQuestions.length - 1) {
        this.currentAnswer = null
        this.currentIndex++
      } else {
        this.step = 3
      }
    },
    calculateScore() {
      const correctAnswers =
        this.quizQuestions[this.currentIndex].correctAnswer.split('/')
      if (
        correctAnswers[0] === this.currentAnswer ||
        correctAnswers[1] === this.currentAnswer ||
        this.quizQuestions[this.currentIndex].correctAnswer ===
          this.currentAnswer
      ) {
        this.quizQuestions[this.currentIndex].isCorrect = true
        this.score++
      } else {
        this.quizQuestions[this.currentIndex].isCorrect = false
      }
    },
    startNewQuiz() {
      this.step = 1
      this.currentIndex = 0
      this.quizQuestions = []
      this.shuffleMode = true
      this.numberOfQuestions = null
      this.currentAnswer = null
      this.score = 0
    },
    onTimerChanged(timer) {
      this.timer = timer
    },
  },
}
</script>
