<template>
	<div class="tab-content">
		<div class="tab-pane fade show active">
	      <form class="py-3 text-right">
	        <div>
	          <input class="border shadow-none p-2 col-6 " type="text" placeholder="Find a User" id="myInput" v-on:keyup="myfunction">
	          <i class="fas fa-search"></i>
	        </div>
	      </form>
	      <table class="table table-bordered m-0" id="myTable">
	        <thead class="bg-light">
	            <tr>
	              <th class="text-center" scope="col">NO</th>
	              <th class="text-center" scope="col">Username</th>
	              <th class="text-center" scope="col">Fullname</th>
	              <th class="text-center" scope="col">Email</th>
	              <th class="text-center" scope="col">Active/Deactive</th>
	            </tr>
	        </thead>
	        <tbody>
	            <tr class="p-0" v-for="data in dataJadi">
	              <th class="text-center">{{data.length}}</th>
	              <td>{{data.username}}</td>
	              <td>{{data.fullname}}</td>
	              <td>{{data.email}}</td>
	              <td class="text-center py-1"><button type="button" class="btn btn-success col-8 " v-model="activ" id="change">{{data.active}}</button></td>
	            </tr>
	        </tbody>
	      </table>
		</div>
	</div>
</template>
<script>
	import axios from 'axios'
	export default {
		data() {
			return {
				url : 'http://192.168.2.231:3000/v1/users',
				dataMentah: [],
				dataJadi:[],
				activ: '',
				classObject: {
					active: true,
					'btn btn-success col-12': true
				},
				activated: 'btn btn-success col-12',
				deactived: 'btn btn-danger col-12'
			}
		},
		mounted() {
			var self = this
			axios.get(this.url).then(response=>{
				if(response.status == 200){
					console.log(response.data.usersData)
					self.dataMentah.push(response.data.usersData)
					self.dataMentah.map(r=>{
						r.map(a=>{
						self.dataJadi.push(a.userData)
						})
					})
				}

				this.dataJadi.map(maut=> {
					if(maut.active == true){
						maut.active = "Active"
					}else {
						maut.active = "Deactive"
					}
				})
			})
			console.log('oke', this.dataJadi)
		},
		methods: {
			myfunction() {
				var input, filter, table, tr, td, i;
				input = document.getElementById("myInput");
				filter = input.value.toUpperCase();
				table = document.getElementById("myTable");
				tr = table.getElementsByTagName("tr");
				for (i = 0; i < tr.length; i++) {
					td = tr[i].getElementsByTagName("td")[0];
					if (td) {
			    		if (td.innerHTML.toUpperCase().indexOf(filter) > -1) {
			    		tr[i].style.display = "";
			    	} else {
			    		tr[i].style.display = "none";
			    	}
				}       
			  }
			}
		}
	}
	
</script>