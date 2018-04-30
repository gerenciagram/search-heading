<template>
	<div class="search-heading d-flex align-items-center justify-content-between flex-nowrap"
	:class="{'search-heading-loading': loading}">
		<form class="w-100">
			<input v-model="input" type="text" class="form-control search-heading-field" :placeholder="`${$trans('search')}...`">
		</form>
		<div>
			<div class="search-heading-button btn btn-primary d-flex flex-nowrap align-items-center position-relative">
				<span class="search-heading-button-ordinary-content mr-2">
					<i class="fas fa-search"></i>
				</span>
				<span class="search-heading-button-ordinary-content">
					<span>{{ $trans('search') }}</span>
				</span>
				<span class="search-heading-button-loading">
					<loading :scale="58"/>
				</span>
			</div>
		</div>
	</div>
</template>

<script>
	/* Marengo */
	import Marengo from 'marengo'
	import config from './config'
	/* Components */
	import Loading from 'pulse-loading'
	/* Body */
	export default Marengo({
		config,
		components: {
			Loading
		},
		props: {
			loading: {
				default: false,
				type: Boolean
			},
			action: {
				default: el => console.log,
				type: Function
			}
		},
		computed: {
			field() {
				return this.$el.querySelector('form input')
			}
		},
		data() {
			return {
				input: null
			}
		},
		updated() {
			this.action(this.field.value, this.field)
		}
	})
</script>

<style lang="scss" scoped>
	.search-heading {
		&-field {
			border-radius: 4px 0 0 4px;
			border-right: none;
			&:focus {
				box-shadow: none;
			}
		}
		&-button {
			border-radius: 0 4px 4px 0;
		}
		&-field,
		&-button {
			padding: 0.575rem 1.00rem;
		}
		&-button-loading {
			position: absolute;
			left: 50%;
			top: 50%;
			transform: translate(-50%, -50%);
			opacity: 0;
			pointer-events: none;
		}		
	}
	.search-heading-loading {
		.search-heading-button-ordinary-content {
			opacity: 0;
			pointer-events: none;
		}
		.search-heading-button-loading {
			opacity: 1;
		}
	}
</style>
