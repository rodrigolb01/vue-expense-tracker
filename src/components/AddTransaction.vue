<template>
    <div>
        <h3>Add Transaction</h3>
        <form id="form" @submit.prevent="onSubmit">
            <div class="form-control">
                <label for="text">Text</label>
                <input type="text" id="text" v-model="text" placeholder="description" >
            </div>
            <div class="form-control">
                <label for="amount">Amount (negative - expense, positive - income)</label>
                <input type="text" id="amount" v-model="amount" placeholder="$0.00">
            </div>
            <button class="btn">Ok</button>
        </form>
    </div>
</template>

<script setup>

import { ref } from 'vue';
import { useToast } from 'vue-toastification';

const text = ref('');
const amount = ref('');

const emit = defineEmits(['transactionSubmitted'])

const toast = useToast();

const onSubmit = () => {
    if((!text || text.value == '') || (!amount || amount.value == ''))
    {
        toast("Both fields must be filled");
        return;
    }

    const transactionData = {
        text: text.value,
        amount: parseFloat(amount.value)
    }

    emit('transactionSubmitted', transactionData);

    text.value = '';
    amount.value = '';
}
</script>