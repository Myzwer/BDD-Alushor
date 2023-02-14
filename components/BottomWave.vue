<template>
	<svg
		:class="['fill-current', color]" viewBox="0 0 1737 181" fill="none"
		xmlns="http://www.w3.org/2000/svg">
		<path
			fill-rule="evenodd" clip-rule="evenodd"
			d="M0.5 74.5L72.5 83.5C145.5 92.5 289.5 109.5 434.5 127.5C579.5 144.5 723.5 161.5 868.5 135.5C1013.5 109.5 1157.5 40.5 1302.5 14.5C1447.5 -11.5 1591.5 5.49998 1664.5 14.5L1736.5 22.5V181H1664.5C1591.5 181 1447.5 181 1302.5 181C1157.5 181 1013.5 181 868.5 181C723.5 181 579.5 181 434.5 181C289.5 181 145.5 181 72.5 181H0.5L0.5 74.5Z"/>
	</svg>
</template>

<script>
export default {
	name: "BottomWave",
	props: {
		color: {
			type: String,
			default: ''
		}
	}
}
</script>
