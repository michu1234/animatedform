<template>
  <div id="app">
<div class="background">
  <img class="background__bloob" src="./assets/img/gredient@1X.png" alt="">
  <img class="background__lines-top" src="./assets/img/lines.png" alt="">
  <img class="background__lines-bottom" src="./assets/img/LINES@1X.png" alt="">
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
              <label for="">Your name *Field required</label>
              <input class="line--input" type="text">

              <div class="input__wrapper">

                <label for="">
                  <select class="line--input" v-model="phone" name="" id="">
                    <option v-for="(prefix, index) in prefixes" :key="index" value="">{{prefix}}</option>
                  </select>
                </label>

                <label for="">
                  <input class="line--input" type="number">
                </label>
              </div>

              <div class="input__wrapper">
                <input id="male" name="male" type="radio">
                <label class="form__content-gender label--male" for="male"></label>
                <input id="female" name="male" type="radio">
                <label class="form__content-gender label--female" for="female"></label>
              </div>




              <label for="">Date of Birth</label>
              <div class="input__wrapper">
                <input placeholder="01" class="normal--input narrow--input" type="number">
                <hr>
                <input placeholder="January" class="normal--input" type="text">
                <hr>
                <input placeholder="1990" class="normal--input" type="number">
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
        phone: "",
        prefixes: [],
      };
    },
    created() {
      fetch("https://api.myjson.com/bins/nkhfb")
        .then(data => {
          return data.json();
        })
        .then(entry => {
          console.log(entry);
          for (let i = 0; i < entry.length; i++) {
            // console.log(`${entry[i].dial_code} (${entry[i].code})`);
            this.prefixes.push(`${entry[i].dial_code} (${entry[i].code})`);
          }
        });
    }
  };

</script>

<style lang="scss">
  /* 
Table of contents
=====================
// 1. Variables
// 2. Font Faces
// 3. Base
// 4. Layout
// 5. Block + element
// 6. Modifier
// 7. State
// 8. Placeholders
// 9. Animations
// 10. Media Queries
 
=====================
*/

  // 1. Variables
  $main_background: #242424;
  $content_background: linear-gradient( -5deg,
  rgba(165, 165, 180, 1) 0%,
  rgba(228, 235, 239, 1) 5%,
  rgba(231, 232, 238, 1) 10%,
  rgba(249, 249, 251, 1) 100%);
  $main_font_family: Rubik,
  sans-serif;
  $header_font: #fff;
  $main_font: #202020;
  $helper_font: #dfdfe4;
  $error_font: #f3afb0;

  $error_input: #ea3030;
  $choose_input: #1cd4a3;
  $border_input: #dcdce1;

  $arrow_button: #411a96;
  $gradient_button: linear-gradient( to right,
  #8658eb 0%,
  #652ae6 100%); // 2. Font Faces
  @font-face {
    font-family: Rubik;

    src: url("assets/fonts/Rubik-Regular.ttf");
  } // 3. Base
  html {
    font-size: 62.5%;
  }

  body {
    max-width: 1366px;
    background-color: $main_background;
    overflow: hidden;
  }

  main {
    @extend %flex;
    @extend %box--center;
    flex-direction: column;
    max-width: 778px;
  }

  h2 {
    color: $header_font;
    font: 300 4.8rem $main_font_family;
    margin: 6.7rem 12.4rem 52px auto;
  }

  h3 {
    max-width: 299px;
    color: $main_font;
    font: 400 1.38rem/24px $main_font_family;
    opacity: 0.9;

    letter-spacing: 0.28px;
  }

  img {
    max-width: 100%;
    height: auto;
    vertical-align: middle;
  }

  input {
    width: 100%;
    background-color: $header_font;
    color: $main_font;
    font: 400 1.6rem/28px $main_font_family;
    padding-left: 1.5rem;
  }

  input[type=radio] {
    // display: none;
    position: absolute;
    border: 2px solid $border-input;
    width: 15px;
    height: 15px;
    margin-left: 43px;
    margin-top: 18px;
    background: transparent;
    -webkit-appearance: none;
    outline: none;
    @extend %pointer;

    &:nth-of-type(2) {
      margin-top: 18px;
      left: 134px;
    }

    &:checked {
      border: 2px solid $choose_input;
      background: transparent url("assets/img/fill@1X.png") no-repeat center center;

      &+label {
        border: 2px solid $choose_input;
      }
    }
  }

  select {
    border: none;
    outline: none;
    background: transparent url("assets/img/dropdownarrow@1X.png") no-repeat center center;
    color: $main_font;
    font: 400 1.6rem/28px $main_font_family;
    height: 60px;
    margin-right: 1.5rem;
    @extend %pointer;

    letter-spacing: 0.32px;
    text-transform: uppercase;
  }

  label {
    color: $helper_font;
    font: 400 1.1rem/28px $main_font_family;
    opacity: 0.5;
    @extend %pointer;
  }

  hr {
    width: 4rem;
    height: 2px;
    margin: 24px 1rem 24px 1rem;
    background: $border_input;
  }
  
   // 4. Layout

   #app {
  
   }

  .form {
    @extend %flex;
  } 

  .background {
    position: absolute;
    width: 100%;
    height: 100vh;
  }
  
  // 5. Block + element

  .background__bloob {
    will-change: auto;
    transform: translate(-3%, -2%);
  }

  .background__lines-top {
    margin-top: -480px;
    margin-left: -500px;
  }

  .background__lines-bottom {
    position: absolute;
    right: -20%;
    bottom: -40%;
  }

  .form__decoration {
    width: 308px;
    height: 552px;
    background: url("assets/img/layer1.png") no-repeat top left;
    position: relative;

    &-img {
      position: absolute;
      z-index: 1;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
  }

  .form__content {
    @extend %flex;
    flex-direction: column;
    max-width: 470px;
    background: $content_background;
    position: relative;
  }

  .form__container {
    padding: 0 5rem 0 5rem;
  }

  input[name=female]{
    margin-right: 3rem;
  }

  .input__wrapper {
    @extend %flex;
    justify-content: space-between;
  }

  .form__content-gender {
    display: block;
    width: 50px;
    height: 50px;
    border: 2px solid $border_input;
  }

  .form__button {
    position: absolute;
    right: -50px;
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
      transition: all .3s;
      &:hover {
        background-color: $arrow_button;
        transition: all .3s;
      }
    }
  } 
  
  // 6. Modifier

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
    padding: 1.5rem;
    margin-bottom: 25px;
    outline: none;
  }

  .label--female {
    margin-right: auto;
     background: url(assets/img/female.png) no-repeat center center;
  }

  .label--male {
    margin-right: 3rem;
    background: url(assets/img/male.png) no-repeat center center;
  }
  
// 8. Placeholders

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

</style>
