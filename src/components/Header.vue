<template>
<div class="container-fluid my-container d-flex">
    <input type="text" v-model.trim="stringToSearch"
    @keyup.enter="$emit('newSearch' , stringToSearch)">  
</div>
</template>
<script>
export default {
name: 'HeaderIndex',
data: function(){
    return{
        stringToSearch: '',
    }
}
}
</script>
<style lang="scss">
div.my-container{
    background-color: aliceblue;
    height: 30px;
}
</style>
