<template>
    <div class="dashboard p-4">
        <p class="text-white font-bold text-3xl mb-4">Overview of your expence</p>
        <div class="total text-white ">
            <p class="text-2xl font-bold">Total expence : {{ totalExpence }}</p>
            <p class="mt-4 mb-2">Expence by category</p>
            <div v-if="allCats.length > 0" class="full-list">
                <table class="table-auto text-white w-full">
                    <thead>
                        <tr>
                            <th v-for="{ name } in allCats">
                                {{ name }}
                            </th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td v-for="{ total } in allCats">{{ total }}</td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <div class="border p-4 min-h-[100px]" v-else>
                <p class="text-white">Please add a expence first 😢</p>
            </div>
        </div>
    </div>
</template>

<script  lang="ts">

let props = {
    totalExpence: null, allCats: null
}
export default {
    name: 'ExpenceOverview',
    props
}
</script>