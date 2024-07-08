<template>
<div>
<h3>History</h3>
<ul id="list" class="list">
<Transaction v-for="transaction in transactions" :key="transaction.id" :transaction="transaction" />
</ul>
</div>
</template>

<script>
import Transaction from './Transaction.vue';

export default {
    props: ['transactions'],
    components: {
        Transaction
    }
}
</script>

<style scoped>
.list {
    margin: 0;
    padding: 0;
    list-style: none;
}
h3 {
    color: #000;
}
</style>
