<template>
  <div id="app" class="container-fluid">
    <div class="row">
      <div style="font-weight: bold;" class="m-0 p-0 border-bottom col-lg-12 d-flex align-items-center">
          <div class="px-3 m-0">
              <router-link to="/"><h1 class="my-2">EClass</h1></router-link>
          </div>
          <div class="col m-0 text-right">
              <button type="button" class="border-0 bg-white font-weight-bold">Log Out</button>
          </div>
      </div>
      <div class="col-12 col-sm-2 p-0 bg-primary">
        <div class="list-group mt-3" id="list-tab" role="tablist">
          <a style="font-size: 25px;" class="list-group-item list-group-item-action border-0 bg-primary text-white rounded-0" id="list-Upload-list" data-toggle="list" href="#list-home" role="tab"><h5 class="m-0 font-weight-bold">Upload Course</h5></a>
          <a style="font-size: 25px;" class="list-group-item list-group-item-action border-0 bg-primary text-white rounded-0" id="list-Catrgories-list" data-toggle="list" href="#list-profile" role="tab"><h5 class="m-0 font-weight-bold">Categories</h5></a>
          <a style="font-size: 25px;"  class="list-group-item list-group-item-action border-0 bg-primary text-white rounded-0" id="list-User-list" data-toggle="list" href="list-User" role="tab"><h5 class="m-0 font-weight-bold">User</h5></a>
        </div>
      </div>
      <router-view/>
    </div>
  </div>
</template>

<script>
  
  export default {
    name: 'app',
    data() {
      return {
        isLoggedIn: false
      }
    }
  }

</script>