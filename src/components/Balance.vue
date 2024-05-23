<template>
  <div class="areatransaction">
    <h4>Balanço</h4>
    <h1 id="balance">
      R$
      {{
        total.toLocaleString("pt-br", {
          minimumFractionDigits: 2,
        })
      }}
    </h1>
  </div>
</template>

<script setup>
const props = defineProps({
  total: {
    type: Number,
    required: true,
  },
});
</script>
