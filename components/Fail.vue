<template>
  <div class="container">
    <div class="img-container">
      <img alt="success-img" src="../assets/img/fail.svg" class="success-img" />
    </div>
    <div class="orange-text-container">
      <span class="green-text">Opps !</span>
    </div>
    <div class="text-container">
      <span class="text">
        Le numéro saisi est déjà un membre de la liste des numéros favoris.
      </span>
    </div>

    <div class="back-button-container">
      <van-button class="add-button">
        ajouter un autre numéro
      </van-button>
      <van-button class="back-button">
        RETOUR A l’Accueil
      </van-button>
    </div>
  </div>
</template>

<script setup></script>

<style lang="scss" scoped>
.container {
  margin: 20px;
  .img-container {
    display: flex;
    justify-content: center;
    margin-top: 45px;
    .success-img {
      width: 180px;
      height: 180px;
    }
  }
  .orange-text-container {
    margin-top: 60px;
    display: flex;
    justify-content: center;
    .green-text {
      color: #f16e00;
      text-align: center;
      white-space: nowrap;
      font-size: 24px;
      font-style: normal;
      font-weight: 700;
      line-height: 24px;
      letter-spacing: 0.169px;
    }
  }
  .text-container {
    margin-top: 45px;
    margin-inline: 10px;
    text-align: center;
    .text {
      font-size: 18px;
      font-style: normal;
      font-weight: 400;
      line-height: 22px;
    }
  }
  .back-button-container {
    margin-top: 30px;
    display: flex;
    flex-direction: column;
    gap: 20px;
    .back-button {
      width: 100%;
      background-color: #fff;
      color: #1c1b1f;
      border-radius: 4px, #000;
      text-align: center;
      font-size: 14px;
      font-style: normal;
      font-weight: 700;
      line-height: 16px;
      letter-spacing: 1.25px;
      text-transform: uppercase;
    }
    .add-button {
      width: 100%;
      background-color: #f16e00;
      color: #fff;
      text-align: center;
      font-size: 14px;
      font-style: normal;
      font-weight: 700;
      line-height: 16px;
      letter-spacing: 1.25px;
      text-transform: uppercase;
    }
  }
}
</style>
