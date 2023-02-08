<template>
	<div>
		<div class="relative">
			<div class="index-h1-background relative">
				<div class="absolute z-10 w-full">
					<svg class = "fill-current text-primary" viewBox="0 0 1736 172" fill="none" xmlns="http://www.w3.org/2000/svg">
						<path fill-rule="evenodd" clip-rule="evenodd" d="M1736 98L1664 89C1591 80 1447 63 1302 45.0001C1157 28.0001 1013 11.0001 868 37.0001C723 63.0001 579 132 434 158C289 184 145 167 72 158L-1.90808e-06 150L-1.50215e-05 7.5472e-05L72 6.91776e-05C145 6.27957e-05 289 5.02068e-05 434 3.75305e-05C579 2.48542e-05 723 1.22653e-05 868 -4.10975e-07C1013 -1.30873e-05 1157 -2.56762e-05 1302 -3.83525e-05C1447 -5.10288e-05 1591 -6.36176e-05 1664 -6.99995e-05L1736 -7.62939e-05L1736 98Z"/>
					</svg>
				</div>
				<div class="content-middle text-white text-center">
					<h1 class="text-8xl mb-2 px-2">
						{{ groomName }} + {{ brideName }}
					</h1>
					<h2 class="text-xl font-bold uppercase body-font">
						{{ hashtag }}
					</h2>
				</div>
			</div>
		</div>
		<div class="bg-secondary py-10">
			<div class="text-center mx-auto md:max-w-2xl">
				<h2 class="body-font text-xl font-bold pb-1">Save The Date</h2>
				<h1 class="body-font text-3xl uppercase">{{ weddingDate }}</h1>
				<CountdownToDate/>
			</div>
			<div class="text-center mb-10">
				<a
					:href="rsvpLink"
					target="_blank"
					class="bg-accent text-white uppercase rounded-md font-bold shadow-lg px-20 py-3 transition duration-300 ease-in-out hover:bg-purple-hover mt-10"
				>
					RSVP!
				</a>
			</div>
		</div>

		<div class="bg-primary">
			<div class="text-center mx-auto max-w-2xl md:max-w-5xl">
				<div class="grid grid-cols-12 gap-4 pt-10 pb-12">
					<div class="col-span-12 md:col-span-6 px-5">
						<div
							class="text-center mx-auto max-w-sm md:max-w-xs px-5"
						>
							<img
								class="rounded-xl shadow-lg"
								:src="groomImage"
								alt="Groom Headshot"
							/>
						</div>

						<div class="mb-10">
							<h2 class="pt-7 text-5xl text-white">
								About {{ groomName }}
							</h2>
							<p class="text-white text-left">
								{{ groomBio.substring(0, 100) + '...' }}
							</p>
						</div>

						<div class="text-center mb-10">
							<NuxtLink
								to="/groom"
								class="text-white uppercase rounded-md font-bold border-white border-2 px-8 py-3 transition duration-300 ease-in-out hover:bg-accent mt-10"
							>
								Read More
							</NuxtLink>
						</div>
					</div>

					<div class="col-span-12 md:col-span-6 px-5">
						<div
							class="text-center mx-auto max-w-sm md:max-w-xs px-5"
						>
							<img
								class="rounded-xl shadow-lg"
								:src="brideImage"
								alt="Bride Headshot"
							/>
						</div>

						<div class="mb-10">
							<h2 class="pt-7 text-5xl text-white">
								About {{ brideName }}
							</h2>
							<p class="text-white text-left">
								{{ brideBio.substring(0, 100) + '...' }}
							</p>
						</div>

						<div class="text-center mb-10">
							<NuxtLink
								to="/bride"
								class="text-white uppercase rounded-md font-bold border-white border-2 px-8 py-3 transition duration-300 ease-in-out hover:bg-accent mt-10"
							>
								Read More
							</NuxtLink>
						</div>
					</div>
				</div>
			</div>
		</div>

		<div class="bg-secondary">
			<div class="text-center mx-auto max-w-2xl md:max-w-5xl">
				<div class="grid grid-cols-12 gap-4 pt-10 pb-12">
					<div class="col-span-12 px-5">
						<div class="mb-10">
							<h2 class="pt-7 text-5xl text-black">
								Meet {{ groomName }} & {{ brideName }}
							</h2>
							<p class="text-black text-left">
								{{ coupleBio.substring(0, 200) + '...' }}
							</p>
						</div>
						<div class="text-center mb-10">
							<NuxtLink
								to="/the-couple"
								class="text-black uppercase rounded-md font-bold border-black border-2 px-8 py-3 transition duration-300 ease-in-out hover:bg-accent mt-10"
							>
								Read More
							</NuxtLink>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
import CountdownToDate from '~/components/CountdownToDate'
import {index, RSVP, groom, bride, tagline, couple} from '~/data/data.json'

export default {
	name: 'IndexPage',
	components: {CountdownToDate},

	data() {
		return {
			weddingDate: index.date,
			hashtag: tagline.hashtag,
			rsvpLink: RSVP.link,
			groomImage: index.groomImage,
			groomBio: groom.bio1,
			groomName: groom.firstName,
			brideImage: index.brideImage,
			brideBio: bride.bio1,
			brideName: bride.firstName,
			coupleBio: couple.bio1,
		}
	},
	head() {
		return {
			title: groom.firstName + ' + ' + bride.firstName + "'s Wedding",
			meta: [
				{
					name:
						groom.firstName +
						' + ' +
						bride.firstName +
						"'s Wedding",
					content:
						"We can't wait for you to join us on" +
						index.date +
						"for our wedding! We are so excited and we'll see you there!",
					hid: 'descrption',
				},
			],
		}
	},
}
</script>

<style>
/* stylelint-disable color-function-notation */
.index-h1-background {
	background: linear-gradient(rgba(0, 0, 0, 70%), rgba(0, 0, 0, 70%)),
	url('~static/images/index/index-head.jpg');
	height: 60vh;
	background-position: center center;
	background-repeat: no-repeat;
	background-size: cover;
}

/* stylelint-enable color-function-notation */
</style>
