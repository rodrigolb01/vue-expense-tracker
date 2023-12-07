<script setup>
import Transaction from './Transaction.vue'
import { defineProps } from 'vue';

const props = defineProps({
    transactions: {
        type: Array,
        required: true
    }
})

const emit = defineEmits(['deleteTransaction']);

const handleOnDeleteTransaction = (id) => {
    emit('deleteTransaction', id)
}

</script>

<template>
    <div>
        <ul id="list" class="list">
            <li v-for="transaction in transactions" :key="transactions.id"
                :class="transaction.amount < 0 ? 'minus' : 'plus'">
                <Transaction @deleteTransaction="handleOnDeleteTransaction" :id="transaction.id" :text="transaction.text" :amount="transaction.amount" />
            </li>
        </ul>
    </div>
</template>