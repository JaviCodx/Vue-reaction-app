<template>
  <h2>Your reaction time was</h2>
  <h3>{{ reactionTime }} ms</h3>
  <p>{{ rank }}</p>
</template>

<script>
export default {
  name: "Results",
  props: ["reactionTime"],
  data() {
    return {
      rank: null,
    };
  },

  mounted() {
    if (this.reactionTime < 250) {
      this.rank = "That was really fast";
    } else if (this.reactionTime < 400) {
      this.rank = "Not great, not terrible";
    } else {
      this.rank = "You better check those reflexes";
    }
  },
};
</script>

<style>
h3 {
  font-size: 2rem;
  color: #0faf87;
}
p {
  font-size: 1.5rem;
  font-style: italic;
  font-weight: bold;
}
</style>