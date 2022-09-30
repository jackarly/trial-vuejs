<template>
    <form @submit="onSubmit" class="add-form">
      <div class="form-control">
        <!-- <label>Title</label> -->
        <input v-model="title"
                type="text"
                name="title"
                placeholder="Title" />
      </div>
      <!-- {{ text }} -->
      <div class="form-control">
        <!-- <label>Body</label> -->
        <!-- <input v-model="body"
                type="textbox"
                name="body"
                placeholder="Note"
        /> -->
        <textarea v-model="body"
                name="body"
                placeholder="Note"></textarea>
      </div>
      <input type="submit" value="Save Task" class="btn btn-block" />
    </form>
</template>

<script>
export default {
    name: 'AddNote',
    data() {
        return {
            title: '',
            body: '',
        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault()

            if(!this.title){
                alert('Please add a note')
                return
            }
            
        
            const newNote = {
                id: Math.floor(Math.random() * 10000),
                title: this.title,
                body: this.body,
                date: new Date().toLocaleString(),
            }

            this.$emit('add-note',newNote)

            this.title = ''
            this.body = ''
        }
    },

}
</script>

<style scoped>
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
    height: 100px;
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
.btn {
display: inline-block;
background: #000;
color: #fff;
border: none;
padding: 5px 10px;
margin: 5px;
border-radius: 5px;
cursor: pointer;
text-decoration: none;
font-size: 20px;
font-family: inherit;
}
</style>