<script>
import axios from 'axios';

export default {
	name: "Beer",
	data() {
		return {
			beerInfo: [],
			errors: [],
			async retryBeer(){
				let response = await axios.get("https://random-data-api.com/api/beer/random_beer");
				this.beerInfo = await response.data;
			},
		};
	},
	async created(){
		let response = await axios.get("https://random-data-api.com/api/beer/random_beer");
		this.beerInfo = await response.data;
	},
}
</script>

<template>
	<div class="main">
		<div class="interface-block">
			<div class="text-block-beer">
				<h1 class="text">Beer for you - {{ beerInfo.brand }}!</h1>
				<p class="text">Name: {{ beerInfo.name }}</p>
				<p class="text">Style: {{ beerInfo.style }}</p>
				<p class="text">Hop: {{ beerInfo.hop }}</p>
				<p class="text">Yeast: {{ beerInfo.yeast }}</p>
				<p class="text">Malts: {{ beerInfo.malts }}</p>
				<p class="text">IBU: {{ beerInfo.ibu }}</p>
				<p class="text">Alcohol: {{ beerInfo.alcohol }}</p>
				<p class="text">Blg: {{ beerInfo.blg }}</p>
				<div class="button-block">
					<button class="retry" @click="retryBeer">Want more?</button>
				</div>
			</div>
		</div>
	</div>
</template>

<style>
</style>