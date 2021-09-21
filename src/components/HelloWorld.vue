<template>
  <div>
    <v-card color="grey lighten-4" flat tile>
      <v-toolbar dense>
        <v-app-bar-nav-icon @click="drawer = !drawer"> </v-app-bar-nav-icon>

        <v-toolbar-title>
          <span class="font-weight-light red--text">Ahmed </span>
          <span class="font-weight-bold blue--text">Eldeib</span>
        </v-toolbar-title>

        <!-- start snackbar -->
        <v-snackbar v-model="snackbar">
          {{ text }}

          <template v-slot:action="{ attrs }">
            <v-btn color="pink" text v-bind="attrs" @click="snackbar = false">
              Close
            </v-btn>
          </template>
        </v-snackbar>
        <!-- end snackbar -->

        <v-spacer></v-spacer>

        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-heart</v-icon>
        </v-btn>

        <div class="text-center">
          <v-menu offset-y>
            <template v-slot:activator="{ on, attrs }">
              <v-btn text color="pink" dark v-bind="attrs" v-on="on">
                Menu
              </v-btn>
            </template>
            <v-list>
              <v-list-item v-for="(item, index) in items" :key="index">
                <v-list-item-title>{{ item.title }}</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
        </div>

        <!-- <v-btn icon>
                <v-icon>mdi-dots-vertical</v-icon>
            </v-btn> -->

        <!-- menue here -->

        <div class="text-center">
          <v-menu offset-y>
            <template v-slot:activator="{ on, attrs }">
              <v-btn icon v-bind="attrs" v-on="on">
                <v-icon>mdi-dots-vertical</v-icon>
              </v-btn>
            </template>
            <v-list>
              <v-list-item v-for="(item, index) in items" :key="index">
                <v-list-item-title>{{ item.title }}</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
        </div>

        <!-- menue here -->
      </v-toolbar>
    </v-card>
    <v-navigation-drawer
      v-model="drawer"
      class="warning"
      absolute
      bottom
      temporary
    >
      <v-list nav dense>
        <v-list-tile-title class="white--text">
          <v-icon left class="white--text"> mdi-view-dashboard </v-icon>
          <b>Dashboard</b>
          <div class="d-flex justify-center my-5">
            <v-avatar color="primary" size="150">
              <img src="@/assets/myPic.jpg" alt="" srcset="" />
            </v-avatar>
          </div>

          <!-- Popup start -->
          <div class="d-flex justify-center">
            <v-dialog
              transition="dialog-bottom-transition"
              v-model="dialog"
              max-width="600"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-btn color="primary" v-bind="attrs" v-on="on"
                  >Add new project</v-btn
                >
              </template>
              <template>
                <v-card>
                  <v-toolbar color="primary" dark>Policies</v-toolbar>
                  <v-card-text>
                    <div class="text-h2 pa-12">Do you love us?</div>
                    <v-form ref="form">
                      <v-text-field
                        :rules="inputRules"
                        label="First name"
                        prepend-icon="mdi-email"
                        placeholder="ahmed el.."
                        v-model="Fname"
                        required
                      ></v-text-field>
                      <v-textarea
                        prepend-icon="mdi-message-text"
                        v-model="theMssg"
                      ></v-textarea>
                      <!-- start date -->
                      <v-menu>
                        <v-text-field
                          slot="activator"
                          label="Due Date"
                        ></v-text-field>
                        <v-date-picker v-model="due"></v-date-picker>
                      </v-menu>
                      <!-- end date -->
                    </v-form>
                  </v-card-text>
                  <v-card-actions class="justify-end">
                    <v-btn text @click="valid">Add Project</v-btn>
                  </v-card-actions>
                </v-card>
              </template>
            </v-dialog>
          </div>
          <!-- Popup end -->
        </v-list-tile-title>
        <v-list-item-group
          v-model="group"
          active-class="deep-purple--text text--accent-4"
        >
          <v-list-item>
            <v-list-item-title>Foo</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-title>Bar</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-title>Fizz</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-title>Buzz</v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script>
  import { theColect } from "../firebase";
  import { addDoc } from "firebase/firestore/lite";

  export default {
    name: "HelloWorld",

    data: () => ({
      drawer: false,
      group: null,
      items: [
        {
          title: "Click Me",
        },
        {
          title: "Click Me",
        },
        {
          title: "Click Me",
        },
        {
          title: "Click Me 2",
        },
      ],
      snackbar: false,
      text: `Submitted successfully!!`,
      dialog: false,
      picker: new Date(Date.now() - new Date().getTimezoneOffset() * 60000)
        .toISOString()
        .substr(0, 10),
      due: null,
      inputRules: [(v) => v.length > 20 || "minimum length if 20 chars"],
      Fname: " ",
      theMssg: " ",
    }),
    watch: {
      group() {
        this.drawer = false;
      },
    },
    methods: {
      valid() {
        if (this.$refs.form.validate()) {
          console.log("yes Valid");
          this.dialog = false;
          this.snackbar = true;
          addDoc(theColect, {
            name: this.Fname,
            text: this.theMssg,
          });
        }
      },
    },
  };
</script>
