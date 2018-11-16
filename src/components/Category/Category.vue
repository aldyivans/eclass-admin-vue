<template>
	<div class="col-12 col-sm-5 m-5">
		<form class="border mb-2" v-for="(category, index) in categories">
			<div class="form-group p-4 border-bottom m-0">
		    <label>Category</label>
		    <input type="text" class="form-control" v-model="category.categoryName">
		  </div>
		  <div class="form-group p-4 border-bottom m-0">
		  	<label class="m-0">Sub-Category</label>
	  		<div class="border-bottom mb-3" v-for="subCategory in categories[0].subCategoryInput">
				  <input type="text" class="form-control mt-3" v-model="subCategory.subCategory">
			  	<div class="row">
			  		<div class="col-md-6 pt-2" v-for="(topic, i) in subCategory.topics">
						  <input type="text" class="form-control" placeholder="Topic" v-model="subCategory.topics[i]">
			  		</div>
		  		</div>
			    <button class="btn bg-white text-primary font-weight-bold m-0 mt-3" type="button" v-on:click="addTopic(subCategory.topics)">+ add topic</button>
		  	</div>
	  		<button class="btn btn-primary font-weight-bold m-0" type="button" v-on:click="addSubCategory">+ add sub-category</button>
			</div>
		</form>
		<button type="button" class="btn btn-primary font-weight-bold" v-on:click="saveCategory">save</button>
		<button type="button" class="btn btn-danger font-weight-bold" v-on:click="resetForm">reset</button>
	</div>
</template>

<script>

import axios from 'axios'
import App from '../../App.vue'

const initialCategories = [
				{
					categoryName: 'JS',
					subCategoryInput: [
						{
							subCategory: "Sub A",
							topics: ["Topic A", "Topic B"]
						}
					],
					topicInput: [{
						topic: ""
					}]
				}
			];

export default {
	data() {
		return {
			categories: []
		}
	},
	mounted(){
		this.categories = App.methods.clone(initialCategories);
	},
	methods: {
		addSubCategory() {
			this.categories[0].subCategoryInput.push({
				subCategory:"New Sub-Category",
				topics: ["New Topic"]
			})
		},
		addTopic(container) {
			container.push("New Topic")
		},
		saveCategory() {
			let self = this;
			console.log(this.categories)

			// post to backend
			setTimeout(function(){
				self.resetForm();
			}, 1000)
		},
		resetForm(){
			console.log('reset')
			this.categories = initialCategories
			console.log(this.categories)
		}
	}
}

</script>

