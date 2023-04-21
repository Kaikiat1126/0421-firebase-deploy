<template>
  <table>
    <tbody>
        <tr>
            <th>Category</th>
            <th>Value</th>
        </tr>
        <tr>
            <td>Alpha</td>
            <td>{{ alpha }}</td>
        </tr>
        <tr>
            <td>Beta</td>
            <td>{{ beta }}</td>
        </tr>
        <tr>
            <td>Charlie</td>
            <td>{{ charlie }}</td>
        </tr>
    </tbody>
  </table>
</template>

<script>
export default {
    props: {
        alpha: {
            type: Number,
            required: true
        },
        beta: {
            type: Number,
            required: true
        },
        charlie: {
            type: Number,
            required: true
        }
    }
}
</script>