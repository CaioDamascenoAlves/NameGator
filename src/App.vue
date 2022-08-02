<template>
	<div >
		<div id="slogan" class="text-center">
			<h1>NameGator</h1>
			<br>
			<h6 class="text-secundary">
				Gerador de nomes Vue.js, GraphQl & NodeJS
			</h6>
		</div>
		<div id="main">
			<div class="conteiner">
				<div class="row">
					<div class="col-md">
						<h5>Prefixos <span class="badge text-bg-primary">{{prefixes.length}}</span></h5>
						<div class="card">
							<div class="card-body">
								<ul class="list-group">
									<li class="list-group-item" v-for="prefix in prefixes" v-bind:key="prefix">
										{{prefix}}
									</li>
								</ul>
								<br>
								<div class="input-group">
									<input class="form-control" type="text" v-model="prefix" v-on:keyup.enter="addPrefix(prefix)" placeholder="Digite o prefixo">		
									<div class="input-group-append">
										<button class="btn btn-success" v-on:click="addPrefix(prefix)"><span class="fa fa-plus"></span></button>
									</div>
								</div>
							</div>
						</div>		
					</div>
					<div class="col-md">
						<h5>Sufixos <span class="badge text-bg-primary">{{sufixes.length}}</span></h5>
						<div class="card">
							<div class="card-body">
								<ul class="list-group">
									<li class="list-group-item" v-for="sufix in sufixes" v-bind:key="sufix">
										{{sufix}}
									</li>
								</ul>
								<br>
								<div class="input-group">
									<input class="form-control" type="text"  v-model="sufix" v-on:keyup.enter="addSufix(sufix)" placeholder="Digite o sufixo">		
									<div class="input-group-append">
										<button class="btn btn-success" v-on:click="addSufix(sufix)"><span class="fa fa-plus"></span></button>
									</div>
								</div>
							</div>
						</div>
					</div>
				</div>
				<br>
				<h5>Domínios <span class="badge text-bg-primary">{{domains.length}}</span></h5>
				<div class="card">
					<div class="card-body">
						<ul class="list-group">
							<li class="list-group-item" v-for="domain in domains" v-bind:key="domain">
								{{domain}}
							</li>
						</ul>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
  name: 'App',
  data: function () {
	return{
		prefix: "",
		sufix: "",
		prefixes: ['Air', 'Jet', 'Flight'],
		sufixes: ['Hub', 'Station', 'Mart'],
		domains: ['AirHub', 'AirStation', 'AirMart', 'JetHub', 'JetStation', 'JetMart', 'FlightHub', 'FlighStation', 'FlightMart'],
	}
  },
  methods: {
	addPrefix(prefix){
		this.prefixes.push(prefix);
		this.prefix = "";
		this.generate();
	},
	addSufix(sufix) {
		this.sufixes.push(sufix);
		this.sufix = "";
		this.generate();
	},
	generate(){
		this.domains = [];
		for(const prefix of this.prefixes){
			for(const sufix of this.sufixes)
			this.domains.push( prefix + sufix );
		}
	}
  }
}
</script>

<style>
#slogan {
	margin: 30px;
}
#main {
	background-color: #f1f1f1;
	padding: 30px;
}
</style>
