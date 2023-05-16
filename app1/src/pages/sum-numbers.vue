<template>
  <q-page>
    <div class="q-pa-md">
      <h2 class="text-h6">Enter two numbers to sum:</h2>
      <q-input v-model="number1" type="number" label="Number 1"></q-input>
      <q-input v-model="number2" type="number" label="Number 2"></q-input>
      <q-btn label="Calculate" @click="sumNumbers" color="primary"></q-btn>
      <h2 class="text-h6">Result : {{ result }}</h2>
    </div>
  </q-page>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      number1: 0,
      number2: 0,
      result: 0,
    };
  },
  methods: {
    sumNumbers() {
      axios
        .post('http://localhost:3000/sum', {
          number1: parseInt(this.number1),
          number2: parseInt(this.number2),
        })
        .then((response) => {
          this.result = response.data.result;
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },
};
</script>
