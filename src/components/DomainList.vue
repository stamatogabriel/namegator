<template>
  <div>
    <div id="main">
      <div class="container">
        <div class="row">
          <div class="col-md">
            <app-item-list v-bind:items="prefixes" v-on:addItem="addPrefix" v-on:deleteItem="deletePrefix" title="Prefixos" />
          </div>
          <div class="col-md">
            <app-item-list v-bind:items="sufixes" v-on:addItem="addSufix" v-on:deleteItem="deleteSufix" title="Sufixos" />
          </div>
        </div>
        <br />
        <h5>
          Domains
          <span class="badge badge-info">{{domains.length}}</span>
        </h5>
        <div class="card">
          <div class="card-body">
            <ul class="list-goup">
              <li class="list-group-item" v-for="domain in domains" v-bind:key="domain.name">
                <div class="row">
                  <div class="col-md">{{domain.name}}</div>
                  <div class="col-md text-right">
                    <a class="btn btn-info" :href="domain.checkout" target="_blank">
                      <span class="fa fa-shopping-cart" />
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
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";
import AppItemList from "./AppItemList";

export default {
	name: "namegator",
	data: function() {
		return {
			prefixes: ["Air", "Jet", "Fly"],
			sufixes: ["Hub", "Station", "Mart"]
		};
	},
	components: {
		AppItemList
	},
	computed: {
		domains() {
			const domains = [];
			for (const prefix of this.prefixes) {
				for (const sufix of this.sufixes) {
					const name = prefix + sufix;
					const checkout = `https://checkout.hostgator.com/?a=add&sld=${name.toLowerCase()}&tld=.com.br`;
					domains.push({ name, checkout });
				}
			}
			return domains;
		}
	},
	methods: {
		addPrefix(prefix) {
			this.prefixes.push(prefix);
		},
		deletePrefix(prefix) {
			this.prefixes.splice(this.prefixes.indexOf(prefix), 1);
		},
		addSufix(sufix) {
			this.sufixes.push(sufix);
		},
		deleteSufix(sufix) {
			this.sufixes.splice(this.sufixes.indexOf(sufix), 1);
		}
	}
};
</script>
<style>

</style>
