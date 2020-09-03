<script>
  import BasePage from "./BasePage.svelte";
  import * as firebase from "firebase/app";
  import "firebase/firestore";

  const firebaseConfig = {
    apiKey: "AIzaSyB00V3BHzH0YPC_uZjvnBPJ880TIPp1ngo",
    authDomain: "cesi-phishing.firebaseapp.com",
    databaseURL: "https://cesi-phishing.firebaseio.com",
    projectId: "cesi-phishing",
    storageBucket: "cesi-phishing.appspot.com",
    messagingSenderId: "115289338245",
    appId: "1:115289338245:web:836428621d1db19dccd4ec"
  };

  // Initialize Firebase
  firebase.initializeApp(firebaseConfig);

  var db = firebase.firestore();
</script>

<style>

</style>

<BasePage {db} />
