<template>
    <div class="cronogram">
        <table>
            <tr>
                <th>Nº Cuotas</th>
                <th>F. Vencimiento</th>
                <th>Amortización</th>
                <th>Interés</th>
                <th>Cuota</th>
                <th>Saldo Pendiente</th>
            </tr>
            <tr v-for="(item, i) in data" :key="i">
                <td>{{ i + 1 }}</td>
                <td>{{ item.payday }}</td>
                <td>{{ item.amortization }}</td>
                <td>{{ item.interest }}</td>
                <td>{{ item.fee }}</td>
                <td>{{ item.capital }}</td>
            </tr>
        </table>
    </div>
</template>

<script>
export default {
    props: ['data']
}
</script>


<style scoped>
    table {
        border-collapse: collapse;
        border-spacing: 0;
        width: 100%;
        border: 1px solid #ddd;
        background: #fff;
    }

    th, td {
        text-align: center;
        padding: 8px;
    }

    .cronogram {
        overflow-x: auto;
    }

</style>