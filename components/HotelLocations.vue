<template>
		<div class="col-span-12 text-left pb-5">
			<h3 class="body-font text-xl font-bold">
				{{ name }}
			</h3>
			<h4 class="text-lg">{{ addressLine1 }}</h4>
			<h4 class="text-lg pb-3">{{ addressLine2 }}</h4>

			<h4 class="text-lg">{{ distance }} away from venue</h4>

			<div class="py-5">
				<a
					:href="link"
					target="_blank"
					class="bg-accent text-white uppercase rounded-full font-bold shadow-lg px-10 md:px-20 py-3 transition duration-300 ease-in-out hover:bg-accent-alt hover:shadow-xl mt-10"
				>
					View Website
					<font-awesome-icon
						icon="fa-solid fa-arrow-up-right-from-square"
					/>
				</a>
			</div>
		</div>
</template>

<script>
export default {
	name: 'HotelLocations',
	props: {
		name: {
			type: String,
			required: true,
		},
		addressLine1: {
			type: String,
			required: true,
		},
		addressLine2: {
			type: String,
			required: true,
		},
		distance: {
			type: String,
			required: true,
		},
		link: {
			type: String,
			required: true,
		},
	},
}
</script>
