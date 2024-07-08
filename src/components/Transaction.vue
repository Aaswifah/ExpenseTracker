<template>
<li :class="{ minus: transaction.amount < 0, plus: transaction.amount > 0}">
{{ transaction.text }} <span>{{ transaction.amount | currency }}</span>
</li>
</template>

<script>
export default {
    props: ['transaction'],
    filters: {
        currency(value) {
            return `$${value.toFixed(2)}`;
        }
    }
}
</script>

<style scoped>
.minus {
    color: red;
}

.plus {
    color: green;
}
</style>
