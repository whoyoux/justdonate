<template>
  <div class="container">
    <img
      src="../assets/popularity.svg"
      alt="logo"
      class="container__img mt-1"
    />
    <h1 class="mt-3">
      justdonate.it/<span class="text-red text-italic">your-name</span>
    </h1>
    <h2 class="text-normal" style="font-size: 28px">that's it</h2>
    <h1>or press big <span class="text-red">red</span> button</h1>
    <Spacer :width="'80%'" style="margin-top: 25px" />
    <div class="community text-center" style="margin-top: 25px">
      <h1>Our <span class="text-red">community</span></h1>
      <div class="flex-container">
        <div
          class="flex-container__item"
          v-for="page in pages"
          v-bind:key="page.title"
          @click="$router.push(`/${page.username}`)"
        >
          <div class="flex-container__item__img">
            <img
              :src="page.photoURL"
              class="flex-container__item__img"
              :alt="page.title"
            />
            <h1 class="flex-container__item__img__text">{{ page.title }}</h1>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import firebase from "firebase/app";
import "firebase/firestore";
import Spacer from "../components/Spacer";

export default {
  name: "Index",
  components: {
    Spacer
  },
  data() {
    return {
      pages: []
    };
  },
  async mounted() {
    try {
      const db = firebase.firestore();

      const pagesCollection = await db.collection("pages").get();

      pagesCollection.forEach(page => {
        this.pages.push(page.data());
      });
    } catch (err) {
      console.log(err);
    }
  }
};
</script>

<style>
.container {
  width: 80vw;
  margin-left: auto;
  margin-right: auto;
  margin-top: 2rem;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.container__img {
  width: 75%;
  height: 50vh;
}

.text-red {
  color: var(--color-primary) !important;
}

.text-italic {
  font-style: italic !important;
}

.text-normal {
  font-style: normal;
}

.mt-3 {
  margin-top: 2.5rem;
}

.mt-2 {
  margin-top: 2rem;
}

.mt-1 {
  margin-top: 1.5rem;
}

.flex-container {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  margin-bottom: 55px;
}

.flex-container__item {
  width: 350px;
  height: 175px;
  cursor: pointer;
  transition: 0.2s all ease-in-out;
  border-radius: var(--border-radius);
}

.flex-container__item__img {
  position: relative;
  width: 100%;
  height: 100%;
  border-radius: var(--border-radius);
}

.flex-container__item__img__text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

  margin: 0;
  padding: 0;
  color: white;
  text-shadow: 1.5px 1.5px #000;
  letter-spacing: 1px;
  font-weight: normal;
  transition: 0.2s all ease-in-out;
}

.flex-container__item:hover .flex-container__item__img__text {
  font-size: 2.5rem;
}

.flex-container__item:hover {
  box-shadow: 2px 2px 10px #000;
}

@media (max-width: 991px) {
  .container__img {
    height: auto;
  }
}

@media (max-width: 540px) {
  .container {
    text-align: center;
  }
  .container__img {
    height: auto;
  }
}
</style>
