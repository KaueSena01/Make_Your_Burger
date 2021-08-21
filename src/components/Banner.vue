<template>
	<div id="main-banner">
		<h1>Make Your Buguer</h1>
	</div>	

</template>

<script>
	export default{
		name: "Banner"
	}
</script>

<style scoped>
	
	#main-banner{
		background-image: url('/img/burger.jpg');
		background-position: 0 -250px;
		background-size: cover;
		height: 500px;
		display: flex;
		align-items: center;
		justify-content: flex-start;
		border-bottom: 4px solid #fa8511;
	}
	#main-banner h1{
		font-family: 'Poppins';
		color: #fa8511;
		text-align: center;
		font-size: 60px;
		background-color: #232323;
		padding: 20px 40px;
		border: 2px solid #fa8511;
		border-top-right-radius: 5px;
		border-bottom-right-radius: 5px;
		margin-left: -15px;
		cursor: default;
	}

</style>