<template>
    <div class="inc-exp-container">
        <div>
            <h4>Income</h4>
            <h1 id="money-plus" class="money plus">${{income}}</h1>
        </div>
        <div>
            <h4>Expense</h4>
            <h1 id="money-minus" class="money minus">${{expense}}</h1>
        </div>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    income : {
        type : Number,
        required : true
    },
    expense : {
        type : Number,
        required : true
    }
})
</script>