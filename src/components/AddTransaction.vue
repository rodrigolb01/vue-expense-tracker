<template>
    <div>
        <h3>Add Transaction</h3>
        <form action="">
            <div class="form-control">
                <label for="text">Text</label>
                <input type="text" id="text" placeholder="description">
            </div>
            <div class="form-control">
                <label for="amount">Amount (negative - expense, positive - income)</label>
                <input type="number" id="amount" placeholder="$0.00">
            </div>
            <button class="btn">Ok</button>
        </form>
    </div>
</template>