<template>
<div>
<h3>Add new transaction</h3>
<form @submit.prevent="onSubmit">
<div class="form-control">
<label for="text">Text</label>
<input type="text" v-model="text" placeholder="Enter text" />
</div>

<div class="form-control">
<label for="amount">Amount <br />(negative - expense, positive - income)</label>
<input type="number" v-model="amount" placeholder="Enter amount" />
</div>

<button class="btn">Add transaction</button>

</form>
</div>
</template>

<script>
export default {
    data() {
        return {
            text: '',
            amount: null
        }
    },
    methods: {
        onSubmit() {
            if (!this.text || !this.amount) {
                alert("Please add text and amount");
                return;
            }

            const newTransaction = {
                id: Math.floor(Math.random() * 100000000),
                text: this.text,
                amount: +this.amount
            };

            this.$emit('add-transaction', newTransaction);

            this.text = '';
            this.amount = null;
        }
    }
}
</script>

<style scoped>
.form-control {
    margin-bottom: 10px;
}

.form-control label {
    display: block;
    color: #000;
}

.form-control input[type='text'],
.form-control input[type='number'] {
    width: 100%;
    padding: 10px;
    margin-top: 5px;
    border: 1px solid #000;
    border-radius: 5px;
    background: #fff;
}

.btn {
    display: block;
    width: 100%;
    padding: 10px;
    color: #fff;
    background: #000;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

.btn:hover {
    background: #555;
}
h3 {
    color: #000;
}
</style>
