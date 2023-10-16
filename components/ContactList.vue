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

      <ul
        class="contact-list"
        v-for="contact in filteredContacts"
        :key="contact.id"
        @click="selectContact(contact)"
        :class="{ selected: contact.selected }"
      >
        <li class="contact-list-item">
          <span class="contact-icon">
            {{ getContactIcon(contact.name) }}
          </span>
          <span class="contact">
            <van-cell  :title="contact.name" @click="show = true" />
            <van-action-sheet
              v-model:show="show"
              :actions="actions"
              @select="onSelect"
              description="Choisir un numéro"
              close-on-click-action
            >
            
          </van-action-sheet>
          </span>
        </li>
      </ul>
      <div class="button-container">
        <van-button :disabled="isDisabled" class="button">
          Ajouter le numéro
        </van-button>
      </div>
    </div>
  </div>
</template>

<script setup>
let input = ref('')
let contacts = ref([
  { id: 1, name: 'Adjoua Bakayoka', selected: false },
  { id: 2, name: 'Affoue Dembele', selected: false },
  { id: 3, name: 'Hiba el echi', selected: false },
])

let isDisabled = ref(true)
let filteredContacts = computed(() => {
  const searchTerm = input.value.trim().toLowerCase()
  if (!searchTerm) {
    return contacts.value
  } else {
    return contacts.value.filter((contact) =>
      contact.name.toLowerCase().includes(searchTerm),
    )
  }
})
let getContactIcon = (contact) => {
  const initials = contact
    .split(' ')
    .map((word) => word.charAt(0).toUpperCase())
    .join('')
    .substring(0, 2)

  return initials
}
let selectContact = (selectedContact) => {
  selectedContact.selected = !selectedContact.selected
  isDisabled.value =
    contacts.value.filter((contact) => contact.selected).length === 0
}
const show = ref(false)
const actions = [
  { name: '5665656566' },
  { name: '6767676777' },
  { name: '6656666666' },
]
const onSelect = (item) => {
  show.value = false
  showToast(item.name)
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
      .contact-list-item {
        display: flex;
        gap: 20px;
        align-items: center;
        height: 56px;
      }
      .selected {
        background-color: #ababab;
        color: red;
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
      .button:disabled {
        cursor: not-allowed;
        background-color: #cccccc;
        color: #ababab;
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
