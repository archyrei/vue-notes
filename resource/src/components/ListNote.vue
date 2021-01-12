<template>
    <div class="listNotes">
        <ul>
            <li v-for="(row, index) in notes" :key="index">
                <button class="btn-note" @click="EditNote(row.id)">
                    <label for="">{{row.title}}</label>
                    <span>{{row.description}}</span>
                </button>
            </li>
        </ul>
    </div>
</template>

<script type="text/javascript">
export default {
    name: 'listNotes',
    data: function() {
        return {
            notes: [
               {   
                    id: 1,
                    title: 'Note Kamis 10 Desember 2020',
                    description: 'sudah memasuki akhir tahun 2020'
               },
               {
                    id: 2,
                    title: 'Note Kamis 7 Januari 2021',
                    description: 'Ya ini..'
               }
          ]
        }
    },
    props: {
        propEditNote : {
            type: Function
        }
    },
    methods: {
        EditNote(id) {
          let dataForm = this.notes.find(note => note.id === id);

          this.$root.$emit('emitForm', dataForm);
       }
    }

}
</script>