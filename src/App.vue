<template>
  <div id="app">

    <main>
      <h2>Your account</h2>
      <section class="form">

        <div class="form__decoration"></div>
        <div class="form__content">

          <div class="form__container">
            <h3>Take it all with you. Switch between devices, and pick up.</h3>

            <form action="">
              <label for="">Your name *Field required</label>
              <input type="text">

              <div class="input__wrapper">

                <label for="">
                  <select v-model="phone" name="" id="">
                    <option v-for="(prefix, index) in prefixes" :key="index" value="">{{prefix}}</option>
                  </select>
                </label>

                <label for="">
                  <input type="number">
                </label>
              </div>


              <label for="">
                <input type="radio">
              </label>
              <label for="">
                <input type="radio">
              </label>

              <label for="">Date of Birth</label>
              <div class="input__wrapper">
                <input class="normal--input" type="number">
                <input class="normal--input" type="text">
                <input class="normal--input" type="number">
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
    name: 'app',
    data() {
      return {
        phone: '',
        prefixes: []
      }
    },
    created() {
      fetch("https://api.myjson.com/bins/nkhfb").then(data=>{
        return data.json();
      }).then(entry=>{
        console.log(entry)
        for (let i=0; i<entry.length; i++){
          // console.log(`${entry[i].dial_code} (${entry[i].code})`);
          this.prefixes.push(`${entry[i].dial_code} (${entry[i].code})`);
        }
      })
    }
  }

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
  $content_background: linear-gradient(-5deg, rgba(165, 165, 180, 1) 0%, rgba(228, 235, 239, 1) 67%, rgba(231, 232, 238, 1) 94%, rgba(231, 232, 238, 1) 100%);

  $main_font_family: Rubik,
  sans-serif;

  $header_font: #ffffff;
  $main_font: #353536;
  $helper_font: #dfdfe4;
  $error_font: #f3afb0;

  $error_input: #ea3030;
  $choose_input: #1cd4a3;
  $border_input: #a2a2af;

  $arrow_button: #7841f4;
  $hover_button: inear-gradient(to right, #472a85 0%, #411998 100%);
  $gradient_button: linear-gradient(to right, #8658eb 0%, #652ae6 100%);

  // 2. Font Faces
  @font-face {
    font-family: Rubik;
    src: url('assets/fonts/Rubik-Regular.ttf');
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
    margin: 0 auto;
    max-width: 778px;
  }

  h2 {
    color: $header_font;
    font: 300 4.8rem $main_font_family;
  }

  h3 {
    max-width: 299px;
    opacity: 0.9;
    color: $main_font;
    font: 400 1.4rem/24px $main_font_family;
    letter-spacing: 0.28px;
  }

  input {
    width: 100%;
  }

  label {
    opacity: 0.5;
    color: $helper_font;
    font: 400 1.1rem/28px $main_font_family;
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
  }

  .form__content {
    background: $content_background;
    max-width: 470px;
    display: flex;
    flex-direction: column;
  }

  .form__container {
    padding-left: 5rem;
  }


  .input__wrapper {
    display: flex;
    justify-content: space-between;
  }


  // 6. Modifier
  .normal--input {
    height: 50px;
    border: 2px solid $border_input;
    background-color: $header_font;

    opacity: 0.9;
    color: $main_font;
    font: 400 1.6rem/28px $main_font_family;
  }

  .line--input {}

</style>
