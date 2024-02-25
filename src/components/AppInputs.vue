<script lang="ts">
export default {
  name: "AppInputs",
  data() {
    return {
      Mbps: null,
      MHz: null,
      result: 0,
      resultBox: 'Enter values'
    };
  },
  methods: {
    onUserInput() {
      if (this.Mbps === null || this.MHz === null) {
        this.result = 0;
      } else {
        this.result = this.Mbps / this.MHz;
      }
      this.updateResultBox();
    },
    updateResultBox() {
      if (this.result === 0 || isNaN(this.result)) {
        this.resultBox = 'Impossible Value';
        return;
      }
      this.resultBox = this.result.toString() + "bits / Hz";
    }
  }
}
</script>

<template>
  <div class="max-w-lg mx-auto mt-10">
    <h1 class="text-3xl font-bold mb-4 text-center">Bits/Hz Calculator</h1>

    <div class="rounded-lg border border-gray-300 px-4 py-2 mb-4 text-center">
      <h2 class="text-1xl font-bold">{{ resultBox }}</h2>
    </div>

    <div class="flex justify-between">
      <input type="number" placeholder="Mbps" v-model="Mbps" @keyup="onUserInput" @change="onUserInput" min="0"
             class="border border-gray-300 rounded-l-md px-3 py-2 mb-2 focus:outline-none focus:border-blue-500 w-full" />
      <span class="px-3 py-2 mb-2 border border-gray-300 rounded-r-md">Mbps</span>
    </div>
    <div class="flex justify-between">
      <input type="number" placeholder="MHz" v-model="MHz" @keyup="onUserInput" @change="onUserInput" min="0"
             class="border border-gray-300 rounded-l-md px-3 py-2 mb-2 focus:outline-none focus:border-blue-500 w-full" />
      <span class="px-3 py-2 mb-2 border border-gray-300 rounded-r-md">MHz</span>
    </div>
  </div>
</template>


<style scoped>

</style>
