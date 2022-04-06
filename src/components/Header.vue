<template>
<div class="container-fluid my-container ">
    <div class="row">
        <div class="col-4">
            <h1>Boolflix</h1>
        </div>
        <div class="col-4 my-input d-flex flex-column justify-content-center">
            <input type="text" v-model.trim="stringToSearch"
            @keyup.enter="$emit('newSearch' , stringToSearch)" placeholder="Cerca un titolo...">  
        </div>   
    </div>  
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
    height: 60px;
}
</style>
