<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Página Inicial</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Idade</ion-title>
        </ion-toolbar>
      </ion-header>

      <div id="container">
        <ion-item>
          <ion-label>Digite o ano que nasceu: </ion-label>
        </ion-item>
        <ion-item>
          <ion-input type="date" v-model="valorInput"></ion-input
        ></ion-item>
        <ion-button color="success" expand="full" @click="validaIdade"
          >Salvar</ion-button
        >
        <ion-item>
          <p>{{ idade }}</p></ion-item
        >
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import {
  IonContent,
  IonHeader,
  IonPage,
  IonTitle,
  IonToolbar,
} from "@ionic/vue";
import { IonLabel, IonInput, IonItem } from "@ionic/vue";
import { defineComponent } from "vue";

export default defineComponent({
  name: "Home",
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    IonLabel,
    IonInput,
    IonItem,
  },
  methods: {
    validaIdade() {
      const dataNasc = new Date(this.valorInput);
      const hoje = new Date();
      const idade = hoje.getFullYear() - dataNasc.getFullYear();
      this.idade = idade;
      console.log(`A sua idade é: ${idade}`);
    },
  },
  data() {
    return {
      valorInput: "",
      idade: 0,
    };
  },
});
</script>

<style scoped>
#container {
  text-align: center;
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container p {
  font-size: 18px;
  text-align: center;
  color: #8c8c8c;
  margin: 0;
}


</style>