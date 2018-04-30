<template>
	<div class="demo-marengo">
		<demo :action="test"/>
	</div>
</template>
<script>
	import Demo from 'demo-component'
	export default {
		components: {
			Demo
		},
		methods: {
			test(value) {
				console.log(value)
			}
		}
	}
</script>
<style>
	div.demo-marengo {
		padding: 15px;
	}
</style>