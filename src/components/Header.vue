<template>
  <div class="header">
    <a href="https://www.sca-pamiers.com" target="_blank">
      <img src="../assets/logo-club.png" alt="" class="logo-club">
    </a>

    <a
      @click.prevent="$emit('openModal')"
      class="contact contact-header"
      href="#"
      >Contacter mes coachs</a
    >
    <h1 class="title">
      <span :class="{ 'before-delete': isDeleting }" class="animated-word">{{ mot }}<span :class="{ 'before-delete': isDeleting }" class="bar"></span></span
      ><br />votre saison
    </h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mots: ["suivez", "vivez"],
      mot: "",
      isDeleting: false,
    };
  },
  mounted() {
    let cpt = 0;
    this.showWord(this.mots[cpt % this.mots.length]);
    cpt++;
    setInterval(() => {
      this.isDeleting = true;
      setTimeout(() => {
        this.isDeleting = false;
        this.mot = "";
        this.showWord(this.mots[cpt % this.mots.length]);
        cpt++;
      }, 500);
    }, 7000);
  },
  methods: {
    async showWord(mot) {
      let motSplited = mot.split("");
      for (let i = 1; i < motSplited.length + 1; i++) {
        this.mot = await this.printWord(motSplited.slice(0, i).join(""));
      }
    },
    async printWord(mot) {
      return new Promise((resolve) => {
        setTimeout(() => {
          resolve(mot);
        }, Math.floor(Math.random() * 600) + 100);
      });
    },
  },
};
</script>

<style lang="scss">
.header {
  height: 80vh;
  background: linear-gradient(to top, #000, rgba(0, 0, 0, 0)),
    linear-gradient(to top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.507)),
    url(../assets/header.png);
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  position: relative;
}
.contact-header {
  position: absolute;
  top: 20px;
  right: 20px;
}

.contact {
  background: #fff;
  color: #1f1f1f;
  text-decoration: none;
  padding: 10px 20px;

  border-radius: 100px;
  font-weight: 600;
  transition: 0.4s;

  &:hover {
    transform: scale(0.98);
  }
  &:active {
    transform: scale(0.96);
  }
}

.title {
  position: absolute;
  top: 50%;
  left: 10%;
  transform: translateY(-50%);
  color: #fff;
  font-size: 50px;
  line-height: 120%;
  letter-spacing: 3px;
  text-transform: uppercase;
  span {
    font-size: 70px;
    &.animated-word{
        position: relative;
        &.before-delete {
      background: rgba(4, 4, 155, 0.589);
    }
    }
    &.bar {
        position: absolute;
        display: inline-block;
        height: 70%;
        top: 50%;
        right: 0;
        transform: translateY(-50%);
        width: 2px;
        background: #fff;
        animation: blink 1.5s    infinite  ease-in;
        &.before-delete {
            left: 0;
            right: auto;
        }
    }
  }
}

.logo-club {
    position: absolute;
    top: 20px;
    left: 20px;
    height: 60px;
    filter: brightness(30%);
}

@keyframes blink {
    0% {
        opacity: 0;
    }
    48% {
        opacity: 0;
    }
    50% {
        opacity: 1;
    }
    98% {
        opacity: 1;
    }
    100% {
        opacity: 0;
    }
}
</style>
