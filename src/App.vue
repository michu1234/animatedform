<template>
<div id="app">
  <div class="background">
    <img class="background__bloob" src="./assets/img/gredient@1X.png" alt="">
    <img class="background__lines-top" src="./assets/img/lines.png" alt="">
  </div>
  <div class="background-bottom">
    <img class="background-bottom__lines" src="./assets/img/LINES@1X.png" alt="">
  </div>
  <main>
    <h2>Your account</h2>
    <section class="form">

      <div class="form__decoration">
        <img class="form__decoration-img" src="./assets/img/lines_decor.png" alt="">
      </div>
      <div class="form__content">

        <div class="form__container">
          <h3>Take it all with you. Switch between devices, and pick up.</h3>

          <form action="">

            <label class="form__name" for=""><span>Your name</span>
              <span :class="[errorName ? 'el--display' : 'el--hide', 'el--alert' ]"> *Field required</span>
            </label>

            <input @blur="!name ? errorName = true : errorName = false" @focus="resetError" v-model="name" :class="[errorName ? 'input--error' : 'line--input' ]" type="text" autofocus>

            <div class="input__wrapper">

              <label for="">Mobile
                  <select class="line--input" v-model="phone" name="" id="">
                    <option v-for="(prefix, index) in prefixes" :key="index" value="">{{prefix}}</option>
                  </select>
                </label>

              <label class="form__number" for="">
                  <span :class="[errorPhone ? 'el--display' : 'el--hide',]">*6 digit number required</span>
                  <input @blur="validateIt" :class="[errorPhone ? 'input--error' : 'line--input']" v-model="phoneNumber" type="number">
                </label>
            </div>
              <label for="">Gender</label>
            <div class="input__wrapper">
              <input id="male" v-model="gender" value="male" name="male" type="radio">
              <label class="form__content-gender label--male" for="male"></label>
              <input id="female" v-model="gender" value="female" name="male" type="radio">
              <label class="form__content-gender label--female" for="female"></label>
            </div>

            <label for="">Date of Birth</label>
            <div class="input__wrapper">
              <input placeholder="01" v-model="day" class="normal--input narrow--input" type="number">
              <hr>
              <input placeholder="January" v-model="month" class="normal--input" type="text">
              <hr>
              <input placeholder="1990" v-model="year" class="normal--input" type="number">
            </div>


            <div class="form__button">continue
              <span class="form__button-hover">
                  <img src="./assets/img/arrow.png" alt="">
                </span>
            </div>

          </form>
        </div>
      </div>
    </section>
  </main>


</div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      errorName: false,
      errorPhone: false,
      phone: "",
      phoneNumber: "",
      name: "",
      gender: "",
      day: "",
      month: "",
      year: "",
      prefixes: []
    };
  },
  created() {
    fetch("https://api.myjson.com/bins/nkhfb")
      .then(data => {
        return data.json();
      })
      .then(entry => {
        for (let i = 0; i < entry.length; i++) {
          this.prefixes.push(`${entry[i].dial_code} (${entry[i].code})`);
        }
      });
  },
  methods: {
    validateIt() {
      let inputLength = this.phoneNumber.length;
      inputLength < 6 ? (this.errorPhone = true) : (this.errorPhone = false);
    },
    resetError() {
      this.errorName = false;
    }
  }
};
</script>

