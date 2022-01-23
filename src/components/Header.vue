<template>
    <div>
        <h1>{{headerText}}</h1>
    </div>
</template>

<script>
export default {
    props: ['headerText']
}
</script>

<style scoped lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro:ital,wght@0,200;0,300;0,400;0,600;0,700;0,900;1,200;1,300;1,400;1,600;1,700;1,900&display=swap');
h1 {
    font-family: 'Source Sans Pro', sans-serif;
    text-align: center;
    margin: 0;
    padding: 40px 64px;
    font-size: 35px;
    font-weight: bold;
}
</style>