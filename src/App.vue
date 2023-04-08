<template>
  <div class="app">
    <div class="container">
      <header class="text-center bg-dark p-5 text-white fs-3">My ToDo List</header>
      <table class="table">

        <div class="input-group my-3 bg-secondary">
          <input type="text" class="form-control" placeholder="Recipient's username" aria-label="Recipient's username" aria-describedby="basic-addon2">
          <div class="input-group-append">
            <button class="btn btn-dark text-white" type="button">Button</button>
          </div>
        </div>

        <thead>
          <tr>
            <th scope="col">#</th>
            <th scope="col">First</th>
            <th scope="col">Last</th>
            <th scope="col">Handle</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <th scope="row">1</th>
            <td>Mark</td>
            <td>Otto</td>
            <td>@mdo</td>
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

  })
}
</script>