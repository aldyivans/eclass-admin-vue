<template>
  <div id="app" class="container-fluid">
    <div class="row">
      <div style="font-weight: bold;" class="m-0 p-0 border-bottom col-lg-12 d-flex align-items-center">
          <div class="m-0 p-0">
              <a class="nav-link mb-0 pb-0" href="index.html"><h1>EClass</h1></a>
          </div>
          <div class="col m-0 text-right">
              <a href="#" style="font-weight: bold; color: black;">Log Out</a>
          </div>
      </div>
      <div class="col-12 col-sm-3 p-0 bg-primary">
        <div class="list-group" id="list-tab" role="tablist">
          <a style="font-size: 25px;" class="list-group-item list-group-item-action border-0 bg-primary text-white rounded-0" id="list-Upload-list" data-toggle="list" href="#list-home" role="tab"><h5>Upload Course</h5></a>
          <a style="font-size: 25px;" class="list-group-item list-group-item-action border-0 bg-primary text-white rounded-0" id="list-Catrgories-list" data-toggle="list" href="#list-profile" role="tab"><h5>Categories</h5></a>
          <a style="font-size: 25px;"  class="list-group-item list-group-item-action border-0 bg-primary text-white rounded-0" id="list-User-list" data-toggle="list" href="list-User" role="tab"><h5>User</h5></a>
        </div>
      </div>
    </div>
    <router-view/>
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