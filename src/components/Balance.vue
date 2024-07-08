<template>
<div>
<h3>Your Balance</h3>
<h1>{{ balance | currency}}</h1>
</div>
</template>

<script>
export default {
    props: ['balance'],
    filters: {
        currency(value) {
            return `$${value.toFixed(2)}`;
        }
    }
}
</script>

<style scoped>
h1 {
    margin: 0;
    font-size: 2rem;
    color: #000;
}
h3 {
    color: #000;
}
</style>
