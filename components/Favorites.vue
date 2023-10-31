<template>
  <div class="container">
    <div class="text-container">
      <span class="favoris">
        Liste des numéros favoris
      </span>
      <br />
      <span class="number">
        <span class="num">{{ favorites.length }} /5</span>
        numéros favoris
      </span>
    </div>
    <div class="search-container">
      <van-search v-model="value" placeholder="Identifiant" />
    </div>
    <div
      class="favorites-list"
      v-for="favorite in favorites"
      :key="favorite.id"
    >
      <van-swipe-cell :right-width="80">
        <template #left>
          <div class="modif-img">
            <img src="./../assets/img/modif.svg" />
          </div>
        </template>
        <div class="favorite-list-item">
          <img src="./../assets/img/contact.svg" />
          <div class="item-element">
            <span class="name">{{ favorite.name }}</span>
            <br />
            <span class="number">{{ favorite.number }}</span>
          </div>
        </div>
        <template #right>
          <div class="delete-img" @click="showDelete()">
            <img src="./../assets/img/delete.svg" />
          </div>
        </template>
      </van-swipe-cell>
      <van-action-sheet v-model:show="show" title="">
        <div class="content">
          <div class="img-container">
            <img src="../assets/img/delete-icon.svg" />
          </div>
          <div class="orange-text-container">
            <span class="text">Supprimer le numéro favori</span>
          </div>
          <div class="delete-text-container">
            <span class="text">
              Voulez-vous supprimer 07 09 XX XX XX de votre liste des numéros
              favoris ?
            </span>
          </div>
          <van-button class="add-button" @click="deleteFavorite(favorite.id)">
            Supprimer
          </van-button>
          <van-button class="cancel-button" @click="show = false">
            Annuler
          </van-button>
        </div>
      </van-action-sheet>
      <hr class="line" />
    </div>
    <div class="add-button">
      <add-button></add-button>
    </div>
  </div>
</template>
<script setup>
let value = ref('')
const show = ref(false)
let favorites = ref([
  { id: '1', name: 'Maman', number: '5656726768' },
  { id: '2', name: 'Travail', number: '565676636768' },
  { id: '3', name: 'Maison', number: '544676636768' },
])
const showDelete = () => {
  show.value = true
}

const deleteFavorite = (favoriteId) => {
  const index = favorites.value.findIndex(
    (favorite) => favorite.id === favoriteId,
  )
  if (index !== -1) {
    favorites.value.splice(index, 1)
  }
  show.value = false
}
</script>

<style lang="scss" scoped>
.container {
  margin: 20px;
  .text-container {
    .favoris {
      color: #000;
      font-size: 14px;
      font-weight: 500;
      line-height: normal;
    }
    .number {
      color: #999;
      font-size: 12px;
      font-weight: 400;
      line-height: normal;
      .num {
        color: #ff7900;
        font-size: 12px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
      }
    }
  }

  .search-container {
    margin-top: 10px;
  }

  .favorites-list {
    .content {
      height: 425px;
      margin: 16px;
      display: flex;
      flex-direction: column;
      gap: 25px;
      margin-top: 60px;
      .img-container {
        display: flex;
        justify-content: center;
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
      .orange-text-container {
        display: flex;
        justify-content: center;
        .text {
          color: #f16e00;
          text-align: center;
          font-size: 24px;
          font-weight: 700;
          line-height: 24px; /* 100% */
          letter-spacing: 0.169px;
        }
      }
      .delete-text-container {
        text-align: center;
        .text {
          color: #000;
          text-align: center;
          font-size: 18px;
          font-weight: 400;
          line-height: 22px; /* 122.222% */
        }
      }

      .cancel-button {
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
    }
    .line {
      margin: 0px;
    }
    .favorite-list-item {
      display: flex;
      gap: 20px;
      align-items: center;
      height: 65px;
      .item-element {
        .name {
          color: #000;
          font-size: 14px;
          font-style: normal;
          font-weight: 500;
          line-height: normal;
          letter-spacing: 0.563px;
        }
        .number {
          color: #000;
          font-size: 12px;
          font-style: normal;
          font-weight: 400;
          line-height: normal;
          letter-spacing: 0.25px;
        }
      }
    }
    .delete-img {
      background-color: #000;
      height: 100%;
      width: 80px;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .modif-img {
      background-color: #f16e00;
      height: 100%;
      width: 80px;
      display: flex;
      align-items: center;
      justify-content: center;
    }
  }
}
</style>
