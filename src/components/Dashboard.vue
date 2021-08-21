<template>
	<div id="burger-table">
		<Message :msg="msg" v-show="msg"/>
		<div>
			<div id="burger-table-heading">
				<div class="order-id">#</div>
				<div>Cliente:</div>
				<div>Pão:</div>
				<div>Carne:</div>
				<div>Ações:</div>
			</div>
		</div>

		<div id="burger-table-rows">
			<div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
				<div class="order-number">{{burger.id}}</div>
				<div>{{burger.nome}}</div>
				<div>{{burger.pao}}</div>
				<div>{{burger.carne}}</div>
				<div>
				<select name="status" class="status" @change="updateBuger($event, burger.id)">
						<option value="">Selecione</option>
						<option v-for="s in status" :key="s.id" :value="s.tipo" 
						:selected="burger.status == s.tipo">
							{{ s.tipo }}
						</option>
					</select>
					<button class="delete-btn" @click="deleteBuger(burger.id)">Cancelar</button>
				</div>
			</div>
		</div>
	</div>
</template>
<script>

import Message from './Message.vue';

export default{
	name: "Dashboard",
	components: {
		Message
	},
	data() {
		return {
			burgers: null,
			burger_id: null,
			status: [],
			msg: null
		}
	},
	methods: {
		async getPedidos() {

			const req = await fetch("http://localhost:3000/burgers");
			const data = await req.json();
			this.burgers = data;

			console.log(this.burgers);

			// Resgatanto os status

			this.getStatus();
		},

		async getStatus() {

			const req = await fetch("http://localhost:3000/status");
			const data = await req.json();
			this.status = data;

		},

		// Deletando
		async deleteBuger(id) {

			const req = await fetch(`http://localhost:3000/burgers/${id}`,{
				method: "DELETE"
			});

			const res = await req.json();

			// Mensagem do sistema
			this.msg = "Pedido removido com sucesso!";

			// Limpar msg
			setTimeout(() => this.msg = "", 5000);

			this.getPedidos();
		},

		async updateBuger(event, id) {
			const option = event.target.value;
			const dataJson = JSON.stringify({status: option});

			const req = await fetch(`http://localhost:3000/burgers/${id}`, {
				method: "PATCH",
				headers: {"Content-Type": "application/json" },
				body: dataJson
			});

			const res = await req.json();

			// Mensagem do sistema
			this.msg = `O pedido foi atualizado para ${res.status}!`;

			// Limpar msg
			setTimeout(() => this.msg = "", 5000);

			console.log(res);
		}
	},
	mounted() {
		this.getPedidos(); // Monta o metodo
	}
}
</script>
<style scoped>
	#buger-table{
		max-width: 1200px;
		margin: 0 auto;
	}
	#burger-table-heading,
	#burger-table-rows,
	.burger-table-row{
		display: flex;
		flex-wrap: wrap;
	}
	#burger-table-heading{
		font-family: 'Poppins';
		font-weight: bold;
		padding: 12px;
		border-bottom: 3px solid #333;
	}
	#burger-table-heading div,
	.burger-table-row div{
		width: 16%;
		font-family: 'Poppins';
	}
	.burger-table-row{
		width: 100%;
		padding: 12px;
		border-bottom: 1px solid #ccc;
	}
	#burger-table-heading .order-id,
	#burger-table-row .order-number{
		font-family: 'Poppins';
		width: 16%;
	}
	select{
		padding: 5px;
		margin-right: 12px;
		float: left;
		border-radius: 2px;
		font-family: 'Poppins';
	}
	.delete-btn{
		font-family: 'Poppins';
		background-color: #fa8511;
		color: #fff;
		font-weight: bold;
		border: 2px solid orange;
		border-radius: 2px;
		padding:4px 10px;
		font-size: 16px;
		margin: 0 auto;
		cursor: pointer;
		transition: .5s;
		position: absolute;
		float: right;
	}
	.delete-btn:hover{
		opacity: 0.8;
		background-color: #fa8511;
		color: #fff;
	}
</style>