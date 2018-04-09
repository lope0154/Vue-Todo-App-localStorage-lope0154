<template>
  <div>
    <section class="dropdown">
      <section class="dropdown-trigger">
    <label>Due date
      <input type="date" v-model="newTask.dueDate" class="button">
    </label>
    <label>Priority
    <label class="dropdown-trigger">
    <select v-model="newTask.priority" class="button">
      <option value="high">high</option>
      <option value="medium">medium</option>
      <option value="low">low</option>
    </select>
    </label>
    </label>
    <label>Category
    <label class="dropdown-trigger">
    <select v-model="newTask.category" class="button">
      <option value=" "> </option>
      <option value="home">home</option>
      <option value="school">school</option>
      <option value="work">work</option>
    </select>
    </label>
    </label>
    </section>
    </section>
    <section>
      <div class="control">
      <input class="input" type="text" placeholder="Task Title" v-model.trim="newTask.title" @keyup.enter="addTask">
      </div>
    <button @click="addTask" class="button is-pulled-right">Add Task</button>
    </section>
  </div>
</template>

<script>
export default {
  data () {
    return {
      newTask: {}
    }
  },
  created () {
    this.newTask = this.getNewTask()
  },
  methods: {
    addTask () {
      // this.taskList.push(this.newTask)
      this.$emit('taskAdded', this.newTask)
      this.newTask = this.getNewTask()
    },
    getNewTask () {
      const now = new Date()
      const today = now.toISOString().substr(0, now.toISOString().indexOf('T'))
      console.log(now)
      return {
        id: null,
        category: ' ',
        dueDate: today,
        isComplete: false,
        priority: 'medium',
        title: ''
      }
    }
  }
}
</script>

<style>
section {
  padding-top: 0.25rem;
  padding-bottom: 0.25em;
}
</style>