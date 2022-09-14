<template>
  <div
    class="grid grid-cols-12 text-lg bg-white rounded-md px-4 py-2 mx-auto mt-4 w-2/5 shadow-sm"
  >
    <div @click="removeItem" class="text-red-500 font-bold cursor-pointer">
      x
    </div>
    <div class="col-span-7 font-semibold">{{ income.desc }}</div>
    <div class="col-span-2 font-semibold">${{ income.value }}</div>
    <div class="col-span-2 font-semibold">{{ formatDate }}</div>
  </div>
</template>

<script>
export default {
  props: {
    income: Object,
  },
  setup(props, { emit }) {
    let date = new Date(props.income.date);
    let day = date.getDate();
    let month = date.getMonth();
    let year = date.getFullYear();

    let formatDate = day + "/" + month + "/" + year;

    function removeItem() {
      emit("remove-item", props.income.id);
    }
    return {
      formatDate,
      removeItem,
    };
  },
};
</script>
