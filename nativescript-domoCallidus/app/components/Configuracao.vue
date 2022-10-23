<template lang="html">
  <Page>
    <ActionBar>
      <Label>Configurações</Label>
    </ActionBar>

    <GridLayout class="page__content">
      <slot name="APIDetalhes"></slot>
    </GridLayout>
  </Page>
</template>

<script>
export default {

  data() {
    return {
      API: "",
      message: "<!-- Browse page content goes here -->",
    };
  },
};
</script>

<style lang="scss" scoped>
// Start custom common variables
@import "@nativescript/theme/scss/variables/blue";
// End custom common variables

// Custom styles
</style>
