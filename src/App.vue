<template>
  <div>
    <div id="header" class="text-center">
      <h1>Celacanto</h1>
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
                  <li
                    class="list-group-item"
                    v-for="prefix in prefixes"
                    v-bind:key="prefix"
                  >{{ prefix }}</li>
                </ul>
                <input
                  class="form-control"
                  type="text"
                  name="prefixo"
                  placeholder="Degite o prefixo"
                />
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
                  <li
                    class="list-group-item"
                    v-for="sufix in sufixes"
                    v-bind:key="sufix"
                  >{{ sufix }}</li>
                </ul>
                <input
                  class="form-control"
                  type="text"
                  name="prefixo"
                  placeholder="Degite o Sufixo"
                />
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
                <li
                  class="list-group-item"
                  v-for="domain in domains"
                  v-bind:key="domain"
                >{{ domain }}</li>
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
      prefixes: ["Air", "Get", "Flight"],
      sufixes: ["Orbe", "Flut", "Bower"],
      domains: ["AirFlut", "GetBower", "FlightOrbe"]
    };
  }
};
</script>

<style>
#header {
  margin: 30px;
}
#main {
  background-color: #f1f1f1;
  padding: 30px;
}
</style>
