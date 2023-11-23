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
            <!-- <li class="plus">
                <span>Paycheck $100</span>
                <button class="delete-btn">x</button>
            </li>
            <li class="minus">
                <span>Lunch $8</span>
                <button class="delete-btn">x</button>
            </li>
            <li class="minus">
                <span>Pharmacy $5</span>
                <button class="delete-btn">x</button>
            </li>
            <li class="minus">
                <span>Shopping $23</span>
                <button class="delete-btn">x</button>
            </li> -->
        </ul>
    </div>
</template>

<script>
export default {
    setup() {
        const transactions = [
            { id: 1, text: "Paycheck", amount: 100 },
            { id: 2, text: "Lunch", amount: -7 },
            { id: 3, text: "Pharmacy", amount: -5 },
            { id: 4, text: "Shopping", amount: -23 }
        ];

        return {
            transactions
        }
    }
}
</script>