<template>
  <keyPad v-if="keypadcomp"></keyPad>
  <favoritesPage v-if="favoritescomp"></favoritesPage>
  <recentPage v-if="recentcomp"></recentPage>
  <contactPage v-if="contactcomp"></contactPage>
  <voiceMail v-if="voicecomp"></voiceMail>

  <div class="bot-navigation">
    <div>
      <button @click="makeFavourites()">
        <img src="../assets/Call/star.png" alt="" />
      </button>
      <label style="color: #7c7c7c">Favourites</label>
    </div>
    <div>
      <button @click="makeRecents()">
        <img src="../assets/Call/clock.png" alt="" />
      </button>
      <label style="color: #7c7c7c">Recents</label>
    </div>
    <div>
      <button @click="makeContacts()">
        <img src="../assets/Call/contact.png" alt="" />
      </button>
      <label style="color: #7c7c7c">Contacts</label>
    </div>
    <div>
      <button @click="makeKeypad()">
        <img src="../assets/Call/keyboard.png" alt="" />
      </button>
      <label style="color: #7c7c7c">Keypad</label>
    </div>
    <div>
      <button @click="makeVoicemail()">
        <img style="height: 20px" src="../assets/Call/voicemail.png" alt="" />
      </button>
      <label style="color: #7c7c7c">Voicemail</label>
    </div>
  </div>
</template>

<script>
import keyPad from "./childComponents/callPageChilds/keyPad.vue";
import favoritesPage from "./childComponents/callPageChilds/favoritesPage.vue";
import recentPage from "./childComponents/callPageChilds/recentPage.vue";
import contactPage from "./childComponents/callPageChilds/contactPage.vue";
import voiceMail from "./childComponents/callPageChilds/voiceMail.vue";
export default {
  components: {
    keyPad,
    favoritesPage,
    recentPage,
    contactPage,
    voiceMail,
  },
  data() {
    return {
      keypadcomp: true,
      favoritescomp: false,
      recentcomp: false,
      contactcomp: false,
      voicecomp: false,
    };
  },

  methods: {
    makeKeypad() {
      this.keypadcomp = true;
      this.favoritescomp = false;
      this.recentcomp = false;
      this.contactcomp = false;
      this.voicecomp = false;
    },
    makeFavourites() {
      this.keypadcomp = false;
      this.favoritescomp = true;
      this.recentcomp = false;
      this.contactcomp = false;
      this.voicecomp = false;
    },
    makeRecents() {
      this.keypadcomp = false;
      this.favoritescomp = false;
      this.recentcomp = true;
      this.contactcomp = false;
      this.voicecomp = false;
    },
    makeContacts() {
      this.keypadcomp = false;
      this.favoritescomp = false;
      this.recentcomp = false;
      this.contactcomp = true;
      this.voicecomp = false;
    },
    makeVoicemail() {
      this.keypadcomp = false;
      this.favoritescomp = false;
      this.recentcomp = false;
      this.contactcomp = false;
      this.voicecomp = true;
    },
  },
};
</script>

<style scoped>
.contactPage {
  height: 100%;
}
.bot-navigation {
  display: flex;
  align-items: center;
  height: 50px;
  justify-content: space-evenly;
  background: #0e0e0e0f;
  overflow: auto;
  border-bottom-right-radius: 16px;
  border-bottom-left-radius: 16px;
  position: sticky;
  -webkit-backdrop-filter: blur(5px);
  backdrop-filter: blur(3px);
}

.bot-navigation button {
  background-color: transparent;
  border: none;
}
.bot-navigation img {
  height: 25px;
  width: 25px;
}
.bot-navigation label {
  font-size: x-small;
}
.bot-navigation div {
  display: flex;
  flex-direction: column;
}
</style>
