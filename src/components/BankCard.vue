<template>
  <div :class="['card', vendor]">

    <div class="card-top">
      <div class="card-top-left">
        <img v-if="vendor == 'bitcoin'" class="wifi-size" src="../assets/wifi.svg" alt="Wifi">
        <img v-else-if="vendor == ''" class="wifi-size" src="../assets/wifi.svg" alt="Wifi">
        <img v-else class="wifi-size" src="../assets/wifi_white.svg" alt="Wifi">
        <img class="chip-size" src="../assets/chip.svg" alt="Chip" />
      </div>
      <img v-if="vendor == 'bitcoin'" class="vendor-size" alt="Vendor Logo" src="../assets/bitcoin.svg" />
      <img v-else-if="vendor == 'ninja'" class="vendor-size" alt="Vendor Logo" src="../assets/ninja.svg" />
      <img v-else-if="vendor == 'blockchain'" class="vendor-size" alt="Vendor Logo" src="../assets/blockchain.svg" />
      <img v-else-if="vendor == 'evil'" class="vendor-size" alt="Vendor Logo" src="../assets/evil.svg" />
      <img v-else class="vendor-size" alt="Vendor Logo" src="../assets/bitcoin.svg" />
    </div>
    
    <p :class="['card-number', vendor]">XXXX XXXX XXXX XXXX{{cardNumber}}</p>
    
    <div class="card-bottom">
        <div>
            <p :class="['card-text', vendor]">{{cardholderText}}</p>
             <p :class="['holder-info', vendor]">{{cardholderName}}</p>
        </div>
        <div>
            <p :class="['card-text', vendor]">{{validThruText}}</p>
            <p :class="['holder-info', vendor]">MM/YY{{validThru}}</p>
        </div>
    </div>
      
  </div>
</template>

<script>
export default {

    data() { return {
        vendorLogo: '',
        cardholderText: 'CARDHOLDER NAMN',
        validThruText: 'VALID THRU',
    }},
    props:[
        'cardNumber',
        'cardholderName',
        'validThru',
        'ccv',
        'vendor'
    ]
}
</script>

<style scoped>

div.card {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 241px;
    width: 382px;
    filter: drop-shadow(0px 0px 32px rgba(0, 0, 0, 0.1));
    background-color: #D0D0D0;
    margin: 16px;
    border-radius: 8px;
}

div.bitcoin {
    background-color: #FFAE34;
}
div.evil {
    background-color: #F33355;
}
div.ninja {
    background-color: #222222;
}
div.blockchain {
    background-color:#8B58F9;
}

p.bitcoin {
    color: black;
}

p.evil,
p.ninja,
p.blockchain {
    color: white
}

p.card-number { 
    font-family: 'PT Mono', sans-serif;
    font-size: 29px;
    margin: 0px 16px;
}
div.card-top {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    padding: 16px
}

div.card-bottom {
    display: flex;
    flex-direction: row ;
    justify-content: space-between;
    padding: 0px 16px
}

div.card-top-left {
    display: flex;
    flex-direction: column;
    align-items: center;
}

p.card-text {
    font-size: 12px;
    font-family: 'PT Mono', sans-serif;
}
p.holder-info {
    font-family: 18px;
    font-family: 'PT Mono', sans-serif;
    text-transform: uppercase;
    font-size: 18px;
}

img.wifi-size {
    width: 44px;
}
img.chip-size {
    width: 50px;  
}
img.vendor-size {
    width: 64px;
}

</style>