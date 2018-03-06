<template>
    <table class="table">
        <thead class="thead-dark">
            <th scope="col">id</th>
            <th scope="col">type</th>
            <th scope="col">category</th>
            <th scope="col">title</th> 
            <th scope="col">date</th> 
            <th scope="col">amount</th>             
            <th scope="col">ops</th>     
        </thead>
        <tbody>
        <tr v-for="op of operations" :key="op.id"> 
            <td>{{op.id}}</td>
            <td>{{op.type}}</td>  
            <td>{{op.category}}</td>  
            <td>{{op.title}}</td> 
            <td>{{op.date}}</td> 
            <td>
                <i v-if="op.type == 'debit'">-</i> 
                <i v-else>+</i>                 
                {{op.amount}}€
            </td> 
            <button @click="action2(op)">delete</button>           
        </tr>
        </tbody>
    </table>
</template>

<script>

export default {
    name: 'operations',
    props: {
      operations: {
          type:Array,
          required: true
      }
    },
    data: function() {
        return {
            total: 0, 
        }
    },
    methods: {
      action2(op) { 
          this.$emit('action2', op);
      },
    }
}
</script>

<style>

</style>
