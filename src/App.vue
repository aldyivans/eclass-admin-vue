<template>
  <div id="app">
    <div class="container-fluid" >
      <div class="row">
        <div style="font-weight: bold;" class="m-0 p-0 border-bottom col-lg-12 d-flex align-items-center" v-if="this.isLoggedIn">
            <div class="px-3 m-0">
                <router-link to="/"><h1 class="my-2">EClass</h1></router-link>
            </div>
            <div class="col m-0 text-right">
                <button type="button" class="border-0 bg-white font-weight-bold">Log Out</button>
            </div>
        </div>
        <div class="col-12 col-sm-2 p-0 bg-primary" v-if="this.isLoggedIn">
          <div class="list-group mt-3" id="list-tab" role="tablist">
            <router-link to="/" style="font-size: 25px;" class="list-group-item list-group-item-action border-0 bg-primary text-white rounded-0"><h5 class="m-0 font-weight-bold">Upload Course</h5></router-link>
            <router-link to="/category"  style="font-size: 25px;" class="list-group-item list-group-item-action border-0 bg-primary text-white rounded-0"><h5 class="m-0 font-weight-bold">Categories</h5></router-link>
            <router-link to="/user"  style="font-size: 25px;"  class="list-group-item list-group-item-action border-0 bg-primary text-white rounded-0"><h5 class="m-0 font-weight-bold">User</h5></router-link>
          </div>
        </div>
        <router-view/>
      </div>
    </div>
  </div>
</template>

<script>
  
  export default {
    name: 'app',
    data() {
      return {
        isLoggedIn: true
      }
    },
    methods: {
      clone(arr){
        return JSON.parse(JSON.stringify(arr));
      }
    }
  }

</script>