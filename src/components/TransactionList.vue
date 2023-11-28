<template>
    <div>
        <ul id="list" class="list">
            <li v-for="transaction in transactions" :key="transactions.id"
                :class="transaction.amount < 0 ? 'minus' : 'plus'">
                >
                <span>
                    {{ transaction.text }}
                    {{ transaction.amount }}
                </span>
                <button class="delete-btn">x</button>
            </li>
        </ul>
    </div>
</template>

<script setup>

import { defineProps } from 'vue';

const props = defineProps({
    transactions : {
        type : Array,
        required : true
    }
})

</script>