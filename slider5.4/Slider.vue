<template>
  <div>
    <div
      class="banner"
      :style="{ background: this.sliderData.color.backgroundColor }"
    >
      <div class="slider">
        <img src="image/1.jpg" alt="bir" ref="sliderImg" id="sliderImg" />
      </div>
      <div class="overlay">
        <button @click="slider()" class="nextbtn">&gt;</button>
        <button @click="sliderprev()" class="prevbtn">&lt;</button>
        <div class="content">
          <h1 ref="title" :style="{ color: this.sliderData.color.titleColor }">
            {{ this.sliderData.titleArray[0] }}
          </h1>
          <h3
            ref="subTitle"
            :style="{ color: this.sliderData.color.subTitleColor }"
          >
            {{ this.sliderData.subTitleArray[0] }}
          </h3>

          <div>
            <router-link ref="path" tag="button" :to="'/' + this.path">
              {{ this.sliderData.btn }}
            </router-link>
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
      titleArray: this.sliderData.titleArray,
      subTitleArray: this.sliderData.subTitleArray,
      pathArray: this.sliderData.pathArray,
      path: this.sliderData.pathArray[0],
      len: null,
      i: 0,
      num: 320 / this.sliderData.images.length,
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
      if (this.i == this.len - 1) {
        this.i = 0;
        this.$refs.sliderImg.src = this.images[this.i];
        this.$refs.title.innerText = this.titleArray[this.i];
        this.$refs.subTitle.innerText = this.subTitleArray[this.i];
        this.path = this.pathArray[this.i];
      } else {
        this.i++;
        this.$refs.sliderImg.src = this.images[this.i];
        this.$refs.title.innerText = this.titleArray[this.i];
        this.$refs.subTitle.innerText = this.subTitleArray[this.i];
        this.path = this.pathArray[this.i];
      }
    },
    sliderprev() {
      if (this.i == 0) {
        this.len = this.images.length;
        this.i = this.len - 1;
        this.$refs.sliderImg.src = this.images[this.i];
        this.$refs.title.innerText = this.titleArray[this.i];
        this.$refs.subTitle.innerText = this.subTitleArray[this.i];
        this.path = this.pathArray[this.i];
      } else {
        this.i--;
        this.$refs.sliderImg.src = this.images[this.i];
        this.$refs.title.innerText = this.titleArray[this.i];
        this.$refs.subTitle.innerText = this.subTitleArray[this.i];
      }
    },
  },
  mounted() {
    setInterval(() => {
      this.slider();
    }, 5000);
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
  background: rgb(77, 80, 93);
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
  animation: zoom 5s linear infinite;
}

@keyframes zoom {
  0% {
    opacity: 0;
    transform: translateX(-100%);
  }
  15% {
    opacity: 1;
    transform: translateX(0%);
  }
  85% {
    opacity: 1;
    transform: translateX(0%);
  }
  100% {
    opacity: 0;
    transform: translateX(100%);
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
  margin: 100px auto 0 auto;
  text-align: center;
  color: #fff;
  position: absolute;
  top: 0;
  animation: opa 5s linear infinite;
}
@keyframes opa {
  0% {
    opacity: 0;
  }
  15% {
    opacity: 1;
  }
  85% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}

.content h3 {
  width: 80%;
  font-weight: 100;
  margin: 20px auto 35px;
  line-height: 40px;
}

button {
  width: 200px;
  padding: 15px 0;
  text-align: center;
  margin: 0;
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

.nextbtn,
.prevbtn {
  padding: 15px 0;
  text-align: center;
  margin: 0;
  font-weight: bold;
  font-size: 30px;
  border: none;
  background: transparent;
  color: #fff;
  cursor: pointer;
}
.nextbtn {
  position: absolute;
  top: 40%;
  right: 0;
}
.prevbtn {
  position: absolute;
  top: 40%;
  left: 0;
}
.nextbtn:hover,
.prevbtn:hover {
  color: #fe7250;
  background: transparent;
  border: none;
}

@media only screen and (min-width: 741px) and (max-width: 9005px) {
  .content {
    margin: 65px auto 0 auto;
  }

  .content h1 {
    font-size: 2.5rem;
  }
  .content h3 {
    font-size: 20px;
    margin: 20px auto 25px;
  }
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
    font-size: 14px;
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
    font-size: 14px;
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