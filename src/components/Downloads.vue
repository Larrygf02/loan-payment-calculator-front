<template>
    <div>
        <button @click="downloadExcel">Descargar en Excel</button>
    </div>
</template>

<script>
import xlsx from 'xlsx';
import { saveAs } from 'file-saver';
export default {
    props: ['data'],
    methods: {
        createWorkbook: function() {
            const workbook = xlsx.utils.book_new();
            workbook.Props = {
                Title: 'Cronograma',
                Subject: 'Test',
                Author: 'RL',
                CreatedDate: new Date()
            }
            workbook.SheetNames.push('Detalle')
            let ws_data = [['hello', 'world']];
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
