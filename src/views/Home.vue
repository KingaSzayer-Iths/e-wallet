<template>
  <div class="home-view">
      <Header headerText="E-WALLET"/>
      <div class="my-cards">
        <div>
            <h2>Active Card</h2>
            <BankCard v-if="activeCard != ''"
                :cardNumber="activeCard.newCardNumber" 
                :cardholderName="activeCard.newCardholderName" 
                :validThru="activeCard.newValidThru"
                :ccv="activeCard.ccv"
                :vendor="activeCard.selected"/>
        </div>
        <ul class="cards-position">
            <li @click="setActiveCard(myCard.newCardNumber)" 
                v-for="myCard in myBankCards" 
                :key="myCard.newCardNumber"
                class="card-position">
                <BankCard  
                    :cardNumber="myCard.newCardNumber"
                    :cardholderName="myCard.newCardholderName" 
                    :validThru="myCard.newValidThru"
                    :vendor="myCard.selected"/>
            </li>
        </ul>
      </div>
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
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro:ital,wght@0,200;0,300;0,400;0,600;0,700;0,900;1,200;1,300;1,400;1,600;1,700;1,900&display=swap');

li:nth-child(4) {
    bottom: 0px;
}
li:nth-child(3) {
    bottom: 40px;
}
li:nth-child(2) {
    bottom: 80px;
}
li:nth-child(1) {
    bottom: 120px;
} 
div.my-cards {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    flex-grow: 1;
}
div.home-view {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    min-height: 896px;
}
li.card-position {
    position: absolute;
}
ul.cards-position {
    position: relative;
    bottom: 0px;
}
h2 {
    color: grey;
    font-size: 12px;
    text-align: center;
    font-family: 'Source Sans Pro', sans-serif;
    margin: 0;
    text-transform: uppercase;
    margin: 0px 0px 8px 0px;
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