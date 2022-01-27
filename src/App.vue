<template>
  <div id="app">
    <Home v-if="currentView == 'home'" 
      @changingView="changeCurrentView"
      :myBankCards="bankCards"/>
    <AddCard  v-else-if="currentView == 'addcard'" 
      @addNewCardToCards="addNewCardToMyCards"/>
  </div>
</template>

<script>
import Home from './views/Home'
import AddCard from './views/AddCard'

export default {
  components: {Home, AddCard},
  data() { return {
    currentView : 'home',
    bankCards: []
  }},
  methods: {
    changeCurrentView(toView) {
      this.currentView = toView
    },
    addNewCardToMyCards(newCardInfo) {
      this.currentView = 'home'

      if (this.bankCards.length < 4) {
        this.bankCards.push(newCardInfo)
      }
    }
  }

}
</script>

<style scoped>
#app {
  width: 414px;
  min-height:896px;
  box-shadow: 0px 0px 32px rgba(0, 0, 0, 0.12);
}
</style>