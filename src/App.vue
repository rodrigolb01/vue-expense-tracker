<script setup>
import Header from './components/Header.vue'
import Balance from './components/Balance.vue'
import IncomeExpense from './components/IncomeExpense.vue'
import TransactionList from './components/TransactionList.vue'
import AddTransaction from './components/AddTransaction.vue'
import { ref } from 'vue'
import { computed } from '@vue/reactivity'

const transactions = ref([
  { id: 1, text: "Paycheck", amount: 100 },
  { id: 2, text: "Lunch", amount: -7 },
  { id: 3, text: "Pharmacy", amount: -5 },
  { id: 4, text: "Shopping", amount: -23 }
]);

const balance = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0)
});

const income = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return transaction.amount > 0 ? acc + transaction.amount : acc + 0;
  }, 0).toFixed(2);
})

const expense = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return transaction.amount < 0 ? acc + transaction.amount : acc + 0;
  }, 0).toFixed(2);
})

</script>

<template>
  <div class="container">
    <Header />
    <div class="container">
      <Balance :balance="balance" />
      <IncomeExpense :income="income" :expense="expense"/>
      <TransactionList :transactions="transactions" />
      <AddTransaction />
    </div>
  </div>
</template>