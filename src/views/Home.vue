<template>
  <div class="home-view">
      <div>
      <Header headerText="E-WALLET"/>
      <h2>Active Card</h2>
      </div>
      <BankCard v-if="activeCard != ''"
        :cardNumber="activeCard.newCardNumber" 
        :cardholderName="activeCard.newCardholderName" 
        :validThru="activeCard.newValidThru"
        :ccv="activeCard.ccv"
        :vendor="activeCard.selected"/>
      <ul>
          <li @click="setActiveCard(myCard.newCardNumber)" 
            v-for="myCard in myBankCards" 
            :key="myCard.cardNumber"
            :class="['card-position',activeCard.newCardNumber==myCard.newCardNumber ? 'hide' : '']">
            <BankCard  
                :cardNumber="myCard.newCardNumber"
                :vendor="myCard.selected"/>
          </li>
      </ul>
      <button @click="changeView">Add a new card</button>
  </div>
</template>

<script>
import Header from '../components/Header'
import BankCard from '../components/BankCard'

export default {
    components: {Header, BankCard},
    data(){ return {
        toView: 'addcard',
        activeCard: ''
    }},
    props: ['myBankCards'],
    methods: {
        changeView() {
            this.$emit('changingView', this.toView)
        },
        setActiveCard(cardNumber) {
            this.activeCard = this.myBankCards.find(card => card.newCardNumber == cardNumber)
        }
    }
}
</script>


<style>
div.home-view {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    min-height: 896px;
}
li.card-position {
    /* position: absolute;*/
}
li.hide {
    display: none;
}
h2 {
    color: grey;
    font-size: 12px;
    text-align: center;
    margin: 0;
    text-transform: uppercase;
}
ul {
    padding: 0px;
}
li {
    list-style: none;
}
button { 
    background-color: white;
    color: black;
    border-radius: 8px;
    width: 382px;
    height: 80px;
    margin: 8px 16px;
    text-transform: uppercase;
    font-size: 22px;
    font-weight: bold;
    font-family: 'PT Mono', sans-serif; 
}
</style>