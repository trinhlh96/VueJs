<template>
    <div>
        <h1>employees</h1>

        <table class="table table-hover">
            <thead>
            <tr>
                <td>Id</td>
                <td>Name</td>
                <td>Wage</td>
            </tr>
            </thead>

            <tbody>
                <tr v-for="item in items" :key="item.id">
                    <td>{{ item.id }}</td>
                    <td>{{ item.name }}</td>
                    <td>{{ item.wage }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>

    export default {
        data(){
            return{
                items: []
            }
        },

        created: function()
        {
            this.fetchItems();
        },

        methods: {
            fetchItems()
            {
              let uri = 'http://localhost:8089/employees/index';
              this.axios.get(uri).then((response) => {
                  this.items = response.data;
                  console.log(this.items);
              });
            },
        }
    }
</script>
