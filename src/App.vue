<template>
  <div id="app">
    <Navigation @onFlag="isAdd"/>
    <AddForm add_or_edit="Добавить" v-if="isEdit_flag" @onAdd="addStudent"/>
    <StudentList v-else :student-list="studentList" @onRemove="removeStudent" @onEdit="Edit"/>
  </div>
</template>

<script>
import Navigation from './components/Navigation.vue'
import AddForm from './components/AddForm.vue'
import StudentList from './components/StudentList.vue'

export default {
  name: 'App',
  components: {
    Navigation,
    AddForm,
    StudentList,
  },
  data() {
    return {
      isEdit_flag: false,
      studentList: [
        {name: 'admin', surname: 'admin', course: '123'},
        {name: 'admin2', surname: 'admin2', course: '321'}
      ]
    }
  },
  methods: {
    addStudent(stud) {
      this.studentList.push(stud)
    },
    removeStudent(index) {
      this.studentList.splice(index, 1)
    },
    isAdd(flag) {
      this.isEdit_flag = flag
    },
    Edit(index, stud) {
      this.studentList[index] = stud
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 50px;
}
</style>
