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
                  <input type="text" class="form-control" placeholder="Digite o Prefixo">
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
                  <input type="text" class="form-control" placeholder="Digite o Sufixos">
                </div>
            </div>
          </div>
        </div>
        <br>
        <h5>Domínios <span class="badge badge-info">{{ domains.length }}</span></h5>
        <div class="card">
          <div class="card-body">
            <ul class="list-group">
              <li class="list-group-item" v-for="domain in domains" v-bind:key="domain">{{ domain }}</li>
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
			prefixes: ["Air", "Jet", "Flight"],
			sufixes: ["Hub", "Station", "Mart"],
			domains: ["Airhub", "AirStation", "AirMart", "JetHub", "JetStation", "JetMart", "FlightHub", "FlightStation", "FlightMart"]
		};
	}
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
