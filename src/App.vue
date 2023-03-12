<template>
  <header>
    <h1>Chytrý dům</h1>
  </header>
  <p v-if="isLoading">Is loading</p>
  <p v-else-if="!isLoading&&error"> {{ error }}</p>
  <main v-else>
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
      sourceData: [],
      rooms: [],
      roomDetail: 0, //starting room in detail
      isLoading: true,
      error: null
    };
  },

  methods: {
    setDetail(index) {
      this.roomDetail = index;
    },
    switchLight(index) {
      this.rooms[index].lightOn = !this.rooms[index].lightOn;
    },
    loadRooms(){
      this.isLoading = true;
      fetch("http://localhost:1337/api/rooms")
        .then((res) => res.json())
        .then((data) => {
          this.isLoading = false;
          this.sourceData = data.data;
          this.sourceData.forEach(item => {
            const newItem = {'name': item.attributes.name, 'lightOn': item.attributes.lightOn, 'id': item.id};
            this.rooms.push(newItem);
          })
        })
        .catch(err => {
          this.isLoading = false;
          this.error = err;
        });
    }
  },
  mounted() {
    this.loadRooms();
  }  
};
</script>


