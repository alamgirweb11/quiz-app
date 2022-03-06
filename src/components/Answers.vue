<template lang="">
    <div class="result">
        <div class="title"> {{ results[answerIndex].title }}</div>
        <div class="desc">
              {{ results[answerIndex].desc }}
        </div>
    </div>
</template>
<script>
export default {
     name:  'AnswersComponent',
     props: ['results', 'totalCorrect'],
     computed:{
           answerIndex(){
                 let index = 0;
                this.results.forEach((e, i) => {
                      if(e.min <= this.totalCorrect && e.max >= this.totalCorrect){
                            index = i;
                      }
                });

                return index;
           }
     }
}
</script>
<style lang="">
    
</style>