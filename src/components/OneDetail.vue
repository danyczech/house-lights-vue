<template>
  <div class="detail">
    <div class="detail-inner">
      <div class="detail-ikona">
        <img
          :src="
            room.zapnuto ? 'images/light-on.svg' : './images/light-off.svg'
          "
        />
        <!-- zobrazuje správnou ikonu světla dle toho, zda je světlo v zobrazované místnosti zapnuto či vypnuto -->
      </div>

      <h2 class="detail-nazev">
        {{ room.nazev }}
      </h2>

      <div class="detail-buttons">
        <button
          @click="$emit('switch-light', id)"
          :class="{ aktivni: !room.zapnuto }"
        >
          Zapnout
        </button>
        <button
          @click="$emit('switch-light', id)"
          :class="{ aktivni: room.zapnuto }"
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
};
</script>

