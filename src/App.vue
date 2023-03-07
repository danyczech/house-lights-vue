<template>
  <div id="app">
    <header>
      <h1>Chytrý dům</h1>
    </header>

    <main>
      <AllLights :rooms="rooms" @change-room="setDetail" />
     
      <OneDetail :room="rooms[roomDetail]" :id="roomDetail" @switch-light="switchLight" />
    </main>
  </div>
</template>

<script>
import AllLights from "@/components/AllLights.vue";
import OneDetail from "@/components/OneDetail.vue";

export default {
  components: { AllLights, OneDetail }, 
  data () {
    return {
      rooms: [
        {
          nazev: "Obývací pokoj",
          zapnuto: false,
        },
        {
          nazev: "Ložnice",
          zapnuto: true,
        },
        {
          nazev: "Dětský pokoj",
          zapnuto: false,
        },
        {
          nazev: "Koupelna",
          zapnuto: false,
        },
        {
          nazev: "Kuchyně",
          zapnuto: true,
        },
        {
          nazev: "Chodba",
          zapnuto: false,
        },
        {
          nazev: "Záchůdek",
          zapnuto: false,
        },
      ],

      roomDetail: 0, //starting room in detail
    };
  },

  methods: {
    setDetail(index) {
      this.roomDetail = index;
    },
    switchLight(index) {
      this.rooms[index].zapnuto = !this.rooms[index].zapnuto;
    }
  },
};
</script>


