<template>
	<div id="nav">
		
    	<router-link to="/">Home</router-link>
    	<router-link to="/Pedidos">Pedidos</router-link>

  </div>
</template>

<script>
	export default {
		name: "Navbar",
		props: ["logo", "alt"]
	}
</script>
	
<style scoped>
	#nav{
		background-color: #232323;
		border-bottom: 4px solid #fa8511;
		padding: 15px 25px;
		display: flex;
		align-content: center;
		/*justify-content: flex-end;*/
	}
 	#nav #logo_url{
 		margin: auto;
 		margin-left: 0;
 	}
 	#logo{
 		width: 40px;
 		height: 40px;
 	}
 	#nav a{
 		color:  #fff;
 		text-decoration: none;
 		margin: 12px;
 		transition: .5s;
 		font-weight: normal;
 		font-family: 'Poppins';
 	}
 	#nav a:hover{
 		color:  #fa8511;
 	}
</style>