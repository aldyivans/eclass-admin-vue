<template>
	<div class="col-12 col-sm-5 m-5">
		<form>
			<div class="form-group">
		    <input type="file" class="d-none" ref="upload">
		    <div style="height:300px" class="w-100 bg-light justify-content-center align-items-center d-flex border" v-on:click="choose">
		    	<h4>add a thumbnail</h4>
				</div>
			</div>
		  <div class="form-group">
		    <label for="exampleInputEmail1" class="font-weight-bold">Title</label>
		    <input type="text" class="form-control" aria-describedby="emailHelp">
		  </div>
		  <div class="form-group">
		    <label for="exampleInputEmail1" class="font-weight-bold">Sub-Title</label>
		    <input type="text" class="form-control" aria-describedby="emailHelp">
		  </div>
		  <div class="form-group">
		    <label for="exampleInputEmail1" class="font-weight-bold">Descriptions</label>
		    <input type="text" class="form-control" aria-describedby="emailHelp">
		  </div>
		  <div class="form-group">
		    <label for="exampleInputEmail1" class="font-weight-bold">Instructor(s)</label>
		    <input type="text" class="form-control mb-2" aria-describedby="emailHelp">
		    <input type="text" class="form-control" aria-describedby="emailHelp">
		  </div>
		  <div class="form-group">
		    <label for="exampleInputEmail1" class="font-weight-bold">Categories</label>
		    <select class="custom-select">
				  <option selected>Open this select menu</option>
				  <option value="1">One</option>
				  <option value="2">Two</option>
				  <option value="3">Three</option>
				</select>
		  </div>
		  <div class="form-group">
		  	<label for="exampleInputEmail1" class="font-weight-bold">Banner</label>
		    <div class="input-group mb-3">
				  <div class="custom-file">
				    <input type="file" class="custom-file-input" id="inputGroupFile01" aria-describedby="inputGroupFileAddon01">
				    <label class="custom-file-label" for="inputGroupFile01">Choose file</label>
				  </div>
				</div>
		    <textarea class="form-control" id="exampleFormControlTextarea1" rows="3" placeholder="Banner Descriptions"></textarea>
		  </div>
		  <div class="form-group">
		  	<div class="border p-3">
		  		<input type="text" class="form-control" aria-describedby="emailHelp" placeholder="Section Title">
		  		<hr class="w-100">
			    <label for="exampleInputEmail1" class="font-weight-bold">Content</label>
			    <input type="text" class="form-control mb-2" aria-describedby="emailHelp" placeholder="Order Number">
			    <input type="text" class="form-control mb-2" aria-describedby="emailHelp" placeholder="Title">
			    <input type="text" class="form-control mb-2" aria-describedby="emailHelp" placeholder="URL">
			    <button type="button" class="btn btn-primary">+ add more content</button>
		  	</div>
		  	<button type="button" class="btn btn-primary w-100 rounded-0">+ add more section</button>
		  </div>
		  <button type="button" class="btn btn-primary rounded-0 font-weight-bold">SUBMIT</button>
		</form>
	</div>
</template>

<script>

import axios from 'axios'

export default {
	data() {
		return {
			course: {
				thumbnail: '',
				title: '',
				subtitle: '',
				descriptions: '',
				instructors: [],
				categories: '',
				banner: '',
				bannerDesc: '',
				section: {
					title: '',
					Content: {
						orderNumber: '',
						Title: '',
						URL: ''
					}
				}
			}
		}
	},
	methods: {
		choose() {
			this.$refs.upload.click()
		}
	}
}

</script>
