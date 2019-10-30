<template>
  <div>
    <div id="header" class="text-center">
      <h1>BlackAssum</h1>
      <h6 class="text-secondary">Gerador de StatupNames Vue.js Node.js GraphQL</h6>
    </div>
    <div id="main">
      <div class="container">
        <div class="row">
          <div class="col-md">
            <h5>
              Prefixos
              <span class="badge badge-info">{{prefixes.length}}</span>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li class="list-group-item" v-for="prefix in prefixes" v-bind:key="prefix">
                    <div class="row">
                      <div class="col">{{ prefix }}</div>
                      <div class="col align-end">
                        <button class="btn btn-info" type="submit">
                          <span class="fa fa-trash"></span>
                        </button>
                      </div>
                    </div>
                  </li>
                </ul>
                <br>
                <div class="input-group">
                  <input @keyup.enter="addPrefix(prefix)" class="form-control" type="text" placeholder="Digite o Prefixo" v-model="prefix"/>
                  <div class="input-group-append">
                    <button type="submit" class="btn btn-info" v-on:click="addPrefix(prefix)">
                      <span class="fa fa-plus"></span>
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="col-md">
            <h5>
              Sufixos
              <span class="badge badge-info">{{sufixes.length}}</span>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li class="list-group-item" v-for="sufix in sufixes" v-bind:key="sufix">
                    <div class="row">
                      <div class="col">{{ sufix }}</div>
                      <div class="col align-end">
                        <button class="btn btn-info" type="submit">
                          <span class="fa fa-trash"></span>
                        </button>
                      </div>
                    </div>
                  </li>
                </ul>
                <br>
                <div class="input-group">
                  <input @keyup.enter="addSufix(sufix)" class="form-control" type="text" name="prefixo" placeholder="Degite o Sufixo" v-model="sufix"/>
                  <div class="input-group-append">
                    <button type="submit" class="btn btn-info" v-on:click="addSufix(sufix)">
                      <span class="fa fa-plus"></span>
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <br />
        <div>
          <h5>
            Domínios
            <span class="badge badge-info">{{domains.length}}</span>
          </h5>
          <div class="card">
            <div class="card-body">
              <ul class="list-group">
                <li class="list-group-item" v-for="domain in domains" v-bind:key="domain.name">
                  <div class="row">
                    <div class="col-md">
                      {{ domain.name }}
                    </div>
                    <div class="col-md align-end">
                      <a class="btn btn-info" :href="domain.url" target="_blank">
                        <span class="fa fa-shopping-cart"></span>
                      </a>
                    </div>
                  </div>
                </li>
              </ul>
            </div>
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

  data: function() {
    return {
      prefix: "",
      sufix: "",
      prefixes: ["Air", "Get", "Flight"],
      sufixes: ["Orbe", "Flut", "Bower"],
    };
  },
  methods: {
    addPrefix(prefix) {
      this.prefixes.push(prefix);
      this.prefix = "";
    },
    addSufix(sufix) {
      this.sufixes.push(sufix);
      this.sufix = "";
    },
    deleteSufix(sufix){
      this.sufixes.splice(this.sufixes.indexOf(sufix), 1)
    }
  },
  computed:{
    domains() {
      console.log("Gerando Domínios...");
      const domains = [];
      for (const prefix of this.prefixes) {
        for (const sufix of this.sufixes) {
          const name = prefix + sufix
          domains.push({
            url : `https://checkout.hostgator.com.br/?a=add&sld=${name.toLowerCase()}&tld=.com`,
            name
          });
        }
      }
      return domains;
    }
  }
};
</script>

<style>
.align-end{
  display: flex;
  justify-content: flex-end;
}
#header {
  margin: 30px;
}
#main {
  background-color: #f1f1f1;
  padding: 30px;
}
</style>
