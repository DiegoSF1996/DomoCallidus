<template>
  <Page>
    <ActionBar>
      <NavigationButton
        @tap="$navigateBack()"
        android.systemIcon="ic_menu_back"
      />
      <Label :text="item.name"></Label>
    </ActionBar>

    <GridLayout>
      <Label class="m-10 h2" verticalAlignment="top"
        >Estado da lâmpada: {{ estado_lampada }}</Label
      >
      <Label class="h3">API: {{ API }}</Label>

      <button height="30%" width="100%" @tap="ligaDesligaLampada()">
        <FormattedString>
          <Span style="font-size: 30%" :text="text_button" fontWeight="bold" />
        </FormattedString>
      </button>
    </GridLayout>
  </Page>
</template>

<script>
import { Http, HttpResponse } from "@nativescript/core";
export default {
  props: ["item", "API"],
  data() {
    return {
      estado_lampada: "Ligada",
      text_button: "Desligar",
      acao_button: false,
    };
  },
  async mounted() {
    await this.atualizaDadosTela();
  },
  methods: {
    async atualizaDadosTela() {
      let responseApi = await this.checarEstadoLampada();
      if (responseApi == false) {
        alert({
          title: "Erro",
          message: "Dispositivo não encontrado",
          okButtonText: "Voltar",
        }).then(() => {
          this.$navigateBack();
        });
      }
      //Se a lampada está ligada, exibe o estado ligada.
      this.estado_lampada = responseApi.estado ? "Ligada" : "Desligada";
      //Se a lampada está ligada, a descrição do botão é desligar.
      this.text_button = responseApi.estado ? "Desligar" : "Ligar";
      //Se a lampada está ligada, a ação é false, para poder desligar.
      this.acao_button = responseApi.estado ? true : false;
    },
    async ligaDesligaLampada() {
      let att = await this.atualizaDadosTela();
      let res = await this.ligaDesligaLampadaApi(!this.acao_button);
      att = await this.atualizaDadosTela();
    },
    async checarEstadoLampada() {
      return await Http.getJSON(this.API + "/")
        .then(
          (result) => {
            return result;
          },
          (e) => {
            return false;
          }
        )
        .catch((a) => {
          console.log(a);
        });
    },
    async ligaDesligaLampadaApi(comando) {
      let url_api = this.API + (comando ? "/ligar" : "/desligar");
      return await Http.getJSON(url_api).then(
        (response) => {
          return response;
        },
        (e) => {
          return false;
        }
      );
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
