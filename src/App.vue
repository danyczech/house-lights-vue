<template>
  <header>
    <h1>Chytrý dům</h1>
  </header>

  <main>
    <OneDetail :room="rooms[roomDetail]" :id="roomDetail" @switch-light="switchLight" />
    <AllLights :rooms="rooms" @change-room="setDetail" />
  </main>
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
          name: "Obývací pokoj",
          lightOn: false,
        },
        {
          name: "Ložnice",
          lightOn: true,
        },
        {
          name: "Dětský pokoj",
          lightOn: false,
        },
        {
          name: "Koupelna",
          lightOn: false,
        },
        {
          name: "Kuchyně",
          lightOn: true,
        },
        {
          name: "Chodba",
          lightOn: false,
        },
        {
          name: "Záchůdek",
          lightOn: false,
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
      this.rooms[index].lightOn = !this.rooms[index].lightOn;
    }
  },
};
</script>


