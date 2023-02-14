<template>
	<svg
		:class="['fill-current', color]" viewBox="0 0 1736 172" fill="none"
		xmlns="http://www.w3.org/2000/svg">
		<path
			fill-rule="evenodd" clip-rule="evenodd"
			d="M1736 98L1664 89C1591 80 1447 63 1302 45.0001C1157 28.0001 1013 11.0001 868 37.0001C723 63.0001 579 132 434 158C289 184 145 167 72 158L-1.90808e-06 150L-1.50215e-05 7.5472e-05L72 6.91776e-05C145 6.27957e-05 289 5.02068e-05 434 3.75305e-05C579 2.48542e-05 723 1.22653e-05 868 -4.10975e-07C1013 -1.30873e-05 1157 -2.56762e-05 1302 -3.83525e-05C1447 -5.10288e-05 1591 -6.36176e-05 1664 -6.99995e-05L1736 -7.62939e-05L1736 98Z"/>
	</svg>
</template>

<script>
export default {
	name: "TopWave",
	props: {
		color: {
			type: String,
			default: ''
		}
	}
}
</script>