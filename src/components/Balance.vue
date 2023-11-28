<template>
    <div>
        <h4>Your Balance</h4>
        <h1 id="balance">${{ balance }}</h1>
    </div>
</template>


<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    balance: {
        type: Number,
        required: true
    }
})
</script>


