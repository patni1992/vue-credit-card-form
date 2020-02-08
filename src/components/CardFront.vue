<template>
  <div class="card-front">
    <img class="card-front__image" :src="backgroundImage" />
    <img class="card-front__symbol" :src="symbolImage" />
    <img class="card-front__chip" :src="'/img/chip.png'" />
    <p class="card-front__number">{{ cardNumber }}</p>
    <div class="card-front__info">
      <p>Expires</p>
      <p class="card-front__expires value">
        {{ expireMonth || "MM" }} / {{ (expireYear && sliceYear) || "YY" }}
      </p>
    </div>
    <div class="card-front__info left">
      <p>Card Owner</p>
      <p class="value">{{ name || "name" }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    backgroundImage: String,
    symbolImage: String,
    cardNumber: String,
    expireMonth: String,
    expireYear: String,
    name: String
  },
  computed: {
    sliceYear() {
      return this.expireYear.toString().slice(2);
    }
  }
};
</script>

<style scoped lang="scss">
$x-space: 24px;
$y-space: 16px;
.card-front {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  z-index: 100;

  &__image {
    width: 100%;
    height: 100%;
    border-radius: 16px;
  }

  &__number {
    position: absolute;
    font-size: 26px;
    top: 35%;
    left: 24px;
  }

  &__chip {
    position: absolute;
    top: $y-space;
    left: $x-space;
    height: 44px;
  }

  &__symbol {
    position: absolute;
    top: $y-space;
    right: $x-space;
    height: 48px;
  }

  &__info {
    position: absolute;
    bottom: $y-space;
    right: $x-space;
    color: white;
    text-align: left;
    margin: 0;

    &.left {
      left: $x-space;
    }

    .value {
      font-weight: bold;
    }

    p {
      margin: 0;
    }
  }
  &__expires {
    right: auto;
    left: $x-space;
  }
  @media screen and (max-width: 480px) {
    &__number {
      font-size: 22px;
    }
    &__info {
      font-size: 12px;
    }
    &__chip {
      height: 34px;
    }
    &__symbol {
      height: 38px;
    }
  }
  @media screen and (max-width: 360px) {
    &__number {
      font-size: 18px;
    }
  }
}
</style>
