<template> 
	<div> 
		<form @submit.prevent="addItem"> 
			<input v-model="newItem"
				placeholder="Enter item..."> 
			<button>Add Item</button> 
		</form> 
		<ul> 
			<li v-for="(item, index) in items"
				:key="index"> 
				{{ item }} 
				<button @click="removeItem(index)"> 
					Remove 
				</button> 
			</li> 
		</ul> 
	</div> 
</template> 

<script> 
	export default { 
		data() { 
			return { 
				newItem: '', 
				items: [], 
			}; 
		}, 
		computed: { 
			itemsFromLocalStorage() { 
				return JSON.parse(localStorage.getItem('items') || '[]'); 
			}, 
		}, 
		watch: { 
			items(newItems) { 
				localStorage.setItem('items', JSON.stringify(newItems)); 
			}, 
		}, 
		methods: { 
			addItem() { 
				this.items.push(this.newItem); 
				this.newItem = ''; 
			}, 
			removeItem(index) { 
				this.items.splice(index, 1); 
			}, 
		}, 
		created() { 
			this.items = this.itemsFromLocalStorage; 
		}, 
	}; 
</script>
