<template>
  <div>
    <div id="main">
      <div class="container">
        <div class="row">
          <div class="col-md">
            <AppItemList title="Prefixos" v-bind:items="prefixes" v-on:addItem="addPrefix" v-on:deleteItem="deletePrefix"/>
          </div>
          <div class="col-md">
            <AppItemList title="Sufixos" v-bind:items="sufixes" v-on:addItem="addSufix" v-on:deleteItem="deleteSufix"/>
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
import AppItemList from './AppItemList';
export default {
  name: "app",
  components: {
    AppItemList
  },
	data: function(){
		return {
			prefixes: ["Air", "Jet", "Flight"],
			sufixes: ["Hub", "Station", "Mart"],
		};
	},
	methods: {
		addPrefix(prefix) {
			this.prefixes.push(prefix);
		},
		addSufix(sufix){
			this.sufixes.push(sufix);
		},
		deletePrefix(prefix){
			this.prefixes.splice(this.prefixes.indexOf(prefix), 1);
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
