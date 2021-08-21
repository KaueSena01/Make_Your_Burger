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
		color: #fff;
    	background-color: #58c75d;
    	border: 2px solid #b8daff;
		border-radius: 5px;
		padding: 10px;
		max-width: 420px;
		margin: 30px auto;
	}
</style>