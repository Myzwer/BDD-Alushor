<template>
	<div>
		<div class="relative">
			<div class="venue-h1-background">
				<div class="absolute z-2 w-full">
					<TopWave color="text-primary"/>
				</div>
				<div class="content-middle text-white text-center">
					<h1 class="text-7xl mb-2 px-2">The Venue</h1>
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
			<div class="text-center mx-auto max-w-2xl md:max-w-5xl">
				<div class="grid grid-cols-12 gap-4 pt-10 pb-12">
					<div class="col-span-12 md:col-span-6 px-5 text-center">
						<h2 class="text-6xl">Ceremony Address</h2>
						<h3 class="text-lg font-bold uppercase body-font">
							{{ ceremonyLine1 }}
						</h3>
						<h3 class="text-lg font-bold uppercase body-font">
							{{ ceremonyLine2 }}
						</h3>
						<h3 class="text-lg font-bold uppercase body-font">
							{{ ceremonyLine3 }}
						</h3>
						<div class="py-5">
							<a
								:href="ceremonyMap"
								target="_blank"
								class="bg-accent text-white uppercase rounded-full font-bold shadow-lg px-20 py-3 transition duration-300 ease-in-out hover:bg-purple-hover mt-10"
							>
								Launch in Maps
								<font-awesome-icon
									icon="fa-solid fa-arrow-up-right-from-square"
								/>
							</a>
						</div>
					</div>

					<div class="col-span-12 md:col-span-6 px-5 text-center">
						<h2 class="text-6xl">Reception Address</h2>
						<h3 class="text-lg font-bold uppercase body-font">
							{{ receptionLine1 }}
						</h3>
						<h3 class="text-lg font-bold uppercase body-font">
							{{ receptionLine2 }}
						</h3>
						<h3 class="text-lg font-bold uppercase body-font">
							{{ receptionLine3 }}
						</h3>
						<div class="py-5">
							<a
								:href="receptionMap"
								target="_blank"
								class="bg-accent text-white uppercase rounded-full font-bold shadow-lg px-20 py-3 transition duration-300 ease-in-out hover:bg-purple-hover mt-10"
							>
								Launch in Maps
								<font-awesome-icon
									icon="fa-solid fa-arrow-up-right-from-square"
								/>
							</a>
						</div>
					</div>

					<div class="col-span-12 px-5 text-left">
						<gmap-map
							ref="mmm"
							:center="center"
							:zoom="11"
							style="width: 100%; height: 300px"
						>
							<gmap-marker
								v-for="(m, index) in markers"
								:key="index"
								:position="m.position"
								:clickable="true"
								:draggable="true"
								@click="center = m.position"
							></gmap-marker>
						</gmap-map>
					</div>
				</div>

				<div class="grid grid-cols-12 gap-4 pt-5 md:pt-10 pb-12">
					<div class="col-span-12 px-5 text-left md:text-center">
						<h2 class="text-6xl pb-2">Special Instructions</h2>
						<ul class="list-none text-lg">
							<li>We are in the crimson ballroom all night!</li>
							<li>
								Park in Lot D when you arrive and take the door
								that's right there.
							</li>
							<li>Follow signs to the ballroom.</li>
							<li>
								You can validate your parking at the front desk
								before you leave.
							</li>
						</ul>
					</div>
				</div>
			</div>
		</div>

		<div class="bg-primary-alt">
			<TopWave color="text-secondary"/>
			<div class="text-center mx-auto max-w-2xl md:max-w-5xl">
				<div
					class="grid grid-cols-12 gap-4 pt-10 pb-12 text-white px-5"
				>

					<div class="col-span-12 md:col-span-6 text-left">
						<h2 class="text-6xl pb-3">Lodging Options</h2>

						<!-- Outer grid so the loop stacks properly -->
						<div
							class="grid grid-cols-12 gap-4"
						>
							<HotelLocations
								v-for="hotel in hotels"
								:key="hotel.name"
								:name="hotel.name"
								:address-line1="hotel.addressLine1"
								:address-line2="hotel.addressLine2"
								:distance="hotel.distance"
								:link="hotel.link"
							/>
						</div>
					</div>

					<div class="col-span-12 md:col-span-6 text-left md:pt-20">
						<img
							:src="hotelImage"
							alt="Hotel Image or Couple Image"
						/>
					</div>

				</div>
			</div>
			<BottomWave color = "text-primary" />
		</div>
	</div>
</template>

<script>
import HotelLocations from '~/components/HotelLocations'
import {
	hotels,
	tagline,
	ceremonyAddress,
	receptionAddress,
	sideImages
} from '~/data/data.json'

export default {
	name: 'EventVenue',
	components: {HotelLocations},
	data() {
		return {
			hotels,
			hashtag: tagline.hashtag,
			ceremonyMap: ceremonyAddress.gmaps,
			ceremonyLine1: ceremonyAddress.address1,
			ceremonyLine2: ceremonyAddress.address2,
			ceremonyLine3: ceremonyAddress.address3,
			receptionMap: receptionAddress.gmaps,
			receptionLine1: receptionAddress.address1,
			receptionLine2: receptionAddress.address2,
			receptionLine3: receptionAddress.address3,
			hotelImage: sideImages.hotel,

			// latlong.net/convert-address-to-lat-long.html
			center: {
				lat: 35.28883,
				lng: -80.75076,
			},
			markers: [
				{
					position: {
						lat: 35.30883,
						lng: -80.75076,
					},
				},
				{
					/* SECOND MARKER FOR ALT RECEPTION:
					 position: {
						lat: 40.8484,
						lng: -73.8857,
					}, */
				},
			],
		}
	},
}
</script>

<style>
/* stylelint-disable color-function-notation */
.venue-h1-background {
	background: linear-gradient(rgba(0, 0, 0, 60%), rgba(0, 0, 0, 60%)),
	url('~static/images/venue/venue-head.jpg');
	height: 60vh;
	background-position: top center;
	background-repeat: no-repeat;
	background-size: cover;
}

/* stylelint-enable color-function-notation */
</style>
