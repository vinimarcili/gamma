<template>
  <div class="calculator default-font">
    <div class="container">
      <div class="row">
        <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
          <p class="instructions">
            Gamma is a daily calorie expenditure calculator based on the Harris and Benedict formula considering moderate daily activity
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
          <input type="radio" name="gender" id="male" value="male" v-model="gender" checked>
          <label for="male">
            <i class="fa fa-male" aria-hidden="true"></i>
          </label>
        </div>
        <div class="col-xs-12 col-sm-12 col-md-6 col-lg-3">
          <input type="radio" name="gender" id="female" value="female" v-model="gender">
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
          <input type="text" name="age" id="age" placeholder="Age" v-model="age">
        </div>
        <div class="col-xs-12 col-sm-12 col-md-6 col-lg-3">
          <label for="time" class="hidden">
            Training time (minutes)
          </label>
          <input type="text" name="time" id="time" placeholder="Training time (minutes)" v-model="time">
        </div>
        <div class="col-xs-12 col-sm-12 col-md-6 col-lg-3">
          <label for="weight" class="hidden">
            Weight (kg)
          </label>
          <input type="text" name="weight" id="weight" placeholder="Weight (kg)" v-model="weight">
        </div>
        <div class="col-xs-12 col-sm-12 col-md-6 col-lg-3">
          <label for="height" class="hidden">
            Height (cm)
          </label>
          <input type="text" name="height" id="height" placeholder="Height (cm)" v-model="height">
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
          <button type="button" v-on:click="calculate">Calculate <i class="fa fa-check" aria-hidden="true"></i></button>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
          <p class="result">Result: {{ result }} Kcal</p>
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
      result: 0,
      gender: 'male',
      age: '',
      time: '',
      weight: '',
      height: ''
    }
  },
  methods: {
    calculate: function () {
      if (this.gender === 'male') {
        this.result = (66.47 + 13.75 * this.weight + 5.0 * this.height + 6.76 * this.age) + (0.086 * this.time * this.weight)
      } else {
        this.result = (655.1 + 9.56 * this.weight + 1.85 * this.height + 4.68 * this.age) + (0.086 * this.time * this.weight)
      }

      this.result = this.result.toFixed(2)
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
        border: 3px solid $green;
        font-weight: 600;
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
      &:focus {
        outline: none;
      }
      &:active{
        font-size: 15px;
      }
    }
  }
</style>
