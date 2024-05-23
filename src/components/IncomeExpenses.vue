<template>
  <div class="inc-exp-container">
    <div class="income-expense-box">
      <h4>Renda</h4>
      <p id="money-plus" class="money plus">
        R$ {{ income.toLocaleString("pt-br", { minimumFractionDigits: 2 }) }}
      </p>
    </div>
    <div class="income-expense-box">
      <h4>Despesa</h4>
      <p id="money-minus" class="money minus">
        R$ {{ expenses.toLocaleString("pt-br", { minimumFractionDigits: 2 }) }}
      </p>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  income: {
    type: Number,
    required: true,
  },
  expenses: {
    type: Number,
    required: true,
  },
});
</script>
