<template>
  <ion-header>
    <ion-toolbar>
      <ion-title>{{ title }}</ion-title>
      <ion-buttons slot="primary">
        <ion-button color="secondary" @click="modalClose(false)">
          <ion-icon slot="icon-only" name="close"></ion-icon>
        </ion-button>
      </ion-buttons>
    </ion-toolbar>
  </ion-header>
  <ion-content>
    <iframe
      width="100%"
      height="100%"
      border="0"
      :src="surveyUrl"
      class="iframe_container"
      scrolling="yes"
      id="surveyIframe"
    ></iframe>
  </ion-content>
</template>

<script>
import {
  IonContent,
  IonHeader,
  IonTitle,
  IonToolbar,
  IonButtons,
  IonButton,
  IonIcon,
  modalController,
  loadingController,
} from "@ionic/vue";
import { defineComponent } from "vue";

export default defineComponent({
  name: "Modal",
  props: {
    title: { type: String, default: "Super Modal" },
    surveyUrl: { type: String },
  },
  async mounted() {
    const loading = await loadingController.create({
      message: "Loading your survey...",
    });

    await loading.present();

    setTimeout(function() {
      loading.dismiss();
    }, 1000);
  },
  data() {
    return {
      content: "Content",
      loading: null,
    };
  },
  methods: {
    modalClose: function() {
      modalController.dismiss();
    },
  },
  components: {
    IonContent,
    IonHeader,
    IonTitle,
    IonToolbar,
    IonButtons,
    IonButton,
    IonIcon,
  },
});
</script>
<style scoped>
.iframe_container {
  width: 100%;
  height: 100%;
  border: 0;
  overflow: scroll !important;
  -webkit-overflow-scrolling: touch !important;
}

.my-custom-class .modal-wrapper {
  --width: 100%;
  --height: 100%;
}
</style>
