<template>
  <Header :totalIncome="state.totalIncome" />
  <Form @add-income="AddIncome" />
  <IncomeList :state="state" @remove-item="removeItem" />
</template>

<script>
import { reactive, computed } from "vue";
import Header from "./components/Header.vue";
import Form from "./components/Form.vue";
import IncomeList from "./components/IncomeList.vue";

export default {
  setup() {
    const state = reactive({
      income: [],
      totalIncome: computed(() => {
        let temp = 0;

        if (state.income.length > 0) {
          for (let i = 0; i < state.income.length; i++) {
            temp += state.income[i].value;
          }
        }
        return temp;
      }),

      sortedIncome: computed(() => {
        let temp = [];

        temp = state.income.sort((a, b) => b.date - a.date);

        return temp;
      }),
    });
    function AddIncome(data) {
      let d = data.date.split("-");
      let newD = new Date(d[0], d[1], d[2]);
      state.income = [
        ...state.income,
        {
          id: Date.now(),
          desc: data.desc,
          value: data.value,
          date: newD.getTime(),
        },
      ];
    }

    function removeItem(id) {
      state.income = state.income.filter((e) => e.id != id);
    }
    return {
      state,
      AddIncome,
      removeItem,
    };
  },
  components: {
    Header,
    Form,
    IncomeList,
  },
};
</script>

<style>
body {
  background: rgba(128, 128, 128, 0.66);
}
</style>
