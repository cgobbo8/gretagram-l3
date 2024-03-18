<template>
  <div>
    <Header @openModal="modal = true" />
    <div class="filtre-container">
      <div class="filtres">
        <a
          @click.prevent="index = 0"
          :class="{ active: index == 0 }"
          class="filtre-item"
          href="#"
          >Plannings</a
        >
        <a
          @click.prevent="index = 1"
          :class="{ active: index == 1 }"
          class="filtre-item"
          href="#"
          >Programme musculation</a
        >
      </div>
    </div>
    <div class="excel-container">
      <div :class="{ out: index != 0 }" class="page planning-container">
        <iframe class="iframe semaine-type" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vTE4dpAiciXwt7VmL4H5BD3d2vYN6XBdEXa2rEcLDEaPK-8Y4TA8e1eVR8Rz0Zogw/pubhtml?gid=1818640998&amp;single=true&amp;widget=true&amp;headers=false"></iframe>
        <iframe class="iframe planning-annee" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vTE4dpAiciXwt7VmL4H5BD3d2vYN6XBdEXa2rEcLDEaPK-8Y4TA8e1eVR8Rz0Zogw/pubhtml?gid=2032979842&amp;single=true&amp;widget=true&amp;headers=false"></iframe>
      </div>
      <div :class="{ out: index != 1 }" class="page musculation-container">
        <iframe class="iframe iframe-muscu-1" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vSX86V2pGSV7R7HVaY8vd-6fElgCCh4cmUU9zf8Q7TINtVkbAPKzat3Luj_YZASdQ/pubhtml?gid=467724892&amp;single=true&amp;widget=true&amp;headers=false"></iframe>
        <iframe class="iframe iframe-muscu-2" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vTJws3OVHXW0nR_x1JdADviQJL0E2UlkBzyPIFOBgWXX9-PMighCCfGv9eJTP7fbg/pubhtml?gid=280658891&amp;single=true&amp;widget=true&amp;headers=false"></iframe>
        <iframe class="iframe iframe-muscu-3" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vTDi6_7aeR8SxaQCRqZjk4pwZ5hEtaa_vn4mv5xKE_lm1X87IBAwD1ARN8IsF3FQw/pubhtml?gid=596558491&amp;single=true&amp;widget=true&amp;headers=false"></iframe>
        <iframe class="iframe iframe-muscu-4" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vRWmAVcSHwELvI3jfzY0r2-BCXGsgPLEKkk4Rh3qLmq8Jjp98DgKNMRJ9vZQfskKw/pubhtml?gid=799237740&amp;single=true&amp;widget=true&amp;headers=false"></iframe>
      </div>
    </div>
    <div class="button-contact">
      <a @click.prevent="modal = true" class="contact contact-footer" href=""
        >Contacter mes coachs</a
      >
    </div>
    <div v-if="loading" class="attente">
      <div class="loading">Vivez votre saison</div>
    </div>
    <div
      @click.self="modal = false"
      :class="{ closed: !modal }"
      class="modal-background"
    >
      <div class="modal">
        <ul>
          <li>
            <div class="bloc-nom">
              <div class="nom">Eric Mercadier</div>
              <div class="poste">Manager</div>
            </div>
            <a href="tel:+33675073685" class="lien phoneNum"
              ><img src="./assets/phone.svg" alt="" />Appeler</a
            >
          </li>
          <li>
            <div class="bloc-nom">
              <div class="nom">David Begu</div>
              <div class="poste">Entraîneur</div>
            </div>
            <a href="tel:+33658036458" class="lien phoneNum"
              ><img src="./assets/phone.svg" alt="" />Appeler</a
            >
          </li>
          <li>
            <div class="bloc-nom">
              <div class="nom">Florian Gobbo</div>
              <div class="poste">Préparateur physique</div>
            </div>
            <a href="tel:+33609282549" class="lien phoneNum"
              ><img src="./assets/phone.svg" alt="" />Appeler</a
            >
          </li>
          <li>
            <div class="bloc-nom">
              <div class="nom">Thibaut Renart</div>
              <div class="poste">Entraîneur</div>
            </div>
            <a href="tel:+33626952138" class="lien phoneNum"
              ><img src="./assets/phone.svg" alt="" />Appeler</a
            >
          </li>
          <li>
            <div class="bloc-nom">
              <div class="nom">Thibaut Servat</div>
              <div class="poste">Kinésitherapeute</div>
            </div>
            <a href="tel:+33663194770" class="lien phoneNum"
              ><img src="./assets/phone.svg" alt="" />Appeler</a
            >
          </li>
        </ul>
      </div>
    </div>
    <p class="copyrigth">
      © Copyright {{ new Date().getFullYear() }} - Flo Coaching
    </p>
  </div>
</template>

<script>
import Header from "./components/Header.vue";

export default {
  components: { Header },
  data() {
    return {
      index: 0,
      modal: false,
      loading: true,
    };
  },
  mounted() {
    setTimeout(() => {
      this.loading = false;
    }, 2000);
  },
  watch: {
    modal(newVal, oldVal) {
      if (newVal) document.documentElement.style.overflow = "hidden";
      else document.documentElement.style.overflow = "auto";
    },
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");

* {
  font-family: "Poppins", sans-serif;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  overflow: hidden;
}

.filtre-container {
  display: flex;
  justify-content: center;
  margin-top: 200px;
  margin-bottom: 100px;

  .filtres {
    display: flex;
    align-items: center;
    @media screen and (max-width: 501px) {
      flex-direction: column;
    }
  }

  .filtre-item {
    margin: 0 20px;
    color: #111111;
    text-decoration: none;
    font-weight: 600;
    transition: 0.4s;
    padding: 10px 20px;
    border-radius: 100px;
    @media screen and (max-width: 501px) {
      margin: 10px 0;
    }

    &.active {
      background: #111111;
      color: #fff;
    }

    &:hover {
      transform: scale(0.98);
      &:not(.active) {
        background: #11111110;
      }
    }

    &:active {
      transform: scale(0.96);
    }
  }
}

.excel-container {
  position: relative;
  width: 100vw;
  max-width: 100%;
  display: flex;
  justify-content: center;
}
.planning-container,
.musculation-container {
  width: 80vw;
  .semaine-type {
    height: 260px;
    width: 100%;
    max-width: 860px;
    margin-bottom: 100px;
  }

  .planning-annee {
    height: 800px;
    width: 100%;
  }
}

.iframe-muscu {
  max-width: 1300px;
  height: 820px;

  &-1, &-2, &-3, &-4 {
    &:not(:first-child) {
      margin-top: 100px;
    }
    max-width: 850px;
    height: 720px;
  }

}

.page {
  display: flex;
  flex-direction: column;
  align-items: center;
  transition: 0.4s;
  &.planning-container.out {
    position: absolute;
    left: 1%;
    transform: translateX(-100%);
  }
  &.musculation-container.out {
    position: absolute;
    right: 1%;
    transform: translateX(100%);
  }
}

.iframe {
  width: 100%;
  border-radius: 15px;
  border: 1px solid #00000023;
  box-shadow: 0px 2px 10px 2px rgb(3 0 17 / 15%),
    0px 2px 41px 20px rgb(3 0 17 / 3%);
}

.progImage {
  margin-top: 100px;
  border-radius: 15px;
  border: 1px solid #00000023;
  box-shadow: 0px 2px 10px 2px rgb(3 0 17 / 15%),
    0px 2px 41px 20px rgb(3 0 17 / 3%);
}

.button-contact {
  height: 300px;
  display: flex;
  align-items: center;
  justify-content: center;

  .contact-footer {
    background: #111111;
    color: #fff;
  }
}

.modal-background {
  &.closed {
    pointer-events: none;
    cursor: auto;
    opacity: 0;
    .modal {
      transform: scale(0);
    }
  }
  cursor: pointer;
  transition: 0.4s;
  transform: scale(1);
  position: fixed;
  top: 0;
  left: 0;
  height: 100vh;
  width: 100vw;
  background: #00000028;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 100;

  .modal {
    background: #fff;
    padding: 40px;
    border-radius: 30px;
    transform: scale(1);
    transition: 0.4s;
    cursor: auto;
    box-shadow: 0px 2px 10px 2px rgb(3 0 17 / 15%),
      0px 2px 41px 20px rgb(3 0 17 / 3%);
    overflow: hidden;
    ul {
      list-style: none;
      li {
        display: flex;
        align-items: center;
        justify-content: space-between;
        font-weight: 600;

        width: 400px;
        padding: 20px 0;
        &:not(:last-child) {
          border-bottom: 1px solid #00000015;
        }

        .poste {
          font-size: 0.85rem;
          font-weight: 500;
          color: rgba(0, 0, 0, 0.432);
        }

        .lien {
          display: flex;
          align-items: center;
          justify-content: flex-end;
          transition: 0.4s;
          padding: 8px 15px;
          border-radius: 100px;
          background: #00000004;

          &:hover {
            background: #00000017;
          }
          img {
            margin-right: 10px;
            height: 20px;
          }
        }

        a {
          text-decoration: none;
          color: #00000067;
          font-weight: 400;
        }
      }
    }
  }
}

@media screen and (max-width: 700px) {
  .modal-background .modal {
    z-index: 1000;
    width: auto;
    padding: 20px;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;

    li {
      flex-direction: column;
      text-align: center;
      .poste {
        margin-bottom: 10px;
      }
      .modal-contacts {
        margin: 10px 0;
      }
    }
  }

  .planning-container,
  .musculation-container {
    width: 87vw;
  }
}

@media screen and (max-width: 580px) {
  .modal-background .modal ul li .modal-contacts .phoneNum {
    margin-right: 10px;
  }
}

@media screen and (max-width: 440px) {
  .modal-background {
    width: 100%;
    justify-content: flex-end;
    align-items: flex-end;
    .modal {
      width: 100%;
      border-bottom-left-radius: 0px;
      border-bottom-right-radius: 0px;
      max-height: 70vh;
      padding-top: 100px;
      overflow-y: auto;
    }
  }

  .semaine-type {
    height: 290px !important;
  }

  .planning-annee {
    height: 830px !important;
  }

  .iframe-muscu {
    height: 850px !important;
  }
}

.attente {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgb(0, 0, 0);
  display: flex;
  justify-content: center;
  align-items: center;
  .loading {
    font-weight: 900;
    text-transform: uppercase;
    font-size: 40px;
    background: linear-gradient(
      to right,
      #00000009,
      #00000009,
      #00000009,
      rgba(255, 255, 255, 0.52),
      #00000009,
      #00000009,
      #00000009
    );
    background-clip: text;
    background-size: 200%;
    background-position-x: 100%;
    -webkit-background-clip: text;
    color: transparent;
    animation: backgroundAnim 5s infinite linear;
  }
}

.copyrigth {
  opacity: 0.3;
  text-align: center;
  margin-bottom: 5px;
}

@keyframes backgroundAnim {
  0% {
    background-position-x: 100%;
  }
  50% {
    background-position-x: 0%;
  }
  100% {
    background-position-x: 100%;
  }
}
</style>
