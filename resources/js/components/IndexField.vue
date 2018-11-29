<template>
	<span>
		<span class="p-1 inline-block" v-for="option in field.value">
			<el-tag size="mini" type="info"> {{  option.name  }}</el-tag>
		</span>
	</span>
</template>

<script>
	export default {
		props: ['resourceName', 'field'],
	}
</script>
