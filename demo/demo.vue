<template>
	<div class="demo-marengo">
		<demo :action="test" :submit="submit"/>
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
			},
			submit(e, value, ready) {
				console.log(e, value)
			}
		}
	}
</script>
<style>
	div.demo-marengo {
		padding: 15px;
	}
</style>