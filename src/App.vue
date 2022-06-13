<template>
  <div id="app">
    <main class="yellow__container">
      <h1>Buddy generator</h1>
      <div class="yellow__container__window">
        <div
          class="yellow__container__window__buddy"
          v-bind:style="{
            width: selectedWidth + 'px',
            height: selectedHeight + 'px',
          }"
        >
          <div class="yellow__container__window__buddy__head"></div>
          <div class="yellow__container__window__buddy__left-arm"></div>
          <div class="yellow__container__window__buddy__right-arm"></div>
          <img
            class="yellow__container__window__buddy__outfit-haut"
            alt=""
            v-if="imageHaut"
            :src="require(`@/assets/${imageHaut}`)"
            @click="imageHaut = ''"
          />
          <img
            class="yellow__container__window__buddy__outfit"
            alt=""
            v-if="image"
            :src="require(`@/assets/${image}`)"
            @click="image = ''"
          />

          <div class="yellow__container__window__buddy__left-leg"></div>
          <div class="yellow__container__window__buddy__right-leg"></div>
        </div>
      </div>
      <div class="yellow__container__selection-fields">
        <div class="yellow__container__selection-fields__height">
          <label
            class="yellow__container__selection-fields__height__label"
            for="height"
            >Height {{ selectedHeight }}</label
          >
          <input
            class="yellow__container__selection-fields__height__input"
            type="range"
            value="125"
            min="100"
            max="150"
            name="height"
            v-model="selectedHeight"
          />
        </div>
        <div class="yellow__container__selection-fields__width">
          <label
            class="yellow__container__selection-fields__width__label"
            for="width"
            >Width {{ selectedWidth }}</label
          >
          <input
            class="yellow__container__selection-fields__width__input"
            type="range"
            value="125"
            min="100"
            max="150"
            name="width"
            v-model="selectedWidth"
          />
        </div>
        <div class="yellow__container__selection-fields__outfits">
          <img
            class="yellow__container__selection-fields__outfits__choice"
            v-for="(img, i) in imagesHaut"
            :key="i"
            :src="require(`@/assets/${img}`)"
            alt=""
            @click="imageHaut = img"
          />
        </div>
        <div class="yellow__container__selection-fields__outfits">
          <img
            class="yellow__container__selection-fields__outfits__choice"
            v-for="(img, i) in images"
            :key="i"
            :src="require(`@/assets/${img}`)"
            alt=""
            @click="image = img"
          />
        </div>
      </div>
    </main>
  </div>
</template>

<style lang="scss">
$gutter-mobile: 16px;
$gutter-desktop: 24px;
$breakpoint: 576px;
$main-yellow: rgb(250, 225, 0);

* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
  font-family: "Poppins", sans-serif;
  color: white;
  text-align: center;
  border-radius: 8px;
}
#app {
  display: flex;
  justify-content: center;
  width: 100%;
  padding: $gutter-desktop;
}
.yellow__container {
  width: clamp(304px, 100%, 400px);
  box-shadow: 2px 0 10px 2px #cecece;
  background-color: $main-yellow;
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: $gutter-desktop;
  padding: $gutter-mobile;

  &__window {
    width: 100%;
    // border: white solid 1px;
    // box-shadow: inset 2px 0 10px 2px #ffffff;
    display: flex;
    justify-content: center;
    padding: 32px;
    align-items: center;

    &__buddy {
      width: 100px;
      height: 120px;
      background-color: white;
      // border-radius: 40px;
      border-radius: 50% 50% 50% 50% / 70% 70% 30% 30%;
      position: relative;

      &__head {
        background-color: rgb(255, 255, 255);
        border-radius: 100%;
        width: 60px;
        height: 60px;
        position: absolute;
        top: -40px;
        left: 50%;
        transform: translateX(-50%);
      }
      &__left-arm {
        background-color: rgb(255, 255, 255);
        // border-radius: 100%;
        border-radius: 50% 50% 50% 50% / 20% 20% 80% 80%;
        width: 40px;
        height: 90px;
        position: absolute;
        top: -5%;
        left: 5%;
        transform: rotate(60deg);
      }
      &__right-arm {
        background-color: rgb(255, 255, 255);
        // border-radius: 100%;
        border-radius: 50% 50% 50% 50% / 20% 20% 80% 80%;
        width: 40px;
        height: 90px;
        position: absolute;
        top: -5%;
        right: 5%;
        transform: rotate(-60deg);
      }
      &__outfit {
        width: 40px;
        height: 90px;
        position: absolute;
        top: -40px;
        left: 50%;
        transform: translateX(-50%);

        &:hover {
          cursor: pointer;
        }

        &-haut {
          width: 40px;
          height: 90px;
          position: absolute;
          top: -60px;
          left: 50%;
          transform: translateX(-50%);

          &:hover {
            cursor: pointer;
          }
        }
      }
      &__left-leg {
        background-color: rgb(255, 255, 255);
        // border-radius: 100%;
        border-radius: 50% 50% 50% 50% / 20% 20% 80% 80%;
        width: 40px;
        height: 70px;
        position: absolute;
        top: 70%;
        left: 0%;
        transform: rotate(10deg);
      }
      &__right-leg {
        background-color: rgb(255, 255, 255);
        // border-radius: 100%;
        border-radius: 50% 50% 50% 50% / 20% 20% 80% 80%;
        width: 40px;
        height: 70px;
        position: absolute;
        top: 70%;
        right: 0%;
        transform: rotate(-10deg);
      }
    }
  }

  &__selection-fields {
    width: 100%;
    display: flex;
    flex-direction: column;
    gap: 24px;

    &__height,
    &__width,
    &__outfits {
      background-color: white;
      width: 100%;
      height: 60px;
      display: flex;
      gap: 16px;
      align-items: center;
      padding: $gutter-mobile;
      justify-content: center;

      &__label {
        color: $main-yellow;
        font-weight: 600;
      }

      &__input {
        width: 100%;
        -webkit-appearance: none; /*nécessaire pour Chrome */
        padding: 0; /* nécessaire pour IE */
        outline: none;
        background: rgb(255, 238, 0);
        cursor: pointer;
      }

      &__choice {
        width: 40px;
        z-index: 2;

        &:hover {
          cursor: pointer;
        }
      }
    }
  }
}

input[type="range"]::-webkit-slider-thumb {
  width: 40px;
  -webkit-appearance: none;
  height: 40px;
  background: #ffffff;
  border-radius: 8px;
  box-shadow: 2px 0 5px 1px #cecece;
}
</style>
<script>
export default {
  name: "App",
  components: {
    // HelloWorld
  },
  data() {
    return {
      selectedHeight: 125,
      selectedWidth: 125,
      image: "",
      images: [
        "mustache.svg",
        "less-than.svg",
        "face-mask.svg",
        "circle-medium.svg",
        "epsilon.svg",
      ],
      imageHaut: "",
      imagesHaut: [
        "sunglasses.svg",
        "eye.svg",
        "eye-outline.svg",
        "safety-goggles.svg",
        "glasses.svg",
      ],
    };
  },
};
</script>
