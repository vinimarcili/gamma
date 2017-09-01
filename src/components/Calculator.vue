<template>
  <div class="calculator default-font">
    <div class="container">
      <div class="row">
        <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
          <p class="instructions">
            Mussum Ipsum, cacilds vidis litro abertis. In elementis mé pra quem é amistosis quis leo. Tá deprimidis, eu conheço uma cachacis que pode alegrar sua vidis. Copo furadis é disculpa de bebadis, arcu quam euismod magna. Posuere libero varius. Nullam a nisl ut ante blandit hendrerit. Aenean sit amet nisi.
          </p>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
          <p class="float-text">
            Select gender
          </p>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-12 col-md-6 col-lg-3 col-lg-offset-3">
          <input type="radio" name="gender" id="male">
          <label for="male">
            <i class="fa fa-male" aria-hidden="true"></i>
          </label>
        </div>
        <div class="col-xs-12 col-sm-12 col-md-6 col-lg-3">
          <input type="radio" name="gender" id="female">
          <label for="female">
            <i class="fa fa-female" aria-hidden="true"></i>
          </label>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-12 col-md-6 col-lg-3">
          <label for="age" class="hidden">
            Age
          </label>
          <input type="text" name="age" id="age" placeholder="Age">
        </div>
        <div class="col-xs-12 col-sm-12 col-md-6 col-lg-3">
          <label for="time" class="hidden">
            Training time (minutes)
          </label>
          <input type="text" name="time" id="time" placeholder="Training time (minutes)">
        </div>
        <div class="col-xs-12 col-sm-12 col-md-6 col-lg-3">
          <label for="weight" class="hidden">
            Weight (kg)
          </label>
          <input type="text" name="weight" id="weight" placeholder="Weight (kg)">
        </div>
        <div class="col-xs-12 col-sm-12 col-md-6 col-lg-3">
          <label for="height" class="hidden">
            Height (cm)
          </label>
          <input type="text" name="height" id="height" placeholder="Height (cm)">
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
          <button type="button">Calculate <i class="fa fa-check" aria-hidden="true"></i></button>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
          <p class="result">Result: $var Kcal</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'calculator',
  data () {
    return {
      msg: ''
    }
  }
}
</script>

<style lang="scss" scoped>
  $transition: all 0.3s ease;

  $green: rgba(20, 220, 20, 0.4);
  $green-light: rgba(50, 205, 50, 0.5);

  .calculator {
    p {
      margin: 15px auto;
      display: inline-block;
      &.float-text{
        margin: 15px auto 5px;
      }
      &.instructions {
        max-width: 500px;
        background: $green;
        border-radius: 10px;
        padding: 15px;
      }
      &.result {
        max-width: 500px;
        background: $green-light;
        border-radius: 10px;
        padding: 15px;
      }
    }
    input {
      &:focus {
        outline: none;
      }
      &[type="radio"] {
        position: absolute;
        left: -9999px;
        & + label {
          cursor: pointer;
          background: $green;
          width: 50px;
          height: 50px;
          border: 1px solid $green-light;
          border-radius: 50%;
          line-height: 50px;
          font-size: 35px;
          margin: 15px;
          color: #fff;
          transition: $transition;
          &:hover{
            background: #fff;
            color: $green-light;
          }
        }
        &:not(:checked) {
          & + label {
            border: none;
          }
        }
        &:checked {
          & + label {
            background: darken($green, 20%);
            color: #fff;
            border-width: 3px;
            line-height: 47px;
          }
        }
      }
      &[type="text"] {
        transition: $transition;
        max-width: 500px;
        width: 100%;
        height: 40px;
        background: $green;
        border: none;
        border-radius: 5px;
        margin: 15px auto;
        color: #fff;
        padding: 0 15px;
        font-size: 20px;
        border: 1px solid rgba(0, 0, 0, 0);
        &:hover, &:focus {
          border-color: #fff;
        }
        &::placeholder {
          color: #fff;
        }
      }
    }
    button {
      border: none;
      max-width: 500px;
      background: $green-light;
      border-radius: 10px;
      padding: 15px;
      transition: $transition;
      &:hover{
        background: #fff;
        color: darken($green, 20%);
      }
    }
  }
</style>
