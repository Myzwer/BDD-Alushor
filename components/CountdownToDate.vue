<template>
	<div class="grid grid-cols-12 gap-4 pt-10 pb-12">

		<div class="col-span-6 md:col-span-3 relative">
			<v-progress-circular
				:value=percentDays
				:rotate="270"
				:size="$vuetify.breakpoint.xs ? 130 : '180'"
				:width="15"
			>
				<div class="absolute">
				<p class="font-bold text-4xl md:text-6xl body-font">{{ days }}</p>
				<p class="font-bold text:xl md:text-2xl">Days</p>
				</div>
			</v-progress-circular>
		</div>

		<div class="col-span-6 md:col-span-3 relative">
			<v-progress-circular
				:value=percentHours
				:rotate="270"
				:size="$vuetify.breakpoint.xs ? 130 : '180'"
				:width="15"
			>
				<div class="absolute">
					<p class="font-bold text-4xl md:text-6xl body-font">{{ hours }}</p>
					<p class="font-bold text:xl md:text-2xl">Hours</p>
				</div>
			</v-progress-circular>
		</div>

		<div class="col-span-6 md:col-span-3 relative">
			<v-progress-circular
				:value=percentMinutes
				:rotate="270"
				:size="$vuetify.breakpoint.xs ? 130 : '180'"
				:width="15"
			>
				<div class="absolute">
					<p class="font-bold text-4xl md:text-6xl body-font">{{ minutes }}</p>
					<p class="font-bold text:xl md:text-2xl">Minutes</p>
				</div>
			</v-progress-circular>
		</div>

		<div class="col-span-6 md:col-span-3 relative">
			<v-progress-circular
				:value=percentSeconds
				:rotate="270"
				:size="$vuetify.breakpoint.xs ? 130 : '180'"
				:width="15"
			>
				<div class="absolute">
					<p class="font-bold text-4xl md:text-6xl body-font">{{ seconds }}</p>
					<p class="font-bold text:xl md:text-2xl">Seconds</p>
				</div>
			</v-progress-circular>
		</div>


	</div>
</template>

<script>
export default {
	name: 'CountdownToDate',
	data() {
		return {
			days: 0,
			hours: 0,
			minutes: 0,
			seconds: 0,
			percentDays: 0,
			percentHours: 0,
			percentMinutes: 0,
			percentSeconds: 0,
		}
	},
	methods: {
		daysRemaining() {
			const weddingDate = new Date('Nov 18, 2023 17:00:00').getTime()
			const now = new Date().getTime()
			const distance = weddingDate - now

			const days = Math.floor(distance / (1000 * 60 * 60 * 24))
			const hours = Math.floor(
				(distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)
			)
			const minutes = Math.floor(
				(distance % (1000 * 60 * 60)) / (1000 * 60)
			)
			const seconds = Math.floor((distance % (1000 * 60)) / 1000)

			return [days, hours, minutes, seconds]
		},

		updateTime() {
			const [days, hours, minutes, seconds] = this.daysRemaining()
			this.days = days
			this.hours = hours
			this.minutes = minutes
			this.seconds = seconds

			this.percentDays = (days / 365) * 100
			this.percentHours = (hours / 24) * 100
			this.percentMinutes = (minutes / 60) * 100
			this.percentSeconds = (seconds / 60) * 100
		},
	},
	mounted() {
		this.updateTime() // run once on mount
		setInterval(this.updateTime, 1000) // run every second
		setInterval(this.updateCircles, 1000) // run every second
	},
}
</script>
