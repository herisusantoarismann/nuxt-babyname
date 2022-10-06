<template>
  <v-card
    class="mt-16 mx-auto px-6 py-4 d-flex flex-column justify-center align-center"
    max-width="500"
    outlined
    elevation="3"
  >
    <h1>Baby Name Generator</h1>
    <p class="font-weight-medium my-2">
      Choose your options and click the "Find Names" button below.
    </p>
    <div class="text-center my-4">
      <p>Choose a gender</p>
      <v-btn-toggle v-model="gender" color="indigo" class="mt-2" group rounded>
        <v-btn value="boy">Boy</v-btn>
        <v-btn value="neutral">Neutral</v-btn>
        <v-btn value="girl">Girl</v-btn>
      </v-btn-toggle>
    </div>
    <v-btn color="indigo" @click="onSubmit">Find Names</v-btn>
  </v-card>
  <v-card
    class="mx-auto mt-2 py-4 d-flex flex-wrap"
    max-width="500"
    elevation="0"
  >
    <v-btn
      class="mx-2 mt-2 text-white"
      color="cyan"
      v-for="result in results"
      :key="result"
      >{{ result }}</v-btn
    >
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      gender: "boy",
      results: [],
    };
  },
  methods: {
    onSubmit() {
      fetch("https://api.api-ninjas.com/v1/babynames?gender=" + this.gender, {
        headers: {
          "X-Api-Key": "1Mw5F/MUNe6DGcwfQCXplA==BMtEmZS9QnbKXsiA",
          "content-type": "application/json",
        },
      })
        .then((res) => res.json())
        .then((res) => (this.results = res));
    },
  },
};
</script>
