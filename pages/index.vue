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
  </div>
</template>

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
</style>
