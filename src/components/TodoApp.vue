<template>
  <div class="container">
    <h2 class="text-center mt-5">Todo App</h2>

    <!-- Input -->
    <div class="d-flex">
      <input type="text" placeholder="Enter task" class="form-control">
      <button class="btn btn-warning rounded-0">SUBMIT</button>
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
    <tr>
      <th>Criar aplicativo Vue.js</th>
      <td>Doing</td>
      <td>
        <div class="text-center">
          <span class="fa fa-pen"></span>
        </div>
      </td>
      <td>
        <div class="text-center">
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
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>