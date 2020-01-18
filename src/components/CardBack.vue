<template>
  <div class="card-back">
    <img class="card-back__image" :src="backgroundImage" />
    <div class="card-back__stripe"></div>
    <div class="card-back__cvv">
      {{ cvv }}
    </div>
  </div>
</template>

<script>
export default {
  props: {
    cvv: String,
    backgroundImage: String
  }
};
</script>

<style scoped lang="scss">
.card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  z-index: 100;
  transform: rotateY(180deg);

  &__image {
    width: 100%;
    height: 100%;
    border-radius: 16px;
  }

  &__stripe {
    padding: 24px;
    position: relative;
    bottom: 90%;
    opacity: 0.8;
    width: 100%;
    background-color: black;
  }

  &__cvv {
    border-radius: 4px;
    position: absolute;
    bottom: 35%;
    left: 50%;
    transform: translateX(-50%);
    width: 92%;
    background-color: white;
    color: black;
    text-align: right;
    font-size: 22px;
    min-height: 45px;
    padding: 8px;
  }

  @media screen and (max-width: 360px) {
    &__stripe {
      padding: 18px;
    }
    &__cvv {
      min-height: 36px;
      padding: 4px;
    }
  }
}
</style>
