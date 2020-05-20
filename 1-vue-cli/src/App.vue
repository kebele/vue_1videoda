<template>
  <!-- bir vue componetinde 3 ana bölüm olur 
  <template></template>
  <script></script>
  <style></style>

  template mutlaka olmalıdır diğerleri olmayabilir yine de component çalışır.

components içine MainContainer.vue tanımladık, buradaki bütün içeriği oraya taşıdık, ancak asıl dosyamız bu oradaki içeriği buraya alabilmemiz için onu import etmeliyiz.
bunu script içinde yapacağız
import MainContainer from "@/components/MainContainer"
daha sonta bunu export default içinde belirtmemiz gerekiyor; benim burada kullanacağım component ler şunlardır şeklinde
components isimli nesnenin içine myComp isimli bir key koyacağız buda MainContainer olacak
daha sonrada <myComp/> şeklinde template deki div içine yazacağız
problem olmaması gerekiyor başlangıçtan kalan diğer component olan HelloeWorld.vue yu silebiliriz

şimdi ürün listeletelim,
components içine Product.vue isimli bir component yapalım
bunu buraya import edelim, <myComp/> a ihtiyacımız yok, comment e aldım

 -->
  <div class="container">
    <!-- <myComp/>   -->
    <Product v-for="index in 5" :key="index" />
  </div>
</template>

<script>
// import MainContainer from "@/components/MainContainer"
// burası template içindekileri kontrol eder
//burası normal html sayfasındaki nw Vue;({...}) ya denk gelir
//data eskisi gibi bir object şeklinde tanımlanamaz, burada artık data(){} function dur. data içindeki verileri de return bir object döndürür, orada tanımlarız
import Product from "@/components/Product";
export default {
  components: {
    //  myComp : MainContainer,
    Product,
    //  bu gösterim aslında Product : Product tır, es6 da bu şekilde de tanımlanabilir
  },
};
</script>

<style>
/* burası style konuları için */
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
</style>
