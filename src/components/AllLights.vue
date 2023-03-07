<template>
	<div class="svetla"> 
							
		<div v-for="(room, index) in rooms"
            :key="index"
			class="svetlo"
			@click="$emit('change-room', index)"> 
												
			<div class="svetlo-ikona">
				<img :src="room.zapnuto ? '/images/light-on.svg':'/images/light-off.svg'">
			</div>
			
			<div class= "svetlo-nazev">
				{{ room.nazev }}
			</div>
		</div>

	</div>
</template>



<script>
export default {
	props: ['rooms'],
	emits: ['change-room'], 
}
</script>

