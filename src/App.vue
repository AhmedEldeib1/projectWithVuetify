<template>
 <v-app>
   <HelloWorld></HelloWorld>
   <Page></Page>
   <NextPage></NextPage>
 </v-app>
</template>

<script>
import HelloWorld from "@/components/HelloWorld";
import Page from "@/components/Page"
import NextPage from "@/components/NextPage"
export default {
  name: "App",
  components:{
    HelloWorld,
    Page,
    NextPage
  },
  data: () => ({
    //
  }),
};
</script>

<style lang="scss">

</style>
