<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    Manual Control
    <div class="input m-4">
      Teebox
      <toggle-button
        class="mb-3"
        v-model="gpu"
        :value="false"
        color="#AE41A7"
        :sync="true"
        :width="65"
        :labels="{ checked: 'ON', unchecked: 'OFF' }"
      />
      Greens <label></label>

      <toggle-button
        class="mb-3"
        v-model="cpu"
        :value="false"
        color="#AE41A7"
        :sync="true"
        :width="65"
        :labels="{ checked: 'ON', unchecked: 'OFF' }"
      />
    </div>
    <div class="input m-4">
      Fairways
      <toggle-button
        class="mb-3"
        v-model="fairw"
        :value="false"
        color="#AE41A7"
        :sync="true"
        :width="65"
        :labels="{ checked: 'GPU', unchecked: 'CPU' }"
      />
      <div id="example-1">
        <button id="x-3" v-on:click="onSubmit">Add connection</button>

        <div v-if="status == 'done'">
          <p>connected {{ status }} To {{ answer }}.</p>
        </div>
      </div>
    </div>

    <table id="demo-table-id" class="table table-striped">
      <caption></caption>
      <thead>
        <tr>
          <th>Hole</th>
          <th>Fairway</th>
          <th>Greens</th>
          <th>Teebox</th>
          <th>Roughs</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>
            <input type="checkbox" id="checkbox" v-model="checked" />
            <label for="checkbox">{{ checked }}</label
            >- Disable if it WILL rain
          </td>
          <td><button type="button" class="btn btn-primary">minute</button></td>
          <td>
            <button type="button" class="btn btn-success">minutes</button>
          </td>
          <td><button type="button" class="btn btn-info">minutes</button></td>
          <td><button type="button" class="btn btn-info">minutes</button></td>
        </tr>

        <tr v-for="(row, idx) in rowsa" :key="idx">
          <td >{{ row["Hole"] }} </td>
          <td>{{ row["Fairway"] }}</td>
          <td>{{ row["Greens"] }}</td>
          <td>{{ row["Teebox"] }}</td>
          <td>{{ row["Roughs"] }}</td>
        </tr>
        <tr class="info">
          <td colspan="4"></td>
          <td>
            <b></b>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { ToggleButton } from "vue-js-toggle-button";
import axios from "axios";

//import { ref } from '@vue/composition-api';

export default {
  name: "HelloWorld",
  props: {
    //rows: rows,
    msg: String,
    api_endpoint_cpu: {
      type: String,
      default: "http://localhost:8081/api",
    },
    api_endpoint_gpu: {
      type: String,
      default: "https://mocki.io/v1/4b04474f-5f43-46bd-8376-cf8d48f669a2",
    },
    queries_examples: {
      type: Array,
      default: function () {
        return [
          "What is artificial intelligence?",
          "What is natural language processing?",
        ];
      },
    },
  },
  components: {
    ToggleButton,
  },
  data() {
    return {
      gpu: false,
      fairw: false,
      cpu: false,
      green: false,
      checked: false,
      status: "",
      answer: "",
      courses: null,
      plans: [],
      responseA: [],
      rowsa: [],
      data: null,
      plansz: [
        { fields: { Hole: 2, Fairway: 9 } },
        { fields: { Hole: 13, Fairway: 10 } },
        { fields: { Hole: 15, Fairway: 10 } },
        { fields: { Hole: 4, Fairway: 10 } },
        { fields: { Hole: 8, Fairway: 11 } },
        { fields: { Hole: 1, Fairway: 10 } },
        { fields: { Hole: 9, Fairway: 8 } },
        { fields: { Hole: 12, Fairway: 12 } },
        { fields: { Hole: 18, Fairway: 8 } },
        { fields: { Hole: 14, Fairway: 10 } },
        { fields: { Hole: 6, Fairway: 10 } },
        { fields: { Hole: 10, Fairway: 10 } },
        { fields: { Hole: 7, Fairway: 10 } },
        { fields: { Hole: null, Fairway: 9 } },
        { fields: { Hole: 17, Fairway: 11 } },
        { fields: { Hole: 5, Fairway: 10 } },
        { fields: { Hole: 16, Fairway: 10 } },
        { fields: { Hole: 3, Fairway: 12 } },
      ],
    };
  },
  created: function () {
    axios
      .get("https://mocki.io/v1/4b04474f-5f43-46bd-8376-cf8d48f669a2")
      .then((res) => {
        this.courses = res.data;
      });
    //   this.loadPlan();
  },
  mounted: function () {
    //this.loadPlan();
    this.fetchPlan();
  },
  methods: {
    fetchPlan() {
      const query = `{
                    queryWaterplan{
                         records{
                             fields{
                               Hole 
                               Fairway 
                               Greens
                               Teebox
                               Roughs
                             } 
                         }
                    }
                 }`;

      try {
        fetch("https://shima.stepzen.net/api/airtable/__graphql", {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
            Authorization:
              "apikey shima::stepzen.net+1000::6c712fbd4771efa8bb73e003d39d39b530b2645e6993693797f9393b18009e0e",
          },
          body: JSON.stringify({
            query:
              "{queryWaterplan{records{fields{Hole Fairway Greens Teebox Roughs} }  }}",
          }),
        })
          .then((response) => response.json())
          .then((res) => {
            this.responseA = res.data;
            this.mapToRows();
          })
          .then((data) => {
            console.log("Success:", data);
            //responseA.value = response.data.data.queryWaterplan.records.map(records => records.fields)

            //  console.log(responseA);
          });
      } finally {
        console.log(query);
      }
    },

    mapToRows() {
      this.rowsa = this.responseA.queryWaterplan.records // <- this is an Array
        // and map each edge into its node attribute
        .map((records) => records.fields); //
      console.log(this.rowsa);
    },
    loadPlan: function () {
      // Get /intro content

      var self = this;
      var data = JSON.stringify({
        query:
          "{queryWaterplan{records{fields{Hole Fairway Greens Teebox Roughs } }  }}",
      });
      //     var url= "https://shima.stepzen.net/api/airtable/__graphql"
      this.plans = [];
      var config = {
        method: "post",
        url: "https://shima.stepzen.net/api/airtable/__graphql",
        headers: {
          Authorization:
            "apikey shima::stepzen.net+1000::6c712fbd4771efa8bb73e003d39d39b530b2645e6993693797f9393b18009e0e ",
          "Content-Type": "application/json",
        },
        data: data,
      };

      axios(config)
        .then(function (response) {
          //  console.log(JSON.stringify(response.data));
          self.plans = response.data;
          console.log(self.plans);
        })
        .catch(function (error) {
          console.log(error);
        });
    },
    onSubmit(evt) {
      evt.preventDefault();
      this.status = "loading";

      if (this.gpu) {
        var api_endpoint = this.api_endpoint_gpu;
      } else {
        api_endpoint = this.api_endpoint_cpu;
      }
      let self = this;
      self.answer = "";
      axios
        .get(api_endpoint, { params: { query: self.query } })
        .then(function (response) {
          self.answer = response.data.courses.name;
          self.status = "done";
        })
        .catch(function (error) {
          alert(error);
        });
    },
  },
};
// fetchGraphQLData();
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
span {
 background-color: #30c49b;
 padding: 6;
 max-width: 30rem;
}
</style>
