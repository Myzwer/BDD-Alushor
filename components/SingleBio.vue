<template>
    <!-- State management of background color-->
    <div
        :class="`
		${even ? 'bg-secondary' : 'bg-primary'}`"
    >
        <div class="text-center mx-auto max-w-2xl md:max-w-6xl">
            <div class="grid grid-cols-12 gap-4 pt-10 pb-12">
                <div
                    :class="`col-span-12 md:col-span-5 px-5 md:mt-10
					${even ? '' : 'md:order-2'}`"
                >
                    <img :src="image" alt="" />
                </div>

                <!-- State management of text color -->
                <div
                    :class="`col-span-12 md:col-span-7 px-5
					${even ? 'text-black' : 'text-white'}`"
                >
                    <h2 class="pt-7 text-6xl text-left">{{ name }}</h2>
                    <h3 class="pb-5 uppercase text-left body-font font-bold">
                        {{ title }}
                    </h3>
                    <p class="text-left pb-5">{{ description }}</p>

                    <div class="grid grid-cols-12 gap-4 pb-12">
                        <div
                            v-if="facebook != null"
                            class="inline-block"
                        >
                            <div class="pb-2 md:pb-5 mr-5">
                                <a :href="facebook" target="_blank">
                                    <div
                                        :class="`text-4xl
                                        ${even ? 'text-black' : 'text-white'}`"
                                    >
                                        <font-awesome-icon
                                            icon="fa-brands fa-facebook"
                                        />

                                    </div>
                                </a>
                            </div>
                        </div>

                        <div
                            v-if="instagram != null"
                            class="inline-block"
                        >
                            <div class="pb-2 md:pb-5 mr-5">
                                <a :href="instagram" target="_blank">
									<div
										:class="`text-4xl
										${even ? 'text-black' : 'text-white'}`"
									>
                                        <font-awesome-icon
                                            icon="fa-brands fa-instagram"
                                        />
                                    </div>
                                </a>
                            </div>
                        </div>

                        <div
                            v-if="twitter != null"
                            class="inline-block "
                        >
                            <div class="pb-2 md:pb-5 mr-5">
                                <a :href="twitter" target="_blank">
									<div
										:class="`text-4xl
										${even ? 'text-black' : 'text-white'}`"
									>
                                        <font-awesome-icon
                                            icon="fa-brands fa-twitter"
                                        />
                                    </div>
                                </a>
                            </div>
                        </div>
                    </div>

                </div>
            </div>
        </div>
		<div
			v-if="!last"
			:class="`${even ? 'hidden' : 'block'}`"
		>
			<BottomWave color = "text-secondary" />
		</div>

		<div
			v-if="!last"
			:class="`${even ? 'block' : 'hidden'}`"
		>
			<BottomWave color = "text-primary" />
		</div>

		<div v-if="last"
		>
			<BottomWave color="text-primary-alt" />
		</div>

    </div>
</template>

<script>
export default {
    name: 'SingleBio',
    props: {
        even: {
            type: Boolean,
            required: true,
        },
        name: {
            type: String,
            required: true,
        },
        title: {
            type: String,
            required: true,
        },
        description: {
            type: String,
            required: true,
        },
        image: {
            type: String,
            required: true,
        },
        facebook: {
            type: String,
            default: null,
            required: false,
        },
        instagram: {
            type: String,
            default: null,
            required: false,
        },
        twitter: {
            type: String,
            default: null,
            required: false,
        },
		last: {
			type: Boolean,
			default: null,
			required: false,
		}
    },
}
</script>
