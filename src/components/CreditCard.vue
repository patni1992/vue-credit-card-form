<template>
  <div class="credit-card">
    <div
      class="credit-card__inner"
      :class="{
        'show-back': showBack
      }"
    >
      <card-front
        :backgroundImage="backgroundImage"
        :symbolImage="symbolImage"
        :cardNumber="cardNumber"
        :expireMonth="expireMonth"
        :expireYear="expireYear"
        :name="name"
      />
      <card-back :cvv="cvv" :backgroundImage="backgroundImage" />
    </div>
  </div>
</template>

<script>
import CardFront from "./CardFront";
import CardBack from "./CardBack";
export default {
  components: {
    CardFront,
    CardBack
  },
  data() {
    return {
      backgroundImage: this.randomCard()
    };
  },
  methods: {
    randomCard() {
      return "/img/card-" + (Math.floor(Math.random() * 5) + 1) + ".jpg";
    }
  },
  props: {
    cardNumber: String,
    expireMonth: String,
    expireYear: String,
    cvv: String,
    name: String,
    showBack: Boolean,
    symbolImage: String
  }
};
</script>

<style scoped lang="scss">
.credit-card {
  font-family: "Source Code Pro", monospace;
  max-width: 420px;
  width: 100%;
  height: 245px;
  background-color: transparent;
  color: white;
  perspective: 1000px;
  display: inline-block;

  &:hover &__inner {
    transform: rotateY(180deg);
  }

  &__inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.6s;
    transform-style: preserve-3d;
  }

  @media screen and (max-width: 480px) {
    height: 210px;
  }

  @media screen and (max-width: 360px) {
    height: 180px;
  }
}
.show-back {
  transform: rotateY(180deg);
  &:hover {
    transform: rotateY(0deg);
  }
}
</style>
