<template>
    <div class="download">
        <font-awesome-icon :icon="iconExcel" @click="downloadExcel" size="3x" color="green"/>
    </div>
</template>

<script>

import xlsx from 'xlsx';
import { saveAs } from 'file-saver';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faFileExcel } from '@fortawesome/free-solid-svg-icons' 
export default {
    props: ['data'],
    data() {
        return {
            iconExcel: faFileExcel
        }
    },
    components: {
        FontAwesomeIcon
    },
    methods: {
        transformData: function() {
            let columns = []
            let header = ['NºCuotas', 'F.Vencimiento', 'Amortizacion', 'Interes', 'Cuota', 'Saldo Pendiente']
            columns.push(header)
            this.data.forEach((item, i) => {
                const {payday, amortization, interest, fee, capital } = item
                columns.push([(i+1), payday, amortization, interest, fee, capital])
            })
            return columns;
        },
        createWorkbook: function() {
            const workbook = xlsx.utils.book_new();
            workbook.Props = {
                Title: 'Cronograma',
                Subject: 'Test',
                Author: 'RL',
                CreatedDate: new Date()
            }
            workbook.SheetNames.push('Detalle')
            let ws_data = this.transformData();
            let ws = xlsx.utils.aoa_to_sheet(ws_data);
            workbook.Sheets["Detalle"] = ws;
            let wbout = xlsx.write(workbook, {bookType: 'xlsx', type: 'binary'})
            return wbout;
        },

        s2ab: function(wbout) { 
            let buf = new ArrayBuffer(wbout.length); //convert s to arrayBuffer
            let view = new Uint8Array(buf);  //create uint8array as viewer
            for (let i=0; i<wbout.length; i++) view[i] = wbout.charCodeAt(i) & 0xFF; //convert to octet
            return buf;    
        },
        downloadExcel: function() {
            saveAs(new Blob([this.s2ab(this.createWorkbook())],{type:"application/octet-stream"}), 'test.xlsx');
        }

    }
}
</script>
<style scoped>
    .download {
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 2rem;
    }
</style>
