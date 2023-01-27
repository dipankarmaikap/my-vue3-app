<template>
    <div class="list-expence w-full md:w-3/4 lg:w-4/6">
        <p class="text-white font-bold text-3xl mb-4">Expence List</p>
        <div v-if="expences.length > 0" class="full-list">
            <table class="table-auto text-white w-full">
                <thead>
                    <tr>
                        <th>Name</th>
                        <th>Category</th>
                        <th>Date</th>
                        <th>Amount</th>
                        <th>Description</th>
                        <th>Action</th>
                    </tr>
                </thead>
                <tbody v-for="{ id, name, category, date, amount, description } in expences">
                    <tr>
                        <td>{{ name }}</td>
                        <td>{{ category }}</td>
                        <td>{{ date }}</td>
                        <td>{{ amount }}</td>
                        <td>{{ description }}</td>
                        <td><button @click="removeExpence(id)" class="bg-white text-black px-1">Delete</button></td>
                    </tr>
                </tbody>

            </table>
        </div>
        <div class="border p-4 min-h-[100px]" v-else>
            <p class="text-white">Please add a expence first 😢</p>
        </div>
    </div>
</template>

<script  lang="ts">

let props = {
    expences: null, removeExpence: null
}
export default {
    name: 'ListExpences',
    props
}
</script>

<style>
table,
th,
td {
    border: 1px solid rgb(191, 191, 191);
    padding: 10px 4px;
}
</style>