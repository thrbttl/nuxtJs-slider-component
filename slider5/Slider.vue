<template>
  <div>
    <div class="banner">
      <div class="slider">
        <img src="image/1.jpg" alt="bir" ref="sliderImg" id="sliderImg" />
      </div>
      <div class="overlay">
        <div class="content">
          <h1 :style="{ color: this.sliderData.color.titleColor }">
            {{ this.sliderData.content.title }}
          </h1>
          <h3 :style="{ color: this.sliderData.color.subTitleColor }">
            {{ this.sliderData.content.subTitle }}
          </h3>

          <div>
            <router-link
              tag="button"
              :to="'/' + this.sliderData.path.btn1Path"
              >{{ this.sliderData.content.btn1 }}</router-link
            >
            <router-link
              class="btn-2"
              tag="button"
              :to="'/' + this.sliderData.path.btn2Path"
              >{{ this.sliderData.content.btn2 }}</router-link
            >
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      images: this.sliderData.images,
      len: null,
      i: 1,
    };
  },
  props: {
    sliderData: {
      required: true,
    },
  },

  methods: {
    slider() {
      this.len = this.images.length;
      if (this.i > this.len - 1) {
        this.i = 0;
      }
      this.$refs.sliderImg.src = this.images[this.i];
      this.i++;
    },
  },
  mounted() {
    setInterval(() => {
      this.slider();
    }, 4000);
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  font-family: sans-serif;
}
.banner {
  width: 100%;
  height: 50vh;
  position: relative;
  overflow: hidden;
}

.slider {
  width: 100%;
  height: 50vh;
  position: absolute;
  top: 0;
}

#sliderImg {
  width: 100%;
  height: 100%;
  object-fit: cover;
  animation: zoom 4s linear infinite;
}

@keyframes zoom {
  0% {
    transform: scale(1.3);
  }
  15% {
    transform: scale(1);
  }
  85% {
    transform: scale(1);
  }
  100% {
    transform: scale(1.3);
  }
}

.overlay {
  width: 100%;
  height: 50vh;
  background: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.2));
  position: absolute;
  top: 0;
}

.content {
  width: 60%;
  margin: 90px auto 0 auto;
  text-align: center;
  color: #fff;
  position: absolute;
  top: 0;
}

.content h3 {
  width: 80%;
  margin: 20px auto 55px;
  font-weight: 100;
  line-height: 25px;
}

button {
  width: 200px;
  padding: 15px 0;
  text-align: center;
  margin: 0 10px;
  border-radius: 25px;
  font-weight: bold;
  border: 2px solid #fe7250;
  background: #fe7250;
  color: #fff;
  cursor: pointer;
  transition: background 0.5s;
}

button:hover {
  background: transparent;
  border: 2px solid #fff;
}

.btn-2 {
  background: transparent;
  border: 2px solid #fff;
}

.btn-2:hover {
  background: #fe7250;
  border: 2px solid #fe7250;
}

@media only screen and (min-width: 1180px) {
}

@media only screen and (min-width: 741px) and (max-width: 1180px) {
}

@media only screen and (min-width: 451px) and (max-width: 740px) {
  .content {
    margin: 110px auto 0 auto;
  }

  .content h1 {
    font-size: 2rem;
  }
  .content h3 {
    font-size: 15px;
    margin: 20px auto 25px;
  }
  button {
    width: 200px;
    width: 80px;
    margin: 0 10px 0 auto;
    font-size: 8px;
  }
}

@media only screen and (min-width: 321px) and (max-width: 450px) {
  .content {
    margin: 90px auto 0 auto;
  }

  .content h1 {
    font-size: 2rem;
  }
  .content h3 {
    font-size: 15px;
    margin: 20px auto 25px;
  }
  button {
    width: 200px;
    width: 80px;
    margin: 0 10px 0 auto;
    font-size: 8px;
  }
}
@media only screen and (max-width: 320px) {
  .content {
    margin: 37px auto 0 auto;
  }

  .content h1 {
    font-size: 1rem;
  }
  .content h3 {
    font-size: 10px;
  }
  button {
    width: 200px;
    width: 80px;
    margin: 0 10px 0 auto;
    font-size: 8px;
  }
}
</style>