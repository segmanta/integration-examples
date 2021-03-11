<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>My Application</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <ion-button expand="block" @click="openModal">Take Survey</ion-button>
    </ion-content>
  </ion-page>
</template>

<script>
import { IonContent,
  IonHeader,
  IonPage,
  IonTitle,
  IonToolbar,
  IonButton,
  modalController, } from "@ionic/vue";
import Modal from "./SurveyModal.vue";

export default {
  components: { IonContent,
  IonHeader,
  IonTitle,
  IonToolbar,
  IonButton,
  IonPage,},
  methods: {
    /**
     * called when the modal is closed
     */
    modalCloseHandler() {
      console.log("modal-closed");
    },
    /**
     * when the user clicks button, we open the modal
     */
    async openModal() {
      
      const modal = await modalController.create({
        component: Modal,
        cssClass: "my-custom-class",
        componentProps: {
          title: "Segmanta Survey",
          surveyUrl: "https://surveys.segmanta.com/bef07d/"
        },
      });
      return modal.present();
    },
  },
};
</script>

<style>
.my-custom-class .modal-wrapper {
  --width: 100%;
  --height: 100%;
}
</style>