<style lang="scss">
/*
Table of contents
=====================
// 1. Variables
// 2. Placeholders
// 3. Functions
// 4. Font Faces
// 5. Base
// 6. Layout
// 7. Block + element
// 8. Modifier
// 9. State
// 10. Animations
// 11. Media Queries
=====================
*/
// 1. Variables
$main_background: #242424;
$content_background: linear-gradient(-5deg, rgba(165, 165, 180, 1) 0%, rgba(228, 235, 239, 1) 5%, rgba(231, 232, 238, 1) 10%, rgba(249, 249, 251, 1) 100%);
$main_font_family: Rubik, sans-serif;
$header_font: #fff;
$main_font: #202020;
$helper_font: #a2a2af;
$error_font: #f3afb0;
$error_input: #ea3030;
$choose_input: #1cd4a3;
$border_input: #dcdce1;
$radio_background: #ecedf2;
$arrow_button: #411a96;
$gradient_button: linear-gradient(to right, #8658eb 0%, #652ae6 100%); // 2. Placeholders
%text--center {
    text-align: center;
}
%box--center {
    margin: 0 auto;
}
%flex {
    display: flex;
}
%pointer {
    cursor: pointer;
}
%transition {
    transition: all 0.3s;
}
// 3. Functions
@function prc($el, $target) {
    @return (100% * $el) / $target;
}
// 4. Font Faces
// @font-face {
//     font-family: Rubik;
//     src: url("assets/fonts/Rubik-Regular.ttf");
// }
// 5. Base
* {
    box-sizing: border-box;
    outline: none;
}
html {
    font-size: 62.5%;
}
body {
    max-width: 1366px;
    background-color: $main_background;
    overflow-x: hidden;
    margin: 0;
}

#app {
  overflow:hidden;
  position: relative;
  min-height: 800px;
}

main {
    @extend %flex;
    @extend %box--center;
    flex-direction: column;
    max-width: 778px;
    height: auto;
}
h2 {
    color: $header_font;
    font: 300 4.8rem $main_font_family;
    @extend %box--center;
    z-index: 1;
    margin: 50px prc(124, 1366) 52px auto;
}
h3 {
    max-width: 299px;
    color: $main_font;
    font: 400 1.38rem/24px $main_font_family;
    letter-spacing: 0.28px;
    margin: 0 0 25px 0;
}
img {
    max-width: 100%;
    height: auto;
    vertical-align: middle;
}
input {
    width: 100%;
    background-color: transparent;
    color: $main_font;
    font: 400 1.6rem/28px $main_font_family;
    padding-left: 1.5rem;
}
input[type="radio"] {
    // display: none;
    position: absolute;
    border: 2px solid $border-input;
    width: 15px;
    height: 15px;
    margin-left: 40px;
    margin-top: 18px;
    background-color: $radio_background;
    -webkit-appearance: none;
    outline: none;
    z-index: 1;
    @extend %pointer;
    &:nth-of-type(2) {
        margin-top: 18px;
        transform: translateX(80px);
    }
    &:checked {
        border: 2px solid $choose_input;
        background: $radio_background url("assets/img/fill@1X.png") no-repeat center center;
        & + label {
            border: 2px solid $choose_input;
            @extend %transition;
        }
    }
}
select {
    border: none;
    outline: none;
    background: transparent url("assets/img/dropdownarrow@1X.png") no-repeat center center;
    color: $main_font;
    font: 400 1.6rem/28px $main_font_family;
    height: 40px;
    margin-right: 1.5rem;
    @extend %pointer;
    letter-spacing: 0.32px;
    text-transform: uppercase;
}
label {
    color: $helper_font;
    font: 400 1.1rem/28px $main_font_family;
    @extend %pointer;
    &:nth-of-type(3){
      display: block;
      padding: 10px 0 0 0;
    }
}
hr {
    width: 4rem;
    height: 2px;
    margin: 24px 1rem;
    background: $border_input;
}
// 6. Layout
#app {}
.form {
    @extend %flex;
    margin: 0 6% 0 6%;
}
.background {
    position: absolute;
    width: 100%;
    height: 100vh;
    animation: bloob 15s ease-out forwards;
}
// 7. Block + element
.background__bloob {
    will-change: auto;
    // animation: bloob 16s forwards;
}
.background__lines-top {
    transform: translate(-69%, -2%);
    position: absolute;
    z-index: -1;
}
.background-bottom__lines {
    position: absolute;
    right: -20%;
    bottom: -40%;
    animation: bloob_lines 5s forwards;
}
.form__decoration {
    display: none;
    animation: decor_animation 3s forwards;
}
.form__content {
    @extend %flex;
    @extend %box--center;
    flex-direction: column;
    max-width: 470px;
    height: 552px;
    background: $content_background;
    position: relative;
    padding-top: 40px;
}
.form__container {
    padding: 0 2%;
}
input[name="female"] {
    margin-right: 2rem;
}
.input__wrapper {
    @extend %flex;
    justify-content: space-between;
    margin-top: 10px;
}

.form__name {
  display: flex;
}

.form__number {
  text-align: right;
}

.form__content-gender {
    display: block;
    width: 50px;
    height: 50px;
    border: 2px solid $border_input;
}
.form__button {
    position: absolute;
    right: 50%;
    transform: translate(50%);
    bottom: -25px;
    width: 237px;
    height: 50px;
    background: $gradient_button;
    color: #ffffff;
    font: 300 1.2rem/50px $main_font_family;
    text-transform: uppercase;
    @extend %pointer;
    @extend %text--center;
    &-hover {
        display: inline-block;
        width: 50px;
        height: 50px;
        right: 0;
        position: absolute;
        @extend %transition;
        &:hover {
            background-color: $arrow_button;
            @extend %transition;
        }
    }
}
// 8. Modifier
.normal--input {
    height: 50px;
    border: 2px solid $border_input;
}
.narrow--input {
    max-width: 5rem;
}
.line--input {
    border: none;
    background: transparent;
    border-bottom: 2px solid $border-input;
    padding: .45rem;
    margin-bottom: 15px;
    outline: none;
}
.label--female {
    margin-right: auto;
    background: url("assets/img/female.png") no-repeat center center;
}
.label--male {
    margin-right: 3rem;
    background: url("assets/img/male.png") no-repeat center center;
}

.input--error {
    border: none;
    background: transparent;
    border-bottom: 2px solid $error_input;
    margin-bottom: 15px;
    padding: .45rem;
    outline: none;
}
// 9. State
.el--display {
    visibility: visible;
    color: $error_input;
    text-align: right;
    display: inline-block;
}
.el--hide {
    visibility: hidden;
}

.el--alert {
  margin-left: auto;
  text-align: right;
}

// 10. Animations
@keyframes bloob {
    0% {
        transform: translate(-3%, -2%) scale(1);
        transform-origin: 0 0;
    }
    100% {
        transform: translate(-3%, -2%) scale(1.1);
        transform-origin: 0 0;
    }
}
@keyframes bloob_lines {
    0% {
        transform: translate(0, 1000px);
    }
    100% {
        transform: translate(0, 0);
    }
}
@keyframes decor_animation {
    0% {
        width: 0;
        margin-left: 308px;
    }
    100% {
        width: 308px;
        margin-left: 0;
    }
}
@keyframes decor_lines {
    0% {
        display: none;
    }
    50% {
        width: 0;
    }
    100% {
        width: 100%;
    }
}
// 11. Media Queries
@media screen and (min-width: 500px) {
    .form__container {
        padding: 0 4rem;
    }
}
@media screen and (min-width: 680px) {
    .form__decoration {
        display: block;
        width: 308px;
        height: 552px;
        position: relative;
        background-color: $main_background;
        &:after {
            content: "";
            display: block;
            background: url("assets/img/layer1.png") no-repeat top left;
            opacity: 0.1;
            top: 0;
            left: 0;
            bottom: 0;
            right: 0;
            position: absolute;
        }
        &-img {
            position: absolute;
            z-index: 1;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            animation: decor_lines 3s 3s forwards;
        }
    }
    .form__button {
        position: absolute;
        right: -50px;
        transform: translate(0);
    }
    // h2 {
    //     margin: 67px prc(124, 1366) 52px auto;
    // }
}
</style>
