<template>
  <div class="container">
    <div class="contacts-container">
      <div>
        <span class="text">
          Ajouter un contact ou un numéro à la liste des numéros favoris
        </span>
      </div>
      <div class="input">
        <van-field
          v-model="input"
          label="Nom ou numéro"
          label-align="top"
          placeholder="Entrer un nom ou un numéro *"
        />
      </div>

      <div class="contacts">
        <span>Contacts</span>
      </div>

      <div
        class="contact-list"
        v-for="contact in filteredContacts"
        :key="contact"
      >
        <div class="contact-list-item">
          <span class="contact-icon">
            {{ getContactIcon(contact) }}
          </span>
          <span class="contact">
            {{ contact }}
          </span>
        </div>
      </div>
      <div class="button-container">
        <van-button class="button">Ajouter le numéro</van-button>
      </div>
    </div>
  </div>
</template>

<script setup>
const input = ref('')
const contacts = ref(['Adjoua Bakayoka', 'Affoue Dembele', 'Hiba el echi'])
const filteredContacts = computed(() => {
  const searchTerm = input.value.trim().toLowerCase()
  if (!searchTerm) {
    return contacts.value
  } else {
    return contacts.value.filter((contact) =>
      contact.toLowerCase().includes(searchTerm),
    )
  }
})
const getContactIcon = (contact) => {
  const initials = contact
    .split(' ')
    .map((word) => word.charAt(0).toUpperCase())
    .join('')
    .substring(0, 2)

  return initials
}
</script>

<style lang="scss" scoped>
.container {
  margin: 20px;

  .contacts-container {
    margin-top: 50px;
    .text {
      font-size: 14px;
      font-style: normal;
      font-weight: 400;
      line-height: 20px;
      letter-spacing: 0.25px;
    }
    .input {
      margin-top: 20px;
    }
    .contacts {
      margin-top: 25px;
      font-size: 18px;
      font-style: normal;
      font-weight: 700;
      line-height: 28px;
    }
    .contact-list {
      margin-top: 25px;
      .contact-list-item {
        display: flex;
        gap: 20px;
      }
      .contact-icon {
        width: 40px;
        height: 40px;
        border-radius: 50%;
        background-color: #f16e00;
        display: flex;
        align-items: center;
        justify-content: center;
        color: #fff;
        font-size: 16px;
        font-style: normal;
        font-weight: 500;
        line-height: 24px; /* 150% */
        letter-spacing: 0.15px;
      }
      .contact {
        line-height: 38px;
      }
    }
    .button-container {
      margin-top: 30px;
      .button {
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

  :deep(.van-field__control) {
    color: #1c1b1f;

    font-size: 1rem;
    line-height: 24px;
    letter-spacing: 0.5px;
  }

  :deep(.van-field--label-top) {
    border: 1px solid #ddd;
    border-radius: 4px;
    padding: 16px;
    overflow: visible;

    .van-field__label--top {
      position: absolute;
      top: -10px;
      left: 12px;
    }

    label {
      background: #fff;
      padding: 0 4px;
      color: #1c1b1f;
      font-size: 0.75rem;
      line-height: 16px;
      letter-spacing: 0.4px;
    }
  }
}
</style>
