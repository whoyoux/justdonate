<template>
  <header class="header">
    <NuxtLink to="/" style="text-decoration: none !important"
      ><h3 class="header__title">justdonate</h3></NuxtLink
    >
    <button class="header__btn">justcreate</button>
  </header>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style>
.header {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: center;

  border-bottom: 1px solid #ccc;
}

.header__btn {
  width: 130px;
  height: 40px;

  /* color: #fff;
  background: rgb(241, 98, 98);
  background: linear-gradient(
    150deg,
    rgba(241, 98, 98, 1) 0%,
    rgba(224, 80, 80, 1) 100%
  );
  border-radius: 5px;
  border: none;
  font-size: 18px;
  box-shadow: 2px 4px 5px 0px rgba(255, 78, 78, 0.45);
  cursor: pointer;
  transition: 0.2s all ease-in-out; */
  box-shadow: 2px 4px 5px 0px rgba(255, 78, 78, 0.45);
  font-size: 18px;
  background-color: #fff;
  border: 2px solid #e05050;
  /* color: #e05050; */
  color: white;
  background-image: linear-gradient(45deg, #e05050 50%, transparent 50%);
  background-position: 0;
  background-size: 400%;
  transition: all 350ms ease-in-out;
  border-radius: var(--border-radius);
  cursor: pointer;
}

.header__btn:hover {
  /* transform: scale(1.05);
  background-color: #e04f4f;
  box-shadow: 2px 4px 5px 0px rgba(255, 78, 78, 0.6); */
  background-position: 100%;
  color: #e05050;
  /* color: white; */
}

.header__title {
  font-size: 24px;
  font-weight: normal;
  color: #000;
}

@media (max-width: 991px) {
  .header {
    flex-direction: column;
    text-align: center;
    padding-bottom: 18px;
  }

  .header__title {
    font-size: 24px;
  }
  .header__btn {
    width: 45%;
    height: 35px;
  }
}

@media (max-width: 540px) {
  .header__title {
    font-size: 28px;
  }
  .header__btn {
    width: 80%;
    height: 45px;
  }
}
</style>
