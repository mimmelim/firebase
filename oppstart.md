    #Oppstart

    Opprett en profil - eller logg inn på - [Firebase sine nettsider](https://console.firebase.google.com/)


    Opprett et Firebase prosjekt ved å klikke 'Add project' i Firebase consolen. Følg instruksjonene på skjermen.  

    Disable Google Analytics hvis du ikke vil 'ha noe med dem å gjøre' :)
    
    Velg 'Test mode' når du får valget mellom denne og 'Locked mode'.


    
    Navigate to the Cloud Firestore section of the Firebase console. You'll be prompted to select an existing Firebase project. Follow the database creation workflow.

    Select a starting mode for your Cloud Firestore Security Rules:

    Test mode

        Good for getting started with the mobile and web client libraries, but allows anyone to read and overwrite your data. After testing, make sure to review the Secure your data section.

        To get started with the web, Apple platforms, or Android SDK, select test mode.
    Locked mode

        Denies all reads and writes from mobile and web clients. Your authenticated application servers (C#, Go, Java, Node.js, PHP, Python, or Ruby) can still access your database.

        To get started with the C#, Go, Java, Node.js, PHP, Python, or Ruby server client library, select locked mode.

    Select a location for your database.

        This location setting is your project's default Google Cloud Platform (GCP) resource location. Note that this location will be used for GCP services in your project that require a location setting, specifically, your default Cloud Storage bucket and your App Engine app (which is required if you use Cloud Scheduler).

        If you aren't able to select a location, then your project already has a default GCP resource location. It was set either during project creation or when setting up another service that requires a location setting.
    Warning: After you set your project's default GCP resource location, you cannot change it.

    Click Done.

Cloud Firestore and App Engine: You can't use both Cloud Firestore and Cloud Datastore in the same project, which might affect apps using App Engine. Try using Cloud Firestore with a different project.

When you enable Cloud Firestore, it also enables the API in the Cloud API Manager.
Set up your development environment
Add the required dependencies and client libraries to your app.

Gå til [Firebase sin quickstartside og velg riktig bibliotekoppsett](https://firebase.google.com/docs/firestore/quickstart). Velg web version 9 (modular).

Follow the instructions to add Firebase to your Web app.
The Cloud Firestore SDK is available as an npm package.

npm install firebase@9.16.0 --save

You'll need to import both Firebase and Cloud Firestore.

import { initializeApp } from "firebase/app";
import { getFirestore } from "firebase/firestore";


## Initialize an instance of Cloud Firestore:

import { initializeApp } from "firebase/app";
import { getFirestore } from "firebase/firestore";

// TODO: Replace the following with your app's Firebase project configuration
// See: https://support.google.com/firebase/answer/7015592
const firebaseConfig = {
    FIREBASE_CONFIGURATION


};

// Initialize Firebase
const app = initializeApp(firebaseConfig);


// Initialize Cloud Firestore and get a reference to the service
const db = getFirestore(app);

((Replace FIREBASE_CONFIGURATION with your web app's firebaseConfig.

To persist data when the device loses its connection, see the Enable Offline Data documentation. )) <--skal disse tre siste linjene være med?


## Add data

Cloud Firestore stores data in Documents, which are stored in Collections. Cloud Firestore creates collections and documents implicitly the first time you add data to the document. You do not need to explicitly create collections or documents.

Create a new collection and a document using the following example code.

import { collection, addDoc } from "firebase/firestore"; 

try {
  const docRef = await addDoc(collection(db, "users"), {
    first: "Ada",
    last: "Lovelace",
    born: 1815
  });
  console.log("Document written with ID: ", docRef.id);
} catch (e) {
  console.error("Error adding document: ", e);
}


Now add another document to the users collection. Notice that this document includes a key-value pair (middle name) that does not appear in the first document. Documents in a collection can contain different sets of information.

// Add a second document with a generated ID.
import { addDoc, collection } from "firebase/firestore"; 

try {
  const docRef = await addDoc(collection(db, "users"), {
    first: "Alan",
    middle: "Mathison",
    last: "Turing",
    born: 1912
  });

  console.log("Document written with ID: ", docRef.id);
} catch (e) {
  console.error("Error adding document: ", e);
}


Read data

To quickly verify that you've added data to Cloud Firestore, use the data viewer in the Firebase console.

You can also use the "get" method to retrieve the entire collection.


import { collection, getDocs } from "firebase/firestore"; 

const querySnapshot = await getDocs(collection(db, "users"));
querySnapshot.forEach((doc) => {
  console.log(`${doc.id} => ${doc.data()}`);
});


## Secure your data
Se [rules tab nederst](https://firebase.google.com/docs/firestore/quickstart#web-version-9) på Firebase sin side.

Lær om oppstart i en [youtube-video](https://youtu.be/BjtxPj6jRM8)


