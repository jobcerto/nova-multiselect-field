<template>
	<panel-item :field="field">
		<div slot="value" v-if="field.value.length">
			<span class="p-1 inline-block" v-for="option in field.value">
				<el-tag size="mini" type="info"> {{  option.name  }}</el-tag>
			</span>    
		</div>
	</panel-item>
</template>

<script>
	export default {
		props: ['resource', 'resourceName', 'resourceId', 'field'],
	}
</script>
