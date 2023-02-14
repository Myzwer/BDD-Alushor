<template>
	<div>
		<div class="relative">
			<div class="couple-h1-background">
				<div class="absolute z-2 w-full">
					<TopWave color="text-primary"/>
				</div>
				<div class="content-middle text-white text-center">
					<h1 class="text-7xl mb-2 px-2">About Us</h1>
					<h2 class="text-xl font-bold uppercase body-font">
						{{ hashtag }}
					</h2>
				</div>
			</div>
			<div class="absolute bottom-0 z-2 w-full">
				<BottomWave color="text-secondary"/>
			</div>
		</div>

		<div class="bg-secondary">
			<div class="text-center mx-auto max-w-2xl md:max-w-3xl">
				<div class="grid grid-cols-12 gap-4 pt-10 pb-12">
					<div class="col-span-12 md:col-start-3 md:col-span-8 px-5">
						<div class="mt-10 px-5">
							<img
								:src="couplePhoto"
								alt="Photo of the Couple"
							/>
						</div>
					</div>

					<div class="col-span-12 px-5 pb-5">
						<h2 class="pt-7 text-7xl text-center">
							Meet {{ groomName }} + {{ brideName }}
						</h2>
						<p class="text-left pb-5">
							{{ bio1 }}
						</p>

						<p class="text-left pb-5">
							{{ bio2 }}
						</p>
					</div>
				</div>
			</div>
			<BottomWave color = "text-primary-alt" />
		</div>

		<button-footer/>
	</div>
</template>

<script>
import {bride, groom, couple, tagline} from '~/data/data.json'

export default {
	name: 'MeetCouple',

	data() {
		return {
			hashtag: tagline.hashtag,
			brideName: bride.firstName,
			groomName: groom.firstName,
			couplePhoto: couple.couplePhoto,
			bio1: couple.bio1,
			bio2: couple.bio2,
			bio3: couple.bio3,
		}
	},
}
</script>

<style>
/* stylelint-disable color-function-notation */
.couple-h1-background {
	background: linear-gradient(rgba(0, 0, 0, 40%), rgba(0, 0, 0, 40%)),
	url('~static/images/couple/couple-head.jpg');
	height: 60vh;
	background-position: center center;
	background-repeat: no-repeat;
	background-size: cover;
}

/* stylelint-enable color-function-notation */
</style>
