<template lang="html">
  <TabView androidTabsPosition="bottom">
    <TabViewItem title="Home">
      <Frame id="items">
        <Items :API="API" />
      </Frame>
    </TabViewItem>

    <TabViewItem title="Config">
      <Frame id="browse">
        <Browse>
          <template slot="APIDetalhes">
            <Label height="30%" width="100%" style="font-size: 30%"
              >API: {{ API }}</Label
            >
            <TextField
              height="20%"
              width="100%"
              style="font-size:25%"
              v-model="API"
              placeholder="Nova API"
            />
          </template>
        </Browse>
      </Frame>
    </TabViewItem>
  </TabView>
</template>

<script>
import Items from "./Items.vue";
import Browse from "./Configuracao.vue";
import Search from "./Search.vue";

export default {
  components: {
    Items,
    Browse,
    Search,
  },
  data() {
    return {
      API: "http://192.168.15.122",
    };
  },
  methods: {
    setApi(api) {
      this.API = api;
    },
    getApi() {
      return this.API;
    },
  },
};
</script>

<style lang="scss">
// Start custom common variables
@import "@nativescript/theme/scss/variables/blue";
// End custom common variables

// Custom styles
</style>
