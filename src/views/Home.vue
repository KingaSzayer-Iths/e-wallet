<template>
  <div>
      <Header headerText="E-WALLET"/>
      <h2>Active Card</h2>
      <BankCard v-if="myBankCards.length>0"
        :cardNumber="activeCard.newCardNumber" 
        :cardholderName="activeCard.newCardholderName" 
        :validThru="activeCard.newValidThru"
        :ccv="activeCard.ccv"
        :vendor="activeCard.selected"/>
      <ul>
          <li @click="setActiveCard(myCard.newCardNumber)" 
            v-for="myCard in myBankCards" 
            :key="myCard.cardNumber">{{myCard}}</li>
      </ul>
      <a @click="changeView">Add a new card</a>
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
h2 {
    color: grey;
    font-size: 12px;
    text-align: center;
    margin: 0;
    text-transform: uppercase;
}
</style>