<template>
  <Page>
    <ActionBar>
      <Label text="Home"></Label>
    </ActionBar>

    <ListView for="item in items" @itemTap="onItemTap">
      <v-template>
        <StackLayout orientation="horizontal">
          <Label :text="item.name" textWrap="true"></Label>
        </StackLayout>
      </v-template>
    </ListView>
  </Page>
</template>

<script>
import ItemDetails from "./ItemDetails";

export default {
  props: ["API"],
  data() {
    return {
      items: [
        {
          name: "Lâmpada",
          description: "Acessar opções da lâmpada",
        },
      ],
    };
  },
  methods: {
    onItemTap(args) {
      console.log(this.API);
      let API  = this.API;
      this.$navigateTo(ItemDetails, {
        frame: "items",
        props: { item: args.item, 'API':API},
        animated: true,
        transition: {
          name: "slide",
          duration: 200,
          curve: "ease",
        },
      });
    },
  },
};
</script>

<style scoped lang="scss">
// Start custom common variables
@import "@nativescript/theme/scss/variables/blue";
// End custom common variables

// Custom styles
</style>
