<template>
<div class="ctr">
  <questions v-if="questionsAnswered < questions.length"
   :questions="questions"
   :questionsAnswered="questionsAnswered"
   @question-answered="questionAnswered"
   ></questions>
  <answers v-else
  :results="results"
  :totalCorrect="totalCorrect"
  ></answers>
    <button type="button" class="reset-btn"
    @click.prevent="resetQuestions()"
    v-if="questionsAnswered === questions.length"
    >Reset</button>
</div>
</template>

<script>
import Questions from '@/components/Questions';
import Answers from '@/components/Answers';
export default {
  name: 'App',
  data(){
     return{
       questionsAnswered: 0,
       totalCorrect: 0,
        questions: [
        {
            q: 'What is 2 + 2?', 
            answers: [
                {
                    text: '4',
                    is_correct: true
                },
                {
                    text: '3',
                    is_correct: false 
                },
                {
                    text: '8',
                    is_correct: false 
                },
                {
                    text: '5',
                    is_correct: false 
                }
            ] 
        },
        { 
            q: 'How many letters are in the word "Banana"?', 
            answers: [
                {
                    text: '5',
                    is_correct: false
                },
                {
                    text: '7',
                    is_correct: false 
                },
                {
                    text: '6',
                    is_correct: true 
                },
                {
                    text: '12',
                    is_correct: false 
                }
            ] 
        },
        { 
            q: 'Find the missing letter: C_ke', 
            answers: [
                {
                    text: 'e',
                    is_correct: false
                },
                {
                    text: 'a',
                    is_correct: true 
                },
                {
                    text: 'i',
                    is_correct: false 
                },
                {
                    text: 'n',
                    is_correct: false 
                }
            ] 
        },
        { 
            q: 'Find the missing letter: Tig_r', 
            answers: [
                {
                    text: 'f',
                    is_correct: false
                },
                {
                    text: 'a',
                    is_correct: false 
                },
                {
                    text: 'e',
                    is_correct: true 
                },
                {
                    text: 'n',
                    is_correct: false 
                }
            ] 
        },
        {
            q: 'What is 10 - 5?', 
            answers: [
                {
                    text: '4',
                    is_correct: false
                },
                {
                    text: '3',
                    is_correct: false 
                },
                {
                    text: '8',
                    is_correct: false 
                },
                {
                    text: '5',
                    is_correct: true 
                }
            ] 
        },
    ],
    results: [
        {
            min: 0,
            max: 3,
            title: "Try again!",
            desc: "Do a little more studying and you may succeed!"
        },
        {
            min: 5,
            max: 5,
            title: "Wow, you're a genius!",
            desc: "Studying has definitely paid off for you!"
        }
    ]
     }
  },
  methods: {
      questionAnswered(is_correct){
           if(is_correct){
               this.totalCorrect++
           }
           this.questionsAnswered++
      },
      resetQuestions(){
              this.questionsAnswered = 0;
              this.totalCorrect = 0;
      }
  },
  components: {
      Questions,
      Answers
  }
}
</script>

<style>

</style>
