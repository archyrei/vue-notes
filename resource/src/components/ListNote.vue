<template>
    <div class="listNotes">
        <ul>
            <li v-for="(row, index) in propNotes" :key="index">
                <button class="btn-note" @click="idNote(row.id)">
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
    props: {
        propNotes : {
            type: Array
        },
        propEditNote : {
            type: Function
        }
    },
    methods: {
        idNote(id) {
            this.propEditNote(id);
        }
    }

}
</script>