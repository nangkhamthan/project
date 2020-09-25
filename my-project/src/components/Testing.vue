<template>

	<div>
		<h1 class="text-danger text-center">This is testing component</h1>
	<p class="text-center">{{name}}</p>
	<div>
	<p v-for="(row,index) in info" :key="index" class="text-center">
	{{row.description}}:<span v-html="row.symbol"></span>{{row.rate_float}}
	</p>
	</div>

	</div>	
</template>
<script type="text/javascript">

	export default{
		data(){
			return{
				name: 'nang kham than',
				info: null
			}
		},
		mounted(){
			this.showData();
		},
		methods:{
			showData(){
			this.$http.get('https://api.coindesk.com/v1/bpi/currentprice.json').then(response=>{this.info=response.data.bpi})
			}
		},
		filters: {currencydecimal (value) {return value.toFixed(2)}
		}
	}
	
</script>
<style type="text/css">

	
</style>