<template>
    <div>
        <span>
            {{ text }}
            ${{ amount }}
        </span>
        <button class="delete-btn" @click="onDelete">x</button>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';

const emit = defineEmits(['deleteTransaction']);

const props = defineProps({
    id : {
        type : Number,
        required : true
    },
    text : {
        type : String,
        required : true
    },
    amount : {
        type : Number,
        required : true
    }
})

const onDelete = () => {
    emit('deleteTransaction', props.id)
}
</script>