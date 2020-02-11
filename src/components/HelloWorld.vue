<template>
<body>
    <div class="form-body">
    <h1>My Todo Maker</h1>
    <form @submit.prevent="tambahTodo">
    <div class="todolist-form">
      <h4>Judul Tugas</h4>
      <input v-model="TodoBaru" type="text" name="TodoBaru" >
      <h4>Detail Tugas</h4>
      <input v-model="DetailBaru" type="text" name="DetailBaru" >
      <h4>Deadline</h4>
      <input v-model="DeadlineBaru" type="text" name="DeadlineBaru" >
      <button class="btn-tambah" type="submit" name="tambahTodo">Tambah</button>
   </div>
   </form>
   </div>
   <div class="todos-body">
   <h1>My Todo List</h1>
      <div class="card-todos">
      <li v-for="todo in TodoKu" :key="todo">
        <h3 :class="{ selesai: todo.selesai }">{{todo.Todo}}</h3>
        <h4>Deadline Tugas</h4>
        <h6 :class="{ selesai: todo.selesai }">{{todo.Deadline}}</h6>
        <h4>Detail Tugas</h4>
        <h6 :class="{ selesai: todo.selesai }">{{todo.Detail}}</h6>
        <button @click="hapusTodo(todo)" class="btn-hapus" type="button">Hapus</button>
      </li>
      </div>
   </div>
</body>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: function () {
    return {
      TodoBaru: '',
      DetailBaru: '',
      DeadlineBaru: '',
      TodoKu: [],
      Todo: '',
      Deadline: '',
      Detail: ''
    }
  },
  props: {
    msg: String
  },
  methods: {
    tambahTodo () {
      this.TodoKu.push({
        Todo: this.TodoBaru,
        Deadline: this.DeadlineBaru,
        Detail: this.DetailBaru,
        done: false
      })
      this.TodoBaru = ''
      this.DeadlineBaru = ''
      this.DetailBaru = ''
    },
    hapusTodo (todo) {
      const indexTodo = this.TodoKu.indexOf(todo)
      this.TodoKu.splice(indexTodo, 1)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
  padding: 2.5%;
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  color: black;
  background-color: #f62a00;
}
h4 {
  text-align: left;
  color: black;
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  font-size: 15px;
  font-weight: 500;
}
.card-todos h4 {
  margin-left: 10px;
  line-height: 1px;
}
h3 {
  padding: 10px;
  text-align: center;
  color: white;
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  font-style: oblique;
  border-bottom: 2px solid black;
}
h6 {
  margin-left: 10px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color:white;
  text-align: left;
  font-weight: 500;
  font-size: 15px;
 }
input {
  padding: 8px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  margin: auto;
  border: none;
  border-radius: 5px;
}
li {
  list-style: none;
  margin: 30px;
  border : 2px solid black;
  border-radius: 10px;
  padding: 10px;
}
li h4 {
  font-size: 20px;
  font-weight: 600;
}
.form-body {
  background-color: #4897d8;
  border-radius: 10px;
}
.todolist-form {
  margin-bottom: 30px;
  padding: 5%;
  border-radius: 15px;
  background-color: #a1d6e2;
  display: inline-flex;
  flex-direction: column;
  box-shadow: 2px 8px 8px 2px rgba(0,0,0,0.2);
}
button {
  transition-duration: 0.4s;
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  font-weight: 600;
  border: none;
}
.btn-tambah {
  margin-top: 30px;
  text-transform: uppercase;
  padding: 5px;
  border-radius: 10px;
  color: #f1f1f2;
  background-color: #1995ad;
}
.btn-tambah:hover {
  background-color: #76d8eb;
}
.btn-hapus{
  font-size: 15px;
  padding: 10px;
  border-radius: 10px;
  color: #f1f1f2;
  background-color: #30896d;
}
.btn-hapus:hover {
  background-color: #98dbc6;
}
.card-todos {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 2fr));
  grid-gap: 20px;
  align-items: stretch;
  background-color: #5bc8ac;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  border-radius: 10px;
}
.todos-body h1 {
  background-color: #FFBB00;
  border-radius: 10px;
}
.selesai {
  text-decoration: line-through;
}
</style>
