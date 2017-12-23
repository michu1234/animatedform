<template>
  <div id="app">

    <section class="form">
      <h2>Your account</h2>
      <div class="form__decoration"></div>
      <div class="form__content">

        <h3>Take it all with you. Switch between devices, and pick up.</h3>

        <form action="">
          <label for="">Your name *Field required</label>
          <input type="text">

          <div class="input__wrapper">

            <label for="">
              <select name="" id="">
                <option value=""></option>
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


          <div class="input__wrapper">
            <label for="">Date of Birth</label>
            <input type="number">
            <input type="text">
            <input type="number">
          </div>


          <button>continue</button>
        </form>
      </div>
    </section>


  </div>
</template>

<script>
  export default {
    name: 'app',
    data() {
      return {
        msg: 'Welcome to Your Vue.js App'
      }
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

$header_font: #ffffff;
$main_font: #6a6a6b;
$helper_font: #d9d9df;
$error_font: #f3afb0; 

$error_input: #ea3030;
$choose_input: #1cd4a3;

$arrow_button: #7841f4;
$hover_button: inear-gradient(to right, #472a85 0%, #411998 100%);
$gradient_button: linear-gradient(to right, #8658eb 0%, #652ae6 100%);









</style>
