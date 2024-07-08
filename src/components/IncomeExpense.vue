<template>
<div class="inc-exp-container">
<div>
<h4>Income</h4>
<p class="money plus">{{ income | currency}}</p>
</div>

<div>
<h4>Expense</h4>
<p class="money minus">{{ expense | currency }}</p>
</div>

</div>
</template>

<script>
export default {
    props: ['income', 'expense'],
    filters: {
        currency(value) {
            return `$${value.toFixed(2)}`;
        }
    }
}
</script>

<style scoped>
.inc-exp-container div {
    margin: 0 5px;
    background: #fff;
}

.money.plus {
    color: #2ecc71;
}

.money.minus {
    color: #c0392b;
}
h4 {
    color: #000;
}
</style>
