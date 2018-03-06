<template>
  <div>
    
    <Addoperation v-on:action1="op => addop(op)"/>
    <h1 class="title text-center">list of operations</h1>
    <Operations :operations="operations" v-on:action2="op => deletop(op)"/>
    
    <div class="totals">
      <table class="table">
          <thead class="thead-dark">
              <th scope="col">Total Credit</th>
              <th scope="col">Total Debit</th>
              <th scope="col">Total</th>             
          </thead>
          <tbody>
          <tr> 
              <td>+{{getTotal()[1]}}€</td> 
              <td>-{{getTotal()[2]}}€</td> 
              <td> {{getTotal()[0]}}€</td>        
          </tr>
          </tbody>
      </table>
    </div>

  </div>
</template>

<script>
import Operations from './Operations.vue';
import Addoperation from './Addoperation.vue';

export default {
  name: 'bankmanager',
  components: {
      Operations,
      Addoperation
  },
  data: function () {
    return {
      operations: [
        {'id': 0, 'type': 'credit', 'category': 'salary', 'title': 'salary', 'date': '01/02/2018', 'amount': 2000},
        {'id': 1, 'type': 'debit', 'category': 'housing', 'title': 'monthly rent', 'date': '03/02/2018', 'amount': 400},
        {'id': 2, 'type': 'debit', 'category': 'alimentary', 'title': 'grocery shopping', 'date': '04/02/2018', 'amount': 100},
      ],
    };
  },
  methods: {
        addop(op) {
            op.id = this.operations.length;
            this.operations.push(op);
        },
        deletop(op) {
            this.operations.splice(this.operations.indexOf(op), 1);
        },
        getTotal() {
        let total = [0, 0, 0];
        this.operations.forEach(op => {
            if (op.type === 'credit') {
                total[0] += op.amount;
                total[1] += op.amount;
            } else {
                total[0] -= op.amount;
                total[2] += op.amount;
            }
        });
          return total;
      }
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
