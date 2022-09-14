<template>
  <header
    class="bg-gray-900 border border-b-8 border-b-yellow-600 px-6 py-4 flex justify-between items-center"
  >
    <h1 class="text-3xl font-bold text-white">Income Tracker</h1>
    <div
      class="bg-yellow-500 min-w-max text-2xl rounded-md shadow px-6 py-2 font-bold text-white italic"
    >
      ${{ totalIncome }}
    </div>
  </header>
</template>

<script>
export default {
  props: {
    totalIncome: Number,
  },
};
</script>

<style></style>
