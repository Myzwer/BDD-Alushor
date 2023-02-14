<template>
	<div>
		<div class="relative">
			<div class="index-h1-background relative">
				<div class="absolute z-2 w-full">
					<TopWave color="text-primary" />
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
			<div class="absolute bottom-0 z-2 w-full">
				<BottomWave color="text-secondary" />
			</div>
		</div>
		<div class="bg-secondary py-10">
			<div class="text-center mx-auto md:max-w-3xl">
				<h1 class="body-font text-3xl uppercase">We're Getting Married!</h1>
				<h2 class="body-font text-xl font-bold pb-1">{{ weddingDate }}</h2>
				<CountdownToDate/>
			</div>
			<div class="text-center mb-10">
				<a
					:href="rsvpLink"
					target="_blank"
					class="bg-accent text-white uppercase rounded-full font-bold shadow-lg px-20 py-3 transition duration-300 ease-in-out hover:bg-purple-hover mt-10"
				>
					RSVP!
				</a>
			</div>
		</div>

		<div class="bg-primary">
			<TopWave color = "text-secondary" />
			<div class="text-center mx-auto max-w-2xl md:max-w-5xl">

				<div class="grid grid-cols-12 gap-4 pt-10 pb-12">
					<div class="col-span-12 px-5">

						<div class="grid grid-cols-12 mb-16 gap-4">
							<div class="col-span-12 md:col-span-5">
								<div
									class="text-center mx-auto max-w-sm md:max-w-xs px-5"
								>
									<img
										:src="groomImage"
										alt="Groom Headshot"
									/>
								</div>
							</div>
							<div class="col-span-12 md:col-span-7 text-left">

								<div class="mb-8">
									<h2 class="pt-7 text-7xl text-white">
										The Groom
									</h2>
									<h4 class = "uppercase font-bold text-xl text-white">{{ groomName }}</h4>
									<p class="text-white text-left">
										{{ groomBio.substring(0, 130) + '...' }}
									</p>
								</div>

								<div class="text-left mb-10">
									<NuxtLink
										to="/groom"
										class="text-white uppercase rounded-full font-bold border-white border-2 px-8 py-3 transition duration-300 ease-in-out hover:bg-accent mt-10"
									>
										Read More
									</NuxtLink>
								</div>
							</div>
						</div>


						<div class="grid grid-cols-12 gap-4">
							<div class="col-span-12 md:col-span-5">
								<div
									class="text-center mx-auto max-w-sm md:max-w-xs px-5"
								>
									<img
										:src="brideImage"
										alt="Bride Headshot"
									/>
								</div>
							</div>
							<div class="col-span-12 md:col-span-7 text-left">

								<div class="mb-8">
									<h2 class="pt-7 text-7xl text-white">
										The Bride
									</h2>
									<h4 class = "uppercase font-bold text-xl text-white">{{ brideName }}</h4>
									<p class="text-white text-left">
										{{ brideBio.substring(0, 130) + '...' }}
									</p>
								</div>

								<div class="text-left mb-10">
									<NuxtLink
										to="/bride"
										class="text-white uppercase rounded-full font-bold border-white border-2 px-8 py-3 transition duration-300 ease-in-out hover:bg-accent mt-10"
									>
										Read More
									</NuxtLink>
								</div>
							</div>
						</div>



					</div>
				</div>
			</div>
		</div>

		<div class="bg-secondary">
			<TopWave color = "text-primary" />

			<div class="text-center mx-auto max-w-2xl md:max-w-5xl">
				<div class="grid grid-cols-12 gap-4 pt-10 pb-12">
					<div class="col-span-12 md:col-span-8 px-5">
						<div class="mb-10">
							<h2 class="pt-7 text-5xl text-black text-left">
								Meet {{ groomName }} & {{ brideName }}
							</h2>
							<p class="text-black text-left">
								{{ coupleBio.substring(0, 200) + '...' }}
							</p>
						</div>
						<div class="text-left mb-10">
							<NuxtLink
								to="/the-couple"
								class="text-black uppercase rounded-full font-bold border-black border-2 px-8 py-3 transition duration-300 ease-in-out hover:text-white hover:bg-accent mt-10"
							>
								Read More
							</NuxtLink>
						</div>
					</div>

					<div class="col-span-12 md:col-span-4">
						<img
							:src="coupleImage"
							alt="Couple Headshot"
						/>
					</div>

				</div>
			</div>
			<BottomWave color = "text-primary" />
		</div>
	</div>
</template>

<script>
import CountdownToDate from '~/components/CountdownToDate'
import TopWave from "~/components/TopWave";
import {index, RSVP, groom, bride, tagline, couple} from '~/data/data.json'

export default {
	name: 'IndexPage',
	components: {CountdownToDate, TopWave},

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
			coupleImage: index.coupleImage,
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
	height: 70vh;
	background-position: center center;
	background-repeat: no-repeat;
	background-size: cover;
}

/* stylelint-enable color-function-notation */
</style>
