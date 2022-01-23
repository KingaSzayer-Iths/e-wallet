<template>
  <div :class="['card', {vendor}]">
      <img :src="wifi" alt="Wifi">
      <img src="" alt="Chip">
      <img src="" alt="Vendor Logo">
      <p class="card-number">{{cardNumber}}</p>
      <p>{{cardholderText}}</p>
      <p>{{cardholderName}}</p>
      <p>{{validThruText}}</p>
      <p>{{validThru}}</p>
  </div>
</template>

<script>
export default {
    data() { return {
        wifi: '',
        chip: '',
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
    height: 241px;
    width: 382px;
    filter: drop-shadow(0px 0px 32px rgba(0, 0, 0, 0.1));
    background-color: #D0D0D0;
    margin: 16px;
    border-radius: 8px;
}

div.bitcoin {
    background-color: blue;
}
div.evilcorp {
    background-color: pink;
}

p.card-number { 
    font-family: 'MT Mono', sans-serif;
    font-size: 29px;
}
</style>