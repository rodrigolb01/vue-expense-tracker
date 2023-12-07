<script setup>
import Header from './components/Header.vue'
import Balance from './components/Balance.vue'
import IncomeExpense from './components/IncomeExpense.vue'
import TransactionList from './components/TransactionList.vue'
import AddTransaction from './components/AddTransaction.vue'
import { ref } from 'vue'
import { computed } from '@vue/reactivity'
import { useToast } from 'vue-toastification'

var transactions = ref([]);

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

const handleTransactionSubmitted = (transactionData) => {
  transactions.value.push({
    id : generateUniqueId(),
    text : transactionData.text,
    amount : transactionData.amount
  });

  const toast = useToast();

  toast.success("Expense added");
}

const generateUniqueId = () => {
  return Math.floor(Math.random() *  1000000);
}

const handleOnDeleteTransaction = (id) => {
    transactions.value = transactions.value.filter(
      (transaction) => transaction.id != id
    );
}

</script>

<template>
  <div class="container">
    <Header />
    <div class="container">
      <Balance :balance="+balance" />
      <IncomeExpense :income="+income" :expense="+expense"/>
      <TransactionList @deleteTransaction="handleOnDeleteTransaction" :transactions="transactions" />
      <AddTransaction  @transactionSubmitted="handleTransactionSubmitted"/>
    </div>
  </div>
</template>