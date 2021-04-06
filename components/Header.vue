<template>
  <header class="header">
    <h3 class="header__title">justdonate</h3>
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
  color: #fff;
  /* background-color: var(--color-primary); */
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
  transition: 0.2s all ease-in-out;
}

.header__btn:hover {
  transform: scale(1.05);
  background-color: #e04f4f;
  box-shadow: 2px 4px 5px 0px rgba(255, 78, 78, 0.6);
}

.header__title {
  font-size: 24px;
  font-weight: normal;
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
