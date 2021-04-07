<template>
  <header class="header">
    <NuxtLink to="/" style="text-decoration: none !important"
      ><h3 class="header__title">justdonate</h3></NuxtLink
    >
    <button class="header__btn" @click="showModal">justcreate</button>
  </header>
</template>

<script>
//TODO: Change from modal to a custom component
import Swal from "sweetalert2";
export default {
  name: "Header",
  data() {
    return {};
  },
  methods: {
    showModal() {
      Swal.mixin({
        title:
          "<h4 style='margin-bottom: 5px'>We need some informations about you</h4>",
        icon: null,
        showCloseButton: true,
        showCancelButton: false,
        focusConfirm: true,
        confirmButtonColor: "#e05050",
        focusCancel: false,
        confirmButtonText: "Next &rarr;",
        progressSteps: ["1", "2", "3", "4"]
      })
        .queue([
          {
            title: "Your personal infomation",
            html:
              '<input id="swal-input1" placeholder="Username" class="swal2-input">' +
              '<input id="swal-input1" placeholder="Email" class="swal2-input">'
          },
          {
            title: "Your personal infomation",
            html:
              '<input id="swal-input1" placeholder="First name" class="swal2-input">' +
              '<input id="swal-input1" placeholder="Last name" class="swal2-input">'
          },
          {
            title: "Rest info",
            html:
              '<input id="swal-input1" placeholder="Title your page" class="swal2-input">' +
              '<input id="swal-input1" placeholder="Photo URL" class="swal2-input">' +
              '<input id="swal-input1" placeholder="PayPal email" class="swal2-input">'
          },
          {
            title: "Description",
            input: "textarea",
            inputPlaceholder: "Type your description here...",
            confirmButtonText: "Create!"
          }
        ])
        .then(response => {
          console.log(response.value);
          Swal.fire({
            icon: "success",
            title: "Your page is created!",
            confirmButtonColor: "#e05050",
            confirmButtonText: "SUPER!"
          });
        });
    }
  }
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

  box-shadow: 2px 4px 5px 0px rgba(255, 78, 78, 0.45);
  font-size: 18px;
  background-color: #fff;
  border: 2px solid var(--color-primary);
  color: white;
  background-image: linear-gradient(
    45deg,
    var(--color-primary) 50%,
    transparent 50%
  );
  background-position: 0;
  background-size: 400%;
  transition: all 350ms ease-in-out;
  border-radius: var(--border-radius);
  cursor: pointer;
}

.header__btn:hover {
  background-position: 100%;
  color: var(--color-primary);
}

.swal2-confirm .swal2-styled {
  width: 130px;
  height: 40px;

  box-shadow: 2px 4px 5px 0px rgba(255, 78, 78, 0.45);
  font-size: 18px;
  background-color: #fff;
  border: 2px solid var(--color-primary);
  color: white;
  background-image: linear-gradient(
    45deg,
    var(--color-primary) 50%,
    transparent 50%
  );
  background-position: 0;
  background-size: 400%;
  transition: all 350ms ease-in-out;
  border-radius: var(--border-radius);
  cursor: pointer;
}
.swal2-progress-steps
  .swal2-progress-step.swal2-active-progress-step
  ~ .swal2-progress-step {
  background: #f37c7c !important;
}

.swal2-progress-step-line {
  background: #f37c7c !important;
}

.swal2-progress-steps .swal2-progress-step {
  background: var(--color-primary) !important;
}
/* 
.swal2-progress-steps .swal2-progress-step.swal2-active-progress-step {
  background: var(--color-primary) !important;
} */

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
