<script>
import Header from './components/Header.vue'
import Balance from './components/Balance.vue'
import IncomeExpense from './components/IncomeExpense.vue'
import TransactionList from './components/TransactionList.vue'
import AddTransaction from './components/AddTransaction.vue'

export default {
  components: {
    Balance,
    Header,
    IncomeExpense,
    TransactionList,
    AddTransaction
  }
}

</script>

<template>
  <div class="container">
    <Header />
    <div class="container">
      <Balance />
      <IncomeExpense />
      <TransactionList />
      <AddTransaction/>
    </div>
  </div>
</template>