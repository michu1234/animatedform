<template>
  <div id="app">

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
                <input id="male" name="gender" type="radio">
                <label class="form__content-gender" for="male"></label>
                <input id="female" name="gender" type="radio">
                <label class="form__content-gender" for="female"></label>
              </div>




              <label for="">Date of Birth</label>
              <div class="input__wrapper">
                <input placeholder="01" class="normal--input narrow--input" type="number">
                <hr>
                <input placeholder="January" class="normal--input" type="text">
                <hr>
                <input placeholder="1990" class="normal--input" type="number">
              </div>


              <button>continue</button>
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
// 8. Animations
// 9. Media Queries
 
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

  $arrow_button: #7841f4;
  $hover_button: inear-gradient(to right, #472a85 0%, #411998 100%);
  $gradient_button: linear-gradient( to right,
  #8658eb 0%,
  #652ae6 100%); // 2. Font Faces
  @font-face {
    font-family: Rubik;

    src: url("assets/fonts/Rubik-Regular.ttf");
  }

  // 3. Base
  html {
    font-size: 62.5%;
  }

  body {
    max-width: 1366px;
    background: $main_background;
  }

  main {
    display: flex;
    flex-direction: column;
    max-width: 778px; // margin: 0 auto;
  }

  h2 {
    color: $header_font;
    font: 300 4.8rem $main_font_family;
  }

  h3 {
    max-width: 299px;
    color: $main_font;
    font: 400 1.4rem/24px $main_font_family;
    opacity: 0.9;

    letter-spacing: 0.28px;
  }

  img {
    max-width: 100%;
    height: auto;
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
    margin-top: 15px;
    background: transparent;
    -webkit-appearance: none;
    outline: none;

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

    letter-spacing: 0.32px;
    text-transform: uppercase;
  }

  label {
    color: $helper_font;
    font: 400 1.1rem/28px $main_font_family;
    opacity: 0.5;
  }

  hr {
    width: 4rem;
    height: 2px;
    margin: 24px 1rem 24px 1rem;
    background: $border_input;
  }

  // 4. Layout
  .form {
    display: flex;
  }

  // 5. Block + element
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
    display: flex;
    flex-direction: column;
    max-width: 470px;
    background: $content_background;
  }

  .form__container {
    padding: 0 5rem 0 5rem;
  }

  .input__wrapper {
    display: flex;
    justify-content: space-between;
  }

  .form__content-gender {
    display: block;
    width: 50px;
    height: 50px;
    border: 2px solid $border_input;
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

</style>
