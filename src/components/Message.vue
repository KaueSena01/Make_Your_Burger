<template>
		<div class="message-container">
			<p>{{ msg }}</p> <!-- -> Imprimindo mensagem do sistema -->
		</div>
</template>

<script>
export default{
	name: "Message",
	props: {// -> passando dados por uma propriedade
		msg: String
}
}
</script>

<style scoped>
	.message-container{
		color: #004085;
		background-color: #cce5ff;
		border: 2px solid #b8daff;
		border-radius: 5px;
		padding: 10px;
		max-width: 305px;
		margin: 30px auto;
	}
</style>