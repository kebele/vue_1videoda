<template>
    <div class="product">
        <strong>ürün adı</strong>
        <p>açıklama</p>
        <strong>fiyat : 23,45 | adet : 12,3</strong>
    </div>
</template>

<script>
export default {
    
}
</script>

<style>
    .product {
        border : 2px dashed #666;
        padding : 5px 10px;
        width : 300px;
        margin-bottom : 5px
    }
    .product:hover{
        border : 2px solid #666;
        transition : all .5s
    }


</style>