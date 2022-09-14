<template>
  <div class="mt-8 mx-auto w-3/5 text-center">
    <form
      @submit.prevent="formHandler"
      class="flex items-center justify-center"
    >
      <input
        v-model="formData.desc"
        class="bg-white focus:outline-none font-semibold text-gray-700 rounded-l-md h-12 px-4 py-2"
        required
        type="text"
        placeholder="Description..."
      />
      <input
        v-model="formData.value"
        class="bg-white focus:outline-none font-semibold text-gray-700 h-12 px-4 py-2"
        required
        type="number"
        placeholder="Income amount..."
      />
      <input
        v-model="formData.date"
        class="bg-white focus:outline-none font-semibold text-gray-700 h-12 px-4 py-2"
        required
        type="date"
      />
      <input
        class="cursor-pointer hover:bg-yellow-600 h-12 px-4 py-2 bg-yellow-500 rounded-r-md font-bold text-white"
        type="submit"
        value="SUBMIT"
      />
    </form>
  </div>
</template>

<script>
import { reactive } from "vue";
export default {
  props: {
    state: Object,
  },
  setup(props, { emit }) {
    const formData = reactive({
      desc: null,
      value: null,
      date: null,
    });

    function formHandler() {
      emit("add-income", {
        desc: formData.desc,
        value: formData.value,
        date: formData.date,
      });

      formData.desc = null;
      formData.value = null;
      formData.date = null;
    }

    return {
      formHandler,
      formData,
    };
  },
};
</script>
