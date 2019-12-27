<template>
  <div>
    <div id="slogan" class="text-center">
      <h1>Namegator</h1>
      <br />
      <h6 class="text-secondary">Gerador de nomes utilizando Vue.js, GraphQl e Node</h6>
    </div>
    <div id="main">
      <domain-list />
    </div>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";
import DomainList from "./components/DomainList";

export default {
	name: "namegator",
	components: {
		DomainList
	},
};
</script>
<style>
#slogan {
  margin: 30px 0;
}

#main {
  background-color: #f1f1f1;
  padding: 30px 0;
}
</style>
