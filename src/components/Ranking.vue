<template>
  <h1>Your best scores</h1>
  <ul>
    <li v-for="(score, index) in sortedScores" :key="score">
      {{ index + 1 }}º - <span>{{ score }} ms</span>
    </li>
  </ul>
</template>

<script>
export default {
  name: "Ranking",
  props: ["scoreArray"],

  computed: {
    sortedScores() {
      return this.scoreArray.sort((a, b) => a - b);
    },
  },
};
</script>

<style scoped>
h1 {
  margin-top: 2em;
}

li {
  list-style: none;
  margin-top: 1em;
  font-size: 1.2rem;
  text-align: center;
}

span {
  color: #0faf87;
}
</style>