<template>
  <div class="areatransaction">
    <h3>Adicionar nova transação</h3>
    <form id="form" @submit.prevent="onSubmit">
      <div class="form-control">
        <label for="type">Tipo de transação:</label>
        <div class="type">
          <input type="radio" name="type" value="expense" v-model="type" />
          Despesa
        </div>
        <div class="type">
          <input type="radio" name="type" value="income" v-model="type" /> Renda
        </div>
      </div>
      <div class="form-control">
        <label for="text">Texto: </label>
        <input
          type="text"
          id="text"
          placeholder="Digite o texto"
          v-model="text"
        />
      </div>
      <div class="form-control">
        <label for="amount">Valor: </label>
        <input
          type="text"
          id="amount"
          placeholder="Digite o valor"
          v-model="amount"
        />
      </div>

      <button class="btn">Adicionar transação</button>
    </form>
  </div>
</template>

<script setup>
import { useToast } from "vue-toastification";
import { ref } from "vue";

const text = ref("");
const amount = ref("");
const type = ref("");

const toast = useToast();

const emit = defineEmits(["transactionSubmitted"]);

const onSubmit = () => {
  if (!text.value || !amount.value || !type) {
    toast.error("Os campos precisam ser preenchidos");
    return;
  }
  if (type.value == "expense") {
    amount.value = "-" + amount.value;
  }

  const transactionData = {
    text: text.value,
    amount: parseFloat(amount.value.replace(".", "").replace(",", ".")),
  };

  emit("transactionSubmitted", transactionData);

  text.value = "";
  amount.value = "";
  type.value = "";
};
</script>
