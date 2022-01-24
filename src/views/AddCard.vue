<template>
  <form @submit.prevent="addNewCard">
      <div class="center-heading">
          <div></div>
          <Header headerText="ADD A NEW BANK CARD"/>
          <div></div>
      </div>
      <h2>NEW CARD</h2>
      <BankCard :cardNumber="cardInfo.newCardNumber" 
        :cardholderName="cardInfo.newCardholderName" 
        :validThru="cardInfo.newValidThru" 
        :vendor="cardInfo.selected" />
      <div class="add-form">
        <label>CARD NUMBER
            <input type="text" v-model="cardInfo.newCardNumber">
        </label>
        <label>CARD HOLDERNAME
            <input type="text" v-model="cardInfo.newCardholderName" >
        </label>
        <div class="add-form-two-columns">
            <label>VALID THRU
                <input class="small-input" type="text" placeholder="MM/YY" v-model="cardInfo.newValidThru"> 
            </label>
            <label>CCV
                <input class="small-input" type="text" v-model="cardInfo.ccv">
            </label>
        </div>
        <label>VENDOR
            <select v-model="cardInfo.selected">
                <option v-for="vendor in vendors" :value="vendor.id" :key="vendor.id">
                    {{vendor.name}}
                </option>
            </select>
        </label>
      </div>
      <button>Add card</button>
  </form>
</template>

<script>
import Header from '../components/Header'
import BankCard from '../components/BankCard'

export default {
    components: {Header, BankCard},
    data(){ return {
        cardInfo: {
            newCardNumber: '',
            newCardholderName: '',
            newValidThru: '',
            ccv:'',
            selected: ''
        },
        toView: 'home',
        vendors: [
            { 
                id: 'bitcoin', 
                name: 'Bitcoin Inc'
            }, 
            {   
                id: 'ninja',
                name: 'Ninja Bank'
            },
            {
                id: 'blockchain',
                name: 'Block Chain Inc'
            }, 
            {
                id: 'evilcorp',
                name: 'Evil Corp'
            }
        ]
    }},
    methods: {
        addNewCard() {
            this.$emit('addNewCardToCards', {...this.cardInfo})
        }
    }
}
</script>

<style scoped lang="scss">
@import url('https://fonts.googleapis.com/css2?family=PT+Mono&family=Source+Sans+Pro:ital,wght@0,200;0,300;0,400;0,600;0,700;0,900;1,200;1,300;1,400;1,600;1,700;1,900&display=swap');

label, 
input {
  display:flex;
  flex-direction:column;
  font-family: 'PT Mono', sans-serif;
  font-size: 12px;
  padding: 8px 16px;
}

input, 
select { 
    font-size: 18pt;
    border: 1px solid rgba(0, 0, 0, 0.8);
    box-sizing: border-box;
    border-radius: 8px;
    width: 382px;
    height: 56px;
}

input.small-input { 
    width: 175px;
}
div.add-form {
    display: grid;
    grid-template-columns: 1fr;
}

div.add-form-two-columns {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

button {
    background-color: black;
    color: white;
    border-radius: 8px;
    width: 382px;
    height: 72px;
    margin: 8px 16px;
    text-transform: uppercase;
    font-size: 22px;
    font-weight: bold;
    font-family: 'PT Mono', sans-serif;
}

.center-heading {
    display: grid;
    grid-template-columns: 1fr 6fr 1fr;
}
</style>