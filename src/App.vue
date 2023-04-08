<template>
  <div class="app">
    <div class="container">
      <header class="text-center bg-dark p-5 text-white fs-3">My ToDo List</header>
      
      <div class="input-group bg-secondary my-3">
        <input type="text" class="form-control" placeholder="Add Procedure" v-model="userInput.todo"  v-on:keyup.enter="addProcedure" aria-label="Recipient's username" aria-describedby="basic-addon2">
        <div class="input-group-append" style="background-color: rgba(221, 221, 221, 0.892);">
          <button class="btn btn-dark text-white rounded mx-1" type="button" @click="addProcedure">Add</button>
          <button class="btn btn-dark text-white rounded mx-1" type="button" v-if="doneTasks != '' && showCompletedTasksStatus == false" @click="showCompletedTasks">Show Completed Tasks</button>
          <button class="btn btn-dark text-white rounded mx-1" type="button" v-if="doneTasks != '' && showCompletedTasksStatus == true" @click="hideCompletedTasks">Hide Completed Tasks</button>
        </div>
      </div>

      <table class="table">
        <thead class="bg-white text-dark">
          <tr>
            <th scope="col">No</th>
            <th scope="col">Tasks</th>
            <th scope="col">Achievement</th>
            <th scope="col">Action</th>
          </tr>
        </thead>

        <tbody>
          <tr v-for="(item,index) in tasks" :key="index">
            <th scope="row">{{ index }}</th>

            <th :class="item.done ? 'text-success' : 'text-danger' ">{{ item.todo }}</th>

            <td v-if="item.done == true" class="text-success">Done</td>
            <td v-else class="text-danger">Need to workon</td>

            <td v-if="item.done == true">
              <input type="checkbox"  disabled checked >
            </td>
            <td v-else>
              <input type="checkbox"  v-model="item.done" @click="filterTask(index)">
            </td>
            

          </tr>
        </tbody>
      </table>
      <hr>

      <header class="text-center bg-secondary p-3 text-white fs-3" v-if="showCompletedTasksStatus == true">Done Tasks</header>

      <table class="table" v-if="showCompletedTasksStatus == true">
        <thead class="bg-white text-dark">
          <tr>
            <th scope="col">No</th>
            <th scope="col">Tasks</th>
            <th scope="col">Achievement</th>
            <th scope="col">Action</th>
          </tr>
        </thead>

        <tbody>
          <tr v-for="(item,index) in doneTasks" :key="index">
            <th scope="row">{{ index }}</th>

            <th scope="row">{{ item.todo }}</th>

            <td v-if="item.done == true">Done</td>
            <td v-else>Need to workon</td>

            <td >
              <input type="checkbox" name="" id="" v-model="item.done" checked disabled>
            </td>

          </tr>
        </tbody>
      </table>

    </div>
  </div>
</template>

<script>
export default{
  name:'app',
  data: () =>({
    userInput: {
      todo: '',
      done:false, 
    },
    tasks :[],
    doneTasks:[],
    showCompletedTasksStatus : false,
  }),
  methods:{
    addProcedure(){
      if(this.userInput.todo != ''){
        this.tasks.push({
          todo: this.userInput.todo,
          done: this.userInput.done
        })
        this.userInput.todo = ''
      }
    },

    filterTask(index){
      this.tasks.done = true;
      this.doneTasks.push({
        todo: this.tasks[index].todo,
        done: this.tasks.done
      })
    },

    showCompletedTasks(){
      if(this.doneTasks != ''){
        this.showCompletedTasksStatus = true;
      }
    },

    hideCompletedTasks(){
        this.showCompletedTasksStatus = false;
    }
  }
}
</script>
