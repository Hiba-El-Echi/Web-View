<template>
  <div class="container">
    <div class="img-container">
      <img
        alt="success-img"
        src="../assets/img/success.svg"
        class="success-img"
      />
    </div>
    <div class="green-text-container">
      <span class="green-text">Numéro ajouter avec succès</span>
    </div>
    <div class="text-container">
      <span class="text">
        Le numéro à été ajouter avec succès dans la liste des numéros favoris
      </span>
    </div>
    <div class="back-button-container"> 
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
  .green-text-container {
    margin-top: 60px;
    display: flex;
    justify-content: center;
    .green-text {
      color: #50be87;

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
}
</style>
