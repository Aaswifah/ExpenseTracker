<template>
<div id="app">
<h2>Expense Tracker</h2>
<Balance :balance="balance" />
<IncomeExpense :income="income" :expense="expense" />
<TransactionList :transactions="transactions" />
<AddTransaction @add-transaction="addTransaction" />
</div>
</template>

<script>
import Balance from './components/Balance.vue';
import IncomeExpense from './components/IncomeExpense.vue';
import TransactionList from './components/TransactionList.vue';
import AddTransaction from './components/AddTransaction.vue';

export default {
  components: {
    Balance,
    IncomeExpense,
    TransactionList,
    AddTransaction
  },
  data() {
    return {
      transactions: [
        { id: 1, text: 'Sneakers', amount: -200 },
        { id: 2, text: 'Work', amount: 500 },
        { id: 3, text: 'Food', amount: -132.29},
        { id: 4, text: 'Stream Donations', amount: 75 },
        { id: 5, text: 'Movie Rental', amount: -19.99 }
      ]
    }
  },
  computed: {
    balance() {
      return this.transactions.reduce((acc, item) => (acc += item.amount), 0).toFixed(2);
    },
    income() {
      return this.transactions
      .filter(item => item.amount > 0)
      .reduce((acc, item) => (acc += item.amount), 0)
      .toFixed(2);
    },
    expense() {
      return (
        this.transactions
        .filter(item => item.amount <0)
        .reduce((acc, item) => (acc += item.amount), 0) * -1
      ).toFixed(2);
    }
  },
  methods: {
    addTransaction(transaction) {
      this.transactions.push(transaction);
    }
  }
}
</script>

<style>
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.6;
  background: #fff;
  margin: 0;
  padding: 0;
  background: rgb(63,94,251);
  background: radial-gradient(circle, rgba(63,94,251,1) 0%, rgba(252,70,107,1) 100%);
}

#app {
  max-width: 360px;
  margin: 30px auto;
  padding: 30px;
  background: #fff;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  border-radius: 5px;
}

h2 {
  margin: 0 0 20px;
  text-align: center;
  color: #000;
}

form {
  margin: 20px 0;
}

.form-control {
  margin-bottom: 10px;
}

.form-control label {
  display: block;
}

.form-control input[type='text'],
.form-control input[type='number'] {
  width: 100%;
  padding: 10px;
  margin-top: 5px;
  border: 1px solid #ddd;
  border-radius: 5px;
}

.btn {
  display: block;
  width: 100%;
  padding: 10px;
  color: #fff;
  background: #333;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.btn:hover {
  background: #555;
}

.inc-exp-container {
  display: flex;
  justify-content: space-between;
  margin: 20px 0;
}

.inc-exp-container div {
  flex: 1;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 5px;
  background: #f9f9f9;
  text-align: center;
}

.inc-exp-container .money {
  font-size: 20px;
  letter-spacing: 1px;
}

.inc-exp-container .money.plus {
  color: #2ecc71;
}

.inc-exp-container .money.minus {
  color: #c0392b;
}

.list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.list li {
  background: #f4f4f4;
  color: #333;
  display: flex;
  justify-content: space-between;
  padding: 10px;
  border-left: 5px solid;
  border-radius: 5px;
  margin: 10px 0;
}

.list li.plus {
  border-color: #2ecc71;
}

.list li.minus {
  border-color: #c0392b;
}
</style>
