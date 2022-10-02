<template>
    <!-- FORM -->
    <div v-show="showAddNote">
        <form @submit="onSubmit" class="add-form">
            <div class="form-control">
                <input v-model="title"
                    type="text"
                    name="title"
                    placeholder="Title" />
            </div>
            <div class="form-control">
                <textarea v-model="body"
                    name="body"
                    placeholder="Note"></textarea>
            </div>
            <input type="submit" value="Save" class="btn btn-block btn-save" />
        </form>
    </div>

    <!-- NOTELIST -->
    <h2>All Notes</h2>
    <hr>
    <div v-if="!noteList.length">
        <p>Tap the + button to create a note.</p>
    </div>
    <div :key="index" v-for="(note,index) in noteList">
        <div @dblclick="onUpdate(index)" class="note">
            <h3>{{ note.title }}
                <i class="fa fa-times" @click="onDelete(index)" ></i>
            </h3>
            <p>{{ note.date }}</p>
        </div>
    </div>
    <div v-if="noteList.length">
        <small>Double click to edit</small>
    </div>
</template>

<script>
    export default {
        name: 'NoteList',
        props: {
            showAddNote: Boolean,
        },
        data() {
            return {
                noteList:[],
                title: '',
                body: '',
                updateNote: null,
            }
        },
        methods: {
            onSubmit(e) {
                e.preventDefault()
                if(!this.title){
                    alert('Please add a note')
                    return
                }

                if (this.updateNote != null){
                    this.noteList[this.updateNote].title = this.title;
                    this.noteList[this.updateNote].body = this.body;
                    this.updateNote = null;
                }else{
                    const newNote = {
                        title: this.title,
                        body: this.body,
                        date: new Date().toLocaleString(),
                    }
                    this.noteList = [...this.noteList, newNote]
                }
                this.title = ''
                this.body = ''
            },
            onDelete(index){
                if(confirm('Are you sure you want to delete this note?')){
                    this.noteList.splice(index, 1);
                }
            },
            onUpdate(index){
                this.title = this.noteList[index].title;
                this.body = this.noteList[index].body;
                this.updateNote = index;
                this.$emit('toggle-true')
            },
        },
        created (){
            this.noteList = [
                {
                title: 'Science' ,
                body: 'It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.',
                date: '9/28/2022, 1:34:36 AM', 
                },
                {
                title: 'Math Assignment' ,
                body: '2',
                date: '9/28/2022, 4:50:03 PM', 
                },
                {
                title: 'Passwords' ,
                body: '3',
                date: '9/29/2022, 1:14:46 PM', 
                },
            ]
        },
        emits: ['toggle-true'],
    }
</script>

<style>
    *{
        font-family: 'Poppins', sans-serif;
    }
    small {
        padding-left: 5px;
        font-style: italic;
    }
    .add-form {
        margin-bottom: 40px;
    }
    .form-control {
        margin: 5px 0;
    }
    .form-control label {
        display: block;
    }
    .form-control input {
        width: 100%;
        height: 40px;
        margin: 5px;
        padding: 3px 7px;
        font-size: 17px;
    }
    .form-control textarea {
        width: 100%;
        height: 150px;
        margin: 5px;
        padding: 3px 7px;
        font-size: 17px;
    }
    .form-control-check {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    .form-control-check label {
        flex: 1;
    }
    .form-control-check input {
        flex: 2;
        height: 20px;
    }
    .fa-times {
        color: red;
    }
    .note {
        background: #f4f4f4;
        margin: 5px;
        padding: 10px 20px;
        cursor: pointer;
    }
    .note h3 {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    i {
        color: rgb(5, 90, 5);
    }
    .btn-save{
        background: green;
        color: #fff;
        font-size: 25px;
    }
</style>

