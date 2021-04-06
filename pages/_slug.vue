<template>
  <div>
    <div v-if="!isLoading">
      <div v-if="pageExist" class="wrapper">
        <div class="grid-container">
          <div class="photo">
            <img
              :src="photoURL"
              alt="photo"
              style="width: 100%; height: 100%"
            />
          </div>
          <div class="title text-center">
            <h1>{{ title }}</h1>
          </div>
          <div class="info text-center">
            <h3>{{ firstName }} {{ lastName }}</h3>
          </div>
        </div>
        <div class="desc">{{ desc }}</div>
        <div class="text-center">
          <button class="btn-donate">donate</button>
        </div>
      </div>
      <div v-else class="text-center">
        <h1>Page doesn't exist. You can create it!</h1>
      </div>
    </div>
    <div v-else>
      <h1 class="text-center">Still loading. Please wait.</h1>
    </div>
  </div>
</template>

<script>
import firebase from "firebase";
export default {
  data() {
    return {
      isLoading: true,
      title: "",
      desc: "",
      email: "",
      firstName: "",
      lastName: "",
      username: "",
      photoURL: "",
      paypalEmail: "",
      pageExist: false,
      error: ""
    };
  },
  async mounted() {
    try {
      const db = firebase.firestore();
      const page = await db
        .collection("pages")
        .where("username", "==", this.$route.params.slug)
        .get();
      this.isLoading = false;

      //const pageExist = page.docs[0]?.data() ? true : false;
      this.pageExist = page.docs[0]?.data() ? true : false;

      if (this.pageExist) {
        this.title = page.docs[0].data().title;
        this.desc = page.docs[0].data().desc;
        this.email = page.docs[0].data().email;
        this.firstName = page.docs[0].data().firstName;
        this.lastName = page.docs[0].data().lastName;
        this.username = page.docs[0].data().username;
        this.photoURL = page.docs[0].data().photoURL;
        this.paypalEmail = page.docs[0].data().paypalEmail;
      }
    } catch (err) {
      this.error = err;
      console.log(err);
    }
  }
};
</script>

<style>
.wrapper {
  width: 80%;
  margin-left: auto;
  margin-right: auto;
}
.grid-container {
  margin-top: 45px;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-template-rows: 1fr 1fr;
  gap: 0px 0px;
  grid-template-areas:
    "photo photo title title"
    "photo photo info info";
}
.photo {
  grid-area: photo;
}
.photo img {
  border-radius: var(--border-radius);
}
.title {
  grid-area: title;
  display: grid;
  place-items: center;
  font-size: 1.45rem;
}
.info {
  grid-area: info;
  display: grid;
  place-items: center;
  font-size: 1.4rem;
}
.desc {
  padding-top: 25px;
  text-align: left;
  font-size: 18px;
}

.text-center {
  text-align: center;
}

.btn-donate {
  margin-top: 25px;
  padding: 12px;
  width: 200px;
  height: 67px;
  font-size: 1.5rem;
  letter-spacing: 2px;

  background-color: #fff;
  box-shadow: 2px 4px 5px 0px rgba(255, 78, 78, 0.45);
  border: 2px solid #e05050;
  color: #e05050;
  background-image: linear-gradient(45deg, #e05050 50%, transparent 50%);
  background-position: 100%;
  background-size: 400%;
  transition: all 350ms ease-in-out;
  border-radius: var(--border-radius);
  cursor: pointer;
}

.btn-donate:hover {
  background-position: 0;
  color: white;
}

@media (max-width: 991px) {
  .wrapper {
    width: 90%;
  }

  .btn-donate {
    width: 65%;
  }
}

@media (max-width: 540px) {
  .wrapper {
    width: 95%;
  }
  .grid-container {
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: 1fr;
    gap: 0px 0px;
    grid-template-areas:
      "title"
      "photo"
      "info"
      "desc";
  }
  .btn-donate {
    width: 100%;
    margin-bottom: 50px;
  }
}
</style>
