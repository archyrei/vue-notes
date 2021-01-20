<template>
  <div id="app">
    <div class="left-side">
      <div class="app-logo">
        <a href="https://wegodev.com/">
          <h2>Wegodev</h2>
          <span>Notes</span>
        </a>
      </div>
      <div class="notes-frame">
        <button class="bg-success btn btn-new-note" @click="newNote">
          + New Note
        </button>
        <ListNote/>
      </div>
    </div>

    <div class="right-side">
         <Form :propSaveNote="saveNote"/>
    </div>

  </div>
</template>

<script>
import ListNote from './components/ListNote.vue'
import Form from './components/Form.vue'

export default {
  name: 'App',
  data: function () {
     return {
     }
  },
  components: {
       ListNote,
       Form
  },
  methods: {
       newNote() {
            this.dataForm = {id:0, title: '', description: ''}
       },
       saveNote(title, description) {
            let newId = 0;

            if(this.notes.length === 0){
                 newId = 1;
            }
            else{
                 newId = this.notes[this.notes.length - 1].id + 1;
            }
            let newNote = { id:newId, 'title':title, 'description':description }
            this.notes.push(newNote);
            this.EditNote(newId);
       }
  }
}
</script>

<style>
body{
     margin:0px;
     overflow:hidden;
}
#app {
     font-family: 'Avenir', Helvetica, Arial, sans-serif;
     color: #2c3e50;
     padding:0px;

     display:flex;
     width:100%;
}

.left-side{
     width: 400px;
     background: #f7f7f7;
     color: #616161;
}

.right-side{
     width: 100%;
     overflow-y: scroll;
     height: 100vh;
     border-left: 1px solid gainsboro;
}

.app-logo{
     padding: 25px 15px;
     border-bottom: 1px solid gainsboro;
}
.app-logo a{
     text-decoration:none;
}
.app-logo a h2{
     margin: 0px;
     display: inline;
     margin-right: 5px;
     font-size: 35px;
     text-transform: capitalize;
     color: #757575;
}
.app-logo a span{
     font-size: 12px;
     letter-spacing: 1px;
     text-transform: uppercase;
     color:#139e5f;
}
.notes-frame{
     overflow-y: scroll;
     overflow-x: hidden;
     height: 85vh;
}
.bg-success{
     background: #219a63;
     color: white;
     outline:none;
}
.bg-success:hover{
     background:#24b774;
     color: white;
}
.bg-danger{
     background:#b50000;
     color: white;
}
.bg-danger:hover{
     background:#c50000;
}
.btn{
     border: none;
     font-size: 12px;
     text-align: center;
     letter-spacing: 1px;
     cursor: pointer;
     border-radius: 2px;
     padding: 7px 25px;
     outline:none;
}
.btn-new-note{
     width: 90%;
     padding: 12px 10px;
     margin: 10px 15px;
     text-align: left !important;
}

ul {
     list-style-type: none;
     padding: 0;
     margin:0px;
}
.btn-note {
     text-align: left;
     border: none;
     border-bottom: 1px solid gainsboro;
     padding: 0px 15px;
     cursor: pointer;
     outline: none;
     background: #f7f7f7;
     height: 150px;
     width: 100%;
}
.btn-note:hover {
     background:#eaeaea;
}
.btn-note label{
     display:block;
     color: #444444;
     font-size: 1.5em;
     margin-bottom: 15px;
}
.btn-note span{
    color: #545454;
}

.menu{
     background: #f7f7f7;
     padding:10px 25px;
     margin-bottom: 25px;
     text-align:right;
     border-bottom: 1px solid #e8e6e6;
}
.btn-delete{ margin-right:10px; }
.content{
     padding: 0px 25px;
}
.text{
     display: block;
     width: 100%;
     padding: 0px;
     font-size: 20px;
     font-weight: bold;
     color: #2c3e50;
     border: none;
     margin-bottom: 10px;
     box-sizing: border-box;
     outline: none;
}
.textarea{
     min-height: 350px;
     font-size: 15px;
     font-weight: lighter;
     line-height: 30px;
}
.loader{
     vertical-align: middle;
}

/* width */
::-webkit-scrollbar {
  width: 5px;
}

/* Track */
::-webkit-scrollbar-track {
  background: #f7f7f7;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: #888;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #555;
}
</style>

