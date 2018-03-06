<template>
    <form v-on:submit.prevent="action1()">
        <fieldset class="form-group">
            <select class="custom-select" name="type" v-model="op.type">
                <option selected>Choose..</option>
                <option value="credit">credit</option>
                <option value="debit">debit</option>                
            </select>
            <select class="custom-select" name="category" v-model="op.category">
                <option selected>choose..</option>                
                <option value="salary">salary</option>
                <option value="housing">housing</option>
                <option value="alimentary">alimentary</option>
                <option value="leisure">leisure</option> 
                <option value="health">health</option>             
            </select>
            <input type="text" name="title" v-model="op.title">
            <input type="date" name="date" v-model="op.date">
            <input type="number" name="amount" min="0" v-model.number="op.amount">
            <input type="submit" value="Add">
        </fieldset>
    </form>
</template>

<script>
export default {
    name: 'addoperation',
    data: function () {
        return {
            op: {
                type: '',
                category: '',
                title: '',
                date: '',
                amount: 0
            }
        };
    },
    methods: {
      action1() { 
          this.$emit('action1', Object.assign({}, this.op));
      },
  }
}
</script>

<style>
fieldset {
    padding: 20px 0;
    margin: 10px 15%;
    border: 1px solid #b8b2b2;
    border-radius: 5px;
}

</style>
