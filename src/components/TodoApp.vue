<template>
  <div class="container">
    <h2 class="text-center mt-5">Todo App</h2>

    <!-- Input -->
    <div class="d-flex">
      <input v-model="task" type="text" placeholder="Enter task" class="form-control">
      <button @click="submitTask" class="btn btn-warning rounded-0">SUBMIT</button>
    </div>
    
    <!-- Task table -->
    <table class="table table-bordered mt-5">
  <thead>
    <tr>
      <th scope="col">Task</th>
      <th scope="col">Status</th>
      <th scope="col" class="text-center">#</th>
      <th scope="col" class="text-center">#</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(task, index) in tasks" :key="index">
      <td>
        <span :class="{'done': task.status === 'Done'}">{{ task.name }}</span>
      </td>
      <td style="width: 120px">
        <span @click="changeStatus(index)" class="pointer"
        :class="{'text-danger': task.status === 'To-Do',
                 'text-warning': task.status === 'Doing',
                 'text-success': task.status === 'Done',}">
          {{ task.status }}
        </span>
      </td>
      <td>
        <div class="text-center" @click="editTask(index)">
          <span class="fa fa-pen"></span>
        </div>
      </td>
      <td>
        <div class="text-center" @click="deleteTask(index)">
          <span class="fa fa-trash"></span>
        </div>
      </td>
    </tr>
  </tbody>
</table>
</div>
</template>

<script>
export default {
  name: 'TodoApp',
  props: {
    msg: String
  },

  data () {
    return {
      task: "",
      editedTask: null,
      tasks: [
        {
          name: 'Create Vue.js App',
          status: 'To-Do'
        },
        {
          name: 'Make it awesome!',
          status: 'To-Do'
        }
      ],
      statuses: ['To-Do', 'Doing', 'Done']
    }
  },

  methods: {
    submitTask() {
      if(this.task.length === 0) return;
      if(this.editedTask == null){
        this.tasks.push({
        name: this.task,
        status: "To-Do"
        });
      } else {
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null;
      }
      this.task = ''
    },
    
    deleteTask(index) {
      this.tasks.splice(index, 1)
    },

    editTask(index) {
      this.task = this.tasks[index].name;
      this.editedTask = index;
    },

    changeStatus(index) {
    let newIndex = this.statuses.indexOf(this.tasks[index].status);
    if (++newIndex > 2) newIndex = 0;
    this.tasks[index].status = this.statuses[newIndex];
    }
  }
}
</script>

<style scoped>
.pointer {
  cursor: pointer;
}

.done {
  text-decoration: line-through;
}
</style>