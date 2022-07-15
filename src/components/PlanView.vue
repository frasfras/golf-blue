<template>
  <div class="about">
    <formWizard @onComplete="submit">
      <tab-content title="Course waterplan" :selected="true">
        <div class="form-group">
          <label for="overview">Requestor</label>
          <input
            type="text"
            class="form-control"
            placeholder="Enter your name"
            v-model="overview"
          />
          <label for="overview">Description</label>
          <input
            type="text"
            class="form-control"
            placeholder="Description"
            v-model="overview"
          />
        </div>
      </tab-content>

      <tab-content title=" Set fairway schedule">
        <b-form-input
          v-model="companyName"
          placeholder="Enter your name"
        ></b-form-input>
        <label for="companyName">Set Fairway api</label>

        <div>
          <v-form>
            <v-container>
              <v-row>
                <v-col cols="6" sm="6" md="6">
                  <v-slider
                    v-model="ex1.val"
                    :color="ex1.color"
                    :label="ex1.label"
                    min="8"
                    max="15"
                    thumb-label="always"
                  ></v-slider>

                  <v-slider
                    v-model="ex2.val"
                    :label="ex2.label"
                    :color="ex2.color"
                    min="8"
                    max="15"
                    thumb-label="always"
                  ></v-slider>
                </v-col>
                <v-col cols="6" sm="6" md="6">
                  <v-slider
                    v-model="ex3.val"
                    :label="ex3.label"
                    min="8"
                    max="15"
                    :color="ex3.color"
                    thumb-label="always"
                  ></v-slider>
                  <v-slider
                    v-model="ex4.val"
                    :label="ex4.label"
                    min="8"
                    max="15"
                    :color="ex3.color"
                    thumb-label="always"
                  ></v-slider>
                </v-col>
              </v-row>
              <v-row>
                <v-col cols="6" sm="6" md="6">
                  <v-slider
                    v-model="fx5.val"
                    :color="fx5.color"
                    :label="fx5.label"
                    min="8"
                    max="15"
                    thumb-label="always"
                  ></v-slider>

                  <v-slider
                    v-model="fx6.val"
                    :label="fx6.label"
                    :color="fx6.color"
                    min="8"
                    max="15"
                    thumb-label="always"
                  ></v-slider>
                </v-col>
                <v-col cols="6" sm="6" md="6">
                  <v-slider
                    v-model="fx7.val"
                    :label="fx7.label"
                    min="8"
                    max="15"
                    :color="ex3.color"
                    thumb-label="always"
                  ></v-slider>
                  <v-slider
                    v-model="fx8.val"
                    :label="fx8.label"
                    min="8"
                    max="15"
                    :color="ex3.color"
                    thumb-label="always"
                  ></v-slider>
                  <v-slider
                    v-model="fx9.val"
                    :label="fx9.label"
                    min="8"
                    max="15"
                    :color="ex3.color"
                    thumb-label="always"
                  ></v-slider>
                </v-col>
              </v-row>
            </v-container>
          </v-form>
        </div>
      </tab-content>
      <tab-content title="Set the Greens">
        <v-slider
          v-model="ex5.val"
          :color="ex5.color"
          :label="ex5.label"
          min="8"
          max="15"
          thumb-label="always"
        ></v-slider>

        <v-slider
          v-model="ex6.val"
          :label="ex6.label"
          :color="ex6.color"
          min="8"
          max="15"
          thumb-label="always"
        ></v-slider>

        <v-slider
          v-model="ex7.val"
          :label="ex7.label"
          min="8"
          max="15"
          :color="ex7.color"
          thumb-label="always"
        ></v-slider>
        <v-slider
          v-model="ex8.val"
          :label="ex8.label"
          min="8"
          max="15"
          :color="ex8.color"
          thumb-label="always"
        ></v-slider>
        <v-slider
          v-model="ex9.val"
          :label="ex9.label"
          min="8"
          max="15"
          :color="ex9.color"
          thumb-label="always"
        ></v-slider>
      </tab-content>
      <tab-content title="Course Review" :selected="false">
        <div class="form-group">
          <label for="overview">Fairway</label>
          <input
            type="text"
            class="form-control"
            placeholder="Enter your name"
            v-model="ex1.val"
          />
          <label for="fulln">Green</label>
          <input
            type="text"
            class="form-control"
            placeholder="Enter your"
            v-model="ex5.val"
          />

          <label for="Teebox">Teebox</label>
          <input
            type="text"
            class="form-control"
            placeholder=""
            v-model="ex6.val"
          />
          <label for="Teebox">Roughs</label>
          <input
            type="text"
            class="form-control"
            placeholder=""
            v-model="ex7.val"
          />
        </div>
      </tab-content>
      <tab-content title="Set Days">
        <div class="form-group">
          <label for="days">Days</label>
        </div>
       
       
        <div align="left" class="sch-colum-haft">
          <label for="sun"></label>sun: </label> <br/>
          <input type="date"  id="sun" v-model="date" required />
        </div>
        
         <div align="left" class="sch-colum-haft">
          <label for="sun"></label>mon: </label><br/>
          <input type="date"  id="mon" v-model="mon" required />
        </div>
        <div align="left" class="sch-colum-haft">
          <label for="sun"> tue:   </label><br/>
          <input type="date" placeholder id="tue" v-model="tue" required />
        </div>
        <div align="left" class="sch-colum-haft">
          <label for="wed"> wed: </label><br/>
          <input type="date"  id="wed" v-model="wed" required />
        </div>
        <div align="left" class="sch-colum-haft">
          <label for="thu">thu: </label><br/>
          <input type="date"  id="thu" v-model="date" required />
        </div>
        <div align="left" class="sch-colum-haft">
          <label for="fri">fri: </label><br/>
          <input type="date"  id="fri" v-model="fri" required />
        </div>
      </tab-content>

      <tab-content title="Resolution">
        <div class="form-group">
          <label for="referral"></label>
        </div>
          <label for="overview">Instructions</label>
          <input
            type="text"
            class="form-control"
            placeholder=""
            v-model="email"
          />
        
      </tab-content>
    </formWizard>
  </div>
</template>
<script>
//local registration
import { FormWizard, TabContent } from "vue-step-wizard";
import "vue-step-wizard/dist/vue-step-wizard.css";

export default {
  name: "PlanView",
  //component code
  components: {
    FormWizard,
    TabContent,
  },
  data() {
    return {
      companyName: "",
      date: "",
      tue: "",
      wed: "",
      thu: "",
      fri: "",
      sat: "",
      picker:"",
      email: "",
      done: "success",
      ex1: { label: "Hole1", val: 25, color: "#234560" },
      ex2: { label: "Hole2", val: 75, color: "#234560" },
      ex3: { label: "Hole3", val: 50, color: "#234560" },
      ex4: { label: "Hole4", val: 25, color: "#234560" },
      ex5: { label: "Hole1", val: 75, color: "#234560" },
      ex6: { label: "Hole2", val: 50, color: "#234560" },
      ex7: { label: "Hole3", val: 25, color: "#234560" },
      ex8: { label: "Hole4", val: 75, color: "#234560" },
      ex9: { label: "Hole5", val: 50, color: "#234560" },
      ex10: { label: "Hole6", val: 50, color: "#234560" },
      ex11: { label: "Hole7", val: 25, color: "#234560" },
      ex12: { label: "Hole8", val: 75, color: "#234560" },
      ex13: { label: "Hole9", val: 50, color: "#234560" },
      fx5: { label: "Hole5", val: 75, color: "#234560" },
      fx6: { label: "Hole6", val: 50, color: "#234560" },
      fx7: { label: "Hole7", val: 25, color: "#234560" },
      fx8: { label: "Hole8", val: 75, color: "#234560" },
      fx9: { label: "Hole9", val: 50, color: "#234560" },
    };
  },
  methods: {
    submit() {
      console.log("ok");
      alert(this.done);
      var myHeaders = new Headers();
      myHeaders.append("Content-Type", "application/json");
      myHeaders.append("Accept", "application/json");

      var gr = this.ex5.val;
      var graphql = JSON.stringify({
        query:
          'mutation MyQuery1 ($greens: Float) {\n  update_waterplan(id: "rec0fL8gLI3iETJFn", greens: $greens, hole: "2") {\n    id\n    greens\n    hole\n  }\n}',
        variables: { greens: gr },
      });
      var requestOptions = {
        method: "POST",
        headers: myHeaders,
        body: graphql,
        redirect: "follow",
      };

      fetch(
        "https://api.baseql.com/airtable/graphql/appneKtre6Ux4ESiq",
        requestOptions
      )
        .then((response) => response.text())
        .then((result) => console.log(result))
        .catch((error) => console.log("error", error));
    },
  },
};
</script>
<style>
nav a {
  font-weight: bold;
  color: #2c3e50;
}
</style>
