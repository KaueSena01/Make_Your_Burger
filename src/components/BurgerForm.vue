<template>
	<div>
		<Message :msg="msg" v-show="msg"/>
		<div>
		 	<form id="burger-form" @submit="creatBurger">
		 	<div class="input-container">
	 			<label for="nome">Nome do cliente</label>
				<input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite seu nome">
		 	</div>
		 	<div class="input-container">
	 			<label for="pao">Escolha o pão</label>
	 			<select name="pao" id="pao" v-model="pao">
	 				<option value="">Selecione o pão</option>
	 				<option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>
	 			</select>
		 	</div>
		 	<div class="input-container">
	 			<label for="carne">Escolha a carne do seu Burger</label>
	 			<select name="carne" id="carne" v-model="carne">
	 				<option value="">Selecione o tipo de carne</option>
	 				<option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
	 			</select>
		 	</div>
		 	<div id="opcionais-container" class="input-container">
	 			<label for="opcionais" id="opcionais-title">Selecione os opcionais:</label>
	 			<div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
	 			<input type="checkbox" name="opcionais" v-model="opcionais" :key="opcional.tipo">
	 			<span>{{ opcional.tipo }}</span>
	 			</div>
		 	</div>

		 	<div class="input-container">
	 			<input type="submit" class="submit-btn" value="Criar meu Burger">
		 	</div>
		 	</form>
		</div>
	</div>
</template>

<script>
import Message from './Message.vue';

	export default{
		name: "BurgerForm",
		components: {
			Message
		},
		data() {
			return{
				paes: null,
				carnes: null,
				opcionaisdata: null,

				nome: null,
				pao: null,
				carne: null,
				opcionais: [],
				msg: null

			}
		},
		methods: {
			async getIngredientes() {
				const req = await fetch("http://localhost:3000/ingredientes");
				const data = await req.json();
				
				this.paes = data.paes;
				this.carnes = data.carnes;
				this.opcionaisdata = data.opcionais;
			},
			async creatBurger(e) { // e-> Argumento de evento
				e.preventDefault();

				// Criando variavel e o que ela deve receber

				const data = {
					nome: this.nome,
					carne: this.carne,
					pao: this.pao,
					opcionais: Array.from(this.opcionais),
					status: "Solicitado"
				}

				const dataJson = JSON.stringify(data);  // Transformando dado em Json

				const req = await fetch("http://localhost:3000/burgers", {
					method: "POST",
					headers: {"Content-Type": "application/json"}, // -> comunicando com json
					body: dataJson
				});

				const res = await req.json();

				// Mensagem do sistema
				this.msg = "Pedido realizado com sucesso!";

				// Limpar msg
				setTimeout(() => this.msg = "", 5000); // -> 5 segundos para a mensagem apagar
				// A mensagem fica vazia = ""
				// Limpar os campos
				this.nome = "";
				this.carne = "";
				this.pao = "";
				this.opcionais= "";
			}
		},
		mounted() {
			this.getIngredientes();
		}
 	}	
</script>

<style scoped>
	#burger-form{
		width: 320px;
		margin: 0 auto;
	}
	.input-container{
		display: flex;
		flex-direction: column;
		margin-bottom: 20px;
	}
	label{
		font-weight: bold;
		margin-bottom: 15px;
		color: #222;
		padding: 5px 10px;
		border-left: 4px solid #fcba03;
	}
	input, select{
		width: 100%;
		padding: 5px 0px; 
	}

	#opcionais-container{
		flex-direction: row;
		flex-wrap: wrap;
	}
	#opcionais-title{
		width: 100%;
	}
	.checkbox-container{
		display: flex;
		align-items: flex-start;
		width: 50%;
		margin-bottom: 20px;
	}

	.checkbox-container span, .checkbox-container input{
		width: auto;
	}
	.checkbox-container span{
		margin-left: 6px;
		font-weight: bold;
	}
	.submit-btn{
		background-color: #222;
		color: #fcba03;
		font-weight: bold;
		border: 2px solid #222;
		padding: 10px;
		font-size: 16px;
		margin: 0 auto;
		border-radius: 3px;
		cursor: pointer;
		transition: .5s;
	}
	.submit-btn:hover{
		background-color: transparent;
		color: #222;
	}
</style>