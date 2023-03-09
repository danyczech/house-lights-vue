<template>
  <div class="detail">
    <div class="detail__inner">
      <div class="detail__icon">
        <img
          :src="room.lightOn ? 'images/light-on.svg' : './images/light-off.svg'"
        />
        <!-- zobrazuje správnou ikonu světla dle toho, zda je světlo v zobrazované místnosti zapnuto či vypnuto -->
      </div>

      <h2 class="detail__name">
        {{ room.name }}
      </h2>

      <div class="detail__buttons">
        <button 
          @click="switchLight('on')"
          :class="{ active: !room.lightOn }"
        >
          Zapnout
        </button>
        <button
          @click="switchLight('off')"
          :class="{ active: room.lightOn }"
        >
          Vypnout
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['room', 'id'],
  emits: ['switch-light'],
  methods: {
    switchLight(state) {
      if ((this.room.lightOn && state === 'off') || (!this.room.lightOn && state === 'on')) {
        this.$emit('switch-light', this.id);
      } 
    }
  }    
};
</script>

