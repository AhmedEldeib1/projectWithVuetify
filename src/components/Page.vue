<template>
  <v-app>
    <h2 class="text-center ma-10">
      Welcome to <span class="red--text">Eldeib</span> Group
    </h2>

    <v-container>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Obcaecati ut
        voluptas eligendi! Unde numquam praesentium, adipisci nesciunt
        repudiandae tempore, facere cumque alias laudantium, harum doloribus
        quisquam aliquid pariatur veritatis quam.
      </p>
      <p>
        Lorem ipsum dolor, sit amet consectetur adipisicing elit. Quos adipisci
        eius eum minima debitis aut iure dolore laboriosam. Nulla exercitationem
        corporis nam quasi quibusdam nisi expedita omnis delectus dolor
        obcaecati?
      </p>

      <v-row>
        <v-col md4 class="d-flex justify-center">
          <v-tooltip top>
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                class="white"
                light
                text
                v-bind="attrs"
                v-on="on"
                @click="sortBy('person')"
              >
                <v-icon left>mdi-cached</v-icon>by person
              </v-btn>
            </template>
            <span>sort by person</span>
          </v-tooltip>
        </v-col>
        <v-col md4 class="d-flex justify-center">
          <v-tooltip top>
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                class="white"
                light
                text
                v-bind="attrs"
                v-on="on"
                @click="sortBy('title')"
              >
                <v-icon left>mdi-cached</v-icon>by project
              </v-btn>
            </template>
            <span>sort by project</span>
          </v-tooltip>
        </v-col>
        <v-col md4 class="d-flex justify-center">
          <v-tooltip top>
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                class="white"
                light
                text
                v-bind="attrs"
                v-on="on"
                @click="sortBy('status')"
              >
                <v-icon left>mdi-cached</v-icon>by status
              </v-btn>
            </template>
            <span>sort by status</span>
          </v-tooltip>
        </v-col>
      </v-row>
      <div
        v-for="project in projects"
        :key="project.title"
        :class="project.status"
      >
        <v-row class="red pa-5 ma-1">
          <v-col md6>
            <h3>{{ project.title }}</h3>
          </v-col>
          <v-col md2>
            <h4>By: {{ project.person }}</h4>
          </v-col>
          <v-col md2>
            <h4>Due: {{ project.due }}</h4>
          </v-col>
          <v-col md2 class="d-flex justify-end">
            <v-chip small class="white--text" :class="project.status">{{
              project.status
            }}</v-chip>
          </v-col>
        </v-row>
      </div>
    </v-container>
  </v-app>
</template>

<script>
  export default {
    name: "Page",
    data() {
      return {
        projects: [
          {
            title: "Design a new website",
            person: "The Net Ninja",
            due: "1st Jan 2019",
            status: "ongoing",
            content:
              "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!",
          },
          {
            title: "Code up the homepage",
            person: "Chun Li",
            due: "10th Jan 2019",
            status: "complete",
            content:
              "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!",
          },
          {
            title: "Design video thumbnails",
            person: "Ryu",
            due: "20th Dec 2018",
            status: "complete",
            content:
              "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!",
          },
          {
            title: "Create a community forum",
            person: "Gouken",
            due: "20th Oct 2018",
            status: "overdue",
            content:
              "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!",
          },
        ],
      };
    },
    methods: {
      sortBy(prop) {
        this.projects.sort((a, b) => (a[prop] < b[prop] ? -1 : 1));
      },
    },
  };
</script>

<style>
  .ongoing {
    border-left: 10px solid yellow;
  }

  .complete {
    border-left: 10px solid green;
  }

  .overdue {
    border-left: 10px solid red;
  }

  .v-chip.ongoing {
    background-color: yellow !important;
  }

  .v-chip.complete {
    background-color: green !important;
  }

  .v-chip.overdue {
    background: red !important;
  }
</style>
