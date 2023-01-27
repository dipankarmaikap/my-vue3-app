
<template>
    <ExpenceOverview :totalExpence="totalExpence" :allCats="allCats" />
    <div class="p-4 flex flex-wrap md:flex-nowrap md:space-x-6">
        <AddExpence :category="category" :addExpence="addExpence" />
        <ListExpences :expences="expences" :removeExpence="removeExpence" />
    </div>
</template>

<script  lang="ts">
import { ref, computed } from "vue"
import { nanoid } from 'nanoid'
import ExpenceOverview from "./ExpenceOverview.vue"
import ListExpences from "./ListExpences.vue"
import AddExpence from "./AddExpence.vue"
export default {
    name: 'ExpenceManager',
    components: { ExpenceOverview, ListExpences, AddExpence },
    setup() {
        let expences = ref([
            {
                id: nanoid(),
                name: 'Beer',
                description: "This is a default Entry",
                amount: 25,
                category: "Party",
                date: "2023-01-25"
            },
            {
                id: nanoid(),
                name: 'Beer',
                description: "This is a default Entry",
                amount: 5,
                category: "Drink",
                date: "2023-01-25"
            },
            {
                id: nanoid(),
                name: 'Beer',
                description: "This is a default Entry",
                amount: 5,
                category: "Travel",
                date: "2023-01-25"
            },
            {
                id: nanoid(),
                name: 'Beer',
                description: "This is a default Entry",
                amount: 5,
                category: "Drink",
                date: "2023-01-25"
            },
            {
                id: nanoid(),
                name: 'Beer',
                description: "This is a default Entry",
                amount: 15,
                category: "Drink",
                date: "2023-02-25"
            },
            {
                id: nanoid(),
                name: 'Beer',
                description: "This is a default Entry",
                amount: 50,
                category: "Health",
                date: "2023-02-25"
            },
        ])
        function addExpence(e) {
            const formData = new FormData(e.target);
            const data = {
                id: nanoid(),
                name: 'Beer',
                description: "",
                amount: 5,
                category: "Food",
                date: "2023-01-25"
            };
            // need to convert it before using not with XMLHttpRequest
            for (let [key, val] of formData.entries()) {
                Object.assign(data, { [key]: val })
            }
            expences.value.push(data)
            e.target.reset()
        }
        function removeExpence(id: string) {
            expences.value = expences.value.filter(ex => ex.id !== id)
        }
        let category = ["Drink", "Party", "Travel", "Health", "Food", "Shopping"]
        let totalExpence = computed(() => expences.value.reduce(
            (accumulator, currentValue) => accumulator + parseInt(currentValue.amount.toString()),
            0
        ))
        //  let existCat = [...new Set(expences.value.map(e => e.category))]
        let allCats = computed(() => {
            return category.map(cat => {
                return {
                    name: cat,
                    total: expences.value.filter(e => e.category === cat).reduce(
                        (accumulator, currentValue) => accumulator + parseInt(currentValue.amount.toString()),
                        0
                    )
                }
            })
        })
        return { expences, category, addExpence, allCats, totalExpence, removeExpence }
    }
}
</script>
