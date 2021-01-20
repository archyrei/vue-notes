<template>
    <div class="formNotes">
        <form @submit="submitNote">
            <div class="menu">
                <button @click="submitRemove" class="bg-danger btn btn-delete" type="button">Delete</button>
                <button class="bg-success btn btn-delete" type="submit">Save</button>
            </div>

            <div class="content">
                <input type="text" class="text" placeholder="id" v-model="id">
                <input type="text" class="text" placeholder="Title" v-model="title">
                <textarea name="" id="" cols="30" rows="10" class="text textarea" placeholder="type whatever you want.." v-model="description"></textarea>
            </div>
        </form>
    </div>
</template>

<script type="text/javascript">
export default {
    name: 'Form',
    props: {
        propSaveNote : {
            type: Function
        }
    },
    data: function () {
        return {
            id: 0,
            title: '',
            description: ''
        }
    },
    methods: {
        submitNote (e) {
            e.preventDefault();
            
            let data = {
                title : this.title,
                description : this.description
            }
                
            if(this.id === 0) {
                this.propSaveNote(this.title, this.description);
            }
            else {
                data.id = this.id;
                this.$root.$emit('emitUpdateNote', data);
            }
        },
        submitRemove() {
            let data = {id : this.id};
            this.$root.$emit('emitRemoveNote', data);
            this.reset();
        },
        reset() {
            this.id = 0;
            this.title = '';
            this.description = '';
        }

    },
    // watch: {
    //     propDataForm: function(note) {
            
    //     }
    // },
    mounted() {
        this.$root.$on('emitForm', data => {
            this.id = data.id;
            this.title = data.title;
            this.description = data.description;
        })
    }
}
</script>