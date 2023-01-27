<template>
    <div class="add-expence w-full md:w-1/4 lg:w-2/6">
        <p class="text-white font-bold text-3xl mb-4">Expence Form</p>
        <form class="expence-form flex flex-col space-y-4" @submit.prevent="addExpence">
            <input required type="text" name="name" placeholder="Add your expence name">
            <select required name="category" id="expence-category">
                <option value="">Select a category</option>
                <template v-for="exp in category">
                    <option :value="exp">{{ exp }}</option>
                </template>
            </select>
            <input required type="date" name="date" id="date">
            <input required type="number" min="1" name="amount" placeholder="Add expence amount">
            <textarea name="description" placeholder="Add a detailed description if you want." id="description"
                cols="10" rows="5"></textarea>
            <button class="bg-white p-2" type="submit">Add Expence</button>
        </form>
    </div>
</template>

<script  lang="ts">

let props = {
    category: null, addExpence: null
}
export default {
    name: 'AddExpence',
    props
}
</script>

<style>
input,
textarea,
select {
    @apply p-1
}
</style>

