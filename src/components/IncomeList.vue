<template>
  <div class="mt-4 px-4 py-2">
    <IncomeItem
      @remove-item="removeItem"
      v-for="data in state.sortedIncome"
      :key="data.id"
      :income="data"
    />
  </div>
</template>

<script>
import IncomeItem from "./IncomeItem.vue";
export default {
  props: {
    state: Object,
  },
  components: {
    IncomeItem,
  },
  setup(props, { emit }) {
    function removeItem(id) {
      emit("remove-item", id);
    }
    return {
      removeItem,
    };
  },
};
</script>

<style></style>
