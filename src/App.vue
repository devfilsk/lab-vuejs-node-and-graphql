<template>
  <div>
    <div id="slogan" class="text-center">
      <h1>NameGator</h1>
      <br/>
      <h6 class="text-secondary">Gerador de nomes de dominios com Vue.js, GraphQL e Node.js</h6>
    </div>
    <div id="main">
      <div class="container">
        <div class="row">
          <div class="col-md">
            <h5>Prefixos <span class="badge badge-info">{{ prefixes.length }}</span></h5>
            <div class="card">
                <div class="card-body">
                  <ul class="list-group">
                    <li class="list-group-item" v-for="prefix in prefixes" v-bind:key="prefix">
                      {{ prefix }}
                    </li>
                  </ul>
                  <br>
                  <div class="input-group">
                    <input type="text" class="form-control" placeholder="Digite o Prefixo" v-model="prefix" v-on:keyup.enter="addPrefix(prefix)">  
                    <div class="input-group-append">
                      <button class="btn btn-info" v-on:click="addPrefix(prefix)"><span class="fa fa-plus"></span></button>
                    </div>                  
                  </div>
                </div>
            </div>
          </div>
          <div class="col-md">
            <h5>Sufixos <span class="badge badge-info">{{ sufixes.length}}</span></h5>
            <div class="card">
                <div class="card-body">
                  <ul class="list-group">
                    <li class="list-group-item" v-for="sufixe in sufixes" v-bind:key="sufixe">
                      {{ sufixe }}
                    </li>
                  </ul>
                  <br>
                  <div class="input-group">
                    <input type="text" class="form-control" placeholder="Digite o Sufixos" v-model="sufix" v-on:keyup.enter="addSufix(sufix)">
                    <div class="input-group-append">
                      <button class="btn btn-info" v-on:click="addSufix(sufix)"><span class="fa fa-plus"></span></button>
                    </div>                  
                  </div>
                </div>
            </div>
          </div>
        </div>
        <br>
        <h5>Domínios <span class="badge badge-info">{{ domains.length }}</span></h5>
        <div class="card">
          <div class="card-body">
            <ul class="list-group">
              <li class="list-group-item" v-for="domain in domains" v-bind:key="domain">
                <div class="row">
                  <div class="col-md">
                    {{ domain }} 
                  </div>
                  <div class="col-md">
                    <button class="btn btn-">
                      <span class="fa fa-shopping-cart"></span></button>
                  </div>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";

export default {
	name: "app",
	data: function(){
		return {
			prefix: "",
			sufix: "",
			prefixes: ["Air", "Jet", "Flight"],
			sufixes: ["Hub", "Station", "Mart"],
		};
	},
	methods: {
		addPrefix(prefix) {
			this.prefixes.push(prefix);
			this.prefix = "";
		},
		addSufix(sufix){
			this.sufixes.push(sufix);
			this.sufix = "";
		},
		deleteSufix(sufix){
			this.sufixes.splice(this.sufixes.indexOf(sufix), 1);
		},
	},
	computed: {
		domains(){
			const domains = [];
			for(const prefix of this.prefixes){
				for(const sufix of this.sufixes){
					domains.push(prefix + sufix);
				}
			}
			return domains;
		}
	},
	// metodo chamado assim que o elemento é criado
	// created() {
	// 	this.domains = this.generate();
	// }
};
</script>

<style>
  #slogan {
    margin-top: 30px;
    margin-bottom: 30px;
  }
  #main{
    background-color: #F1F1F1;
    padding-top: 30px;
    padding-bottom: 30px;
  }
</style>
