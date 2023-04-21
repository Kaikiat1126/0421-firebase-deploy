<template>
    <table>
        <tbody>
            <tr>
                <th>Index</th>
                <th>Value</th>
            </tr>
            <tr v-for="item in data" :key="item.index">
                <td>{{ item.index }}</td>
                <td>{{ item.value }}</td>
            </tr>
        </tbody>
    </table>
</template>

<script>

export default {
    props: ['data']
}
</script>

<style>
    table{
        border-collapse: collapse;
        width: 100%;
        max-width: 750px;
        margin: auto;
    }

    th {
        background-color: #f2f2f2;
        font-weight: bold;
        color: #333;
    }

    th, td {
        padding: .65rem;
        text-align: center;
        border: 1px solid #ddd;
    }
</style>