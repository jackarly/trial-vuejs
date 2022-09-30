<template>
  <div class="container">
    <!-- HEADER & ADD NOTES -->
    <!-- <h3>eListahan</h3> -->
    <Header @toggle-add-note="toggleAddNote" />
    <div v-show="showAddNote">
      <AddNote @add-note="addNote" />
    </div>
    <NoteList :noteList="noteList" 
      @delete-note="deleteNote"
      @toggle-update="toggleUpdate" />
    <!-- NOTE LIST -->


  </div>
</template>

<script>
import Header from './components/Header.vue';
import NoteList from './components/NoteList.vue';
import AddNote from './components/AddNote.vue';

export default {
  name: 'App',
  components: {
    Header,
    NoteList,
    AddNote,
},
  data (){
    return {
      noteList:[],
      showAddNote: false,
    }
  },
  methods:{
    toggleAddNote(){
      this.showAddNote = !this.showAddNote
    },
    addNote(note){
      this.noteList = [...this.noteList, note]
    },
    deleteNote(id){
      // console.log('note', id)
      if(confirm('Are you sure you want to delete this note?')){
        this.noteList = this.noteList.filter((note) => note.id != id)
      }
    },
    toggleUpdate(id) {
      console.log(id)
    }
  },
  created (){
    this.noteList = [
      {
        id: 1,
        title: '1' ,
        body: '1',
        date: '1', 
      },
      {
        id: 2,
        title: '2' ,
        body: '2',
        date: '2', 
      },
      {
        id: 3,
        title: '3' ,
        body: '3',
        date: '3', 
      },
    ]
  },
}

</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
  
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  
  body {
    font-family: 'Poppins', sans-serif;
  }
  
  .container {
    max-width: 500px;
    margin: 30px auto;
    overflow: auto;
    min-height: 300px;
    border: 1px solid steelblue;
    padding: 30px;
    border-radius: 5px;
  }
  
  .btn {
    display: inline-block;
    /* background: #000;
    color: #fff; */
    background: #fff;
    border: none;
    /* padding: 5px 10px; */
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 30px;
    font-family: inherit;
  }
  
  .btn:focus {
    outline: none;
  }
  
  .btn:active {
    transform: scale(0.98);
  }
  
  .btn-block {
    display: block;
    width: 100%;
  }
  </style>
  