<template>
  <div class="game">
    <div class="gameOver" v-if="config.gameOver">
        <h1>Game is over</h1>
        <h1>{{ config.currentScore }}</h1>
    </div>
    <div class="gameComing" v-else>
        <div class="questions" v-if="config.answering">
            <h1 class="questions-title">{{ questions[config.currentQuestion].title }}</h1>
            <ul>
                <li @click="questionToAnswer(index, questions[config.currentQuestion].answer)" :key="index" v-for="(option, index) in questions[config.currentQuestion].options">
                    {{ option }}
                </li>
            </ul>
        </div>
        <div class="answers" v-else>
            <div class="wrong" v-if="config.currentJudge">
                答錯了哭哭
            </div>
            <div class="correct" v-else>
                答對了棒棒
            </div>
            <button @click="answerToQuestion()">下一題</button>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Game',
  data () {
    return {
      config: {
        totalQuestion: 10,
        currentQuestion: 0,
        totalScore: 100,
        currentScore: 0,
        currentJudge: true,
        answering: true,
        gameOver: false
      },
      questions: [
          {
              title: '第1題：哪個縣市的地方首長，曾擔任超過10年，創下連任最長紀錄？',
              options: ['宜蘭市', '台中市', '苗栗縣', '澎湖縣'],
              answer: 1,
              id: 'id001'
          },
          {
              title: '第2題：哪個縣市的地方首長，曾擔任超過10年，創下連任最長紀錄？',
              options: ['宜蘭市', '台中市', '苗栗縣', '澎湖縣'],
              answer: 3,
              id: 'id002'
          },
          {
              title: '第3題：哪個縣市的地方首長，曾擔任超過10年，創下連任最長紀錄？',
              options: ['宜蘭市', '台中市', '苗栗縣', '澎湖縣'],
              answer: 4,
              id: 'id003'
          },
          {
              title: '第4題：哪個縣市的地方首長，曾擔任超過10年，創下連任最長紀錄？',
              options: ['宜蘭市', '台中市', '苗栗縣', '澎湖縣'],
              answer: 2,
              id: 'id004'
          },
          {
              title: '第5題：哪個縣市的地方首長，曾擔任超過10年，創下連任最長紀錄？',
              options: ['宜蘭市', '台中市', '苗栗縣', '澎湖縣'],
              answer: 4,
              id: 'id005'
          },
          {
              title: '第6題：哪個縣市的地方首長，曾擔任超過10年，創下連任最長紀錄？',
              options: ['宜蘭市', '台中市', '苗栗縣', '澎湖縣'],
              answer: 2,
              id: 'id006'
          },
          {
              title: '第7題：哪個縣市的地方首長，曾擔任超過10年，創下連任最長紀錄？',
              options: ['宜蘭市', '台中市', '苗栗縣', '澎湖縣'],
              answer: 1,
              id: 'id007'
          },
          {
              title: '第8題：哪個縣市的地方首長，曾擔任超過10年，創下連任最長紀錄？',
              options: ['宜蘭市', '台中市', '苗栗縣', '澎湖縣'],
              answer: 3,
              id: 'id008'
          },
          {
              title: '第9題：哪個縣市的地方首長，曾擔任超過10年，創下連任最長紀錄？',
              options: ['宜蘭市', '台中市', '苗栗縣', '澎湖縣'],
              answer: 3,
              id: 'id009'
          },
          {
              title: '第10題：哪個縣市的地方首長，曾擔任超過10年，創下連任最長紀錄？',
              options: ['宜蘭市', '台中市', '苗栗縣', '澎湖縣'],
              answer: 2,
              id: 'id010'
          }
      ],
      answers: {
          'id001': 1,
          'id002': 3,
          'id003': 4,
          'id004': 2,
          'id005': 4,
          'id006': 2,
          'id007': 1,
          'id008': 3,
          'id009': 3,
          'id010': 2
      }
    }
  },
  methods:  {
      questionToAnswer (option, answer) {
        
          this.checkAnswer(option, answer)
          this.config.answering = false
          
      },
      answerToQuestion () {
          console.log("hello")
          if(this.config.currentQuestion + 1 < this.config.totalQuestion) {
              this.config.currentQuestion++
          } else {
              this.config.currentQuestion = 0
              this.config.gameOver = true
          }
          this.config.answering = true
      },
      checkAnswer(option, answer) {

          if ( option + 1 === answer ) {
              this.config.currentScore += 20
              this.config.currentJudge = true
          } else {
              this.config.currentJudge = false
          }
          
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.game {
  
}
</style>
