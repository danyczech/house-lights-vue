<template>
	<div class="lights"> 
							
		<div v-for="(room, index) in rooms"
            :key="index"
			class="light"
			@click="$emit('change-room', index)"> 
												
			<div class="light__icon">
				<img :src="room.lightOn ? '/images/light-on.svg':'/images/light-off.svg'">
			</div>
			
			<div class= "light__name">
				{{ room.name }}
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

