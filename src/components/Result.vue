<template>
  <div class="result">
    <div class="title">{{ results[resultIndex].title }}</div>
    <div class="desc">
      {{ results[resultIndex].desc }}
    </div>
    <div class="desc" v-if="showScore">
      you got {{ correctAnswers }} / {{ questions.length }}
    </div>
  </div>
</template>

<script>
export default {
  props: ["correctAnswers", "results", "questions"],
  computed: {
    resultIndex() {
      let index = 0;
      this.results.forEach((e, i) => {
        if (e.min <= this.correctAnswers && e.max >= this.correctAnswers) {
          index = i;
        }
      });
      return index;
    },
    showScore() {
      if (this.correctAnswers < this.questions.length) {
        return true;
      } else {
        return false;
      }
    },
  },
};
</script>
