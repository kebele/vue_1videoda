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
Product.vue içine v-for="index in 5" :key="index" şeklinde kod ile 5 tane product compunu dizdik
şimdi önceki çalışmalardan listeler içindeki listeyi alıp buradaki Product componenti içine koyup verileri dinamik hale getirelim, oradan productList [aldık ve] burada data ya koyduk (data nın cli kullanımında bir function olduğuna dikkat)
şimdi v-for döngümüzü ona göre ayarlayalım, v-for ile productList ten dizilimi yaptık ancak burada bir hata verdi, bunu sebebi şua nda bunu bir function içinden aldığımız için key değerini index ten alamazsın dedi bu yüzden her bir ürüne unique bir değer vermeliyiz, listenin iiçne gidip her üürün için ayrı bir id değeri vereceğiz, v-for ile bir veri döndürüyorsak burada ayrı bir id ye ihtiyacımız var. Vue burada sıralarını tutar, eğer bir id verirsek eşşiz bir değer vue bunu tutar vermezsek yine çalışır ama ileide sıkıntı çıkarabilir, çünkü sıralama değişirse ortalık karışıri vue sıraları tutar eğer id yoksa
şimdi sıra arraydeki bilgileri Product.vue içine yollamak, ayrıca bu array a birde description ekleyelim

componentler arası veri iletişimi
bunun bir kaç yolu var;
1. props 
bunun içiçn root comp içindeyken yani ver göndereceğimiz componenti kullandığımız yerde o componentin içinde yollamak; burada product ı product olarak yollamak istiyoruz
:product="product"

Product.vue ya gidip script içinde props : ["product"]
şeklinde ekleyeceğiz

bundna sonra artık bu bilgileri kullanabilir hae geliriz
yani title için {{prosut.title}}
{{product.price}} vb şeklinde

bu yöntem parettan child a veri iletimi yöntemi

şimdi alta bir buton koyalım


 -->
  <div class="container">
    <!-- <myComp/>   -->
    <!-- <Product v-for="index in 5" :key="index" /> -->
    <Product
      :product="product" 
      v-for="product in productList" 
      :key="product.id" />
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
  data() {
    return {
      productList: [
        {
          id: 1,
          title: "macbook pro",
          price: 100,
          count: 0,
          description : "açıklama 1"
        },
        {
          id: 2,
          title: "iphone",
          price: 50,
          count: 100,
          description : "açıklama 2"
        },
        {
          id: 3,
          title: "klavye",
          price: 10,
          count: 1000,
          description : "açıklama 3"
        },
      ],
    };
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
