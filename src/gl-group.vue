<template>
	<div style="display: none;">
		<slot />
	</div>
</template>
<script lang="ts">
import { Vue } from './imports'
import {Component, Inject, Model, Prop, Watch} from 'vue-property-decorator'
import {goldenContainer, goldenChild} from './gl-roles'

@Component({mixins: [goldenChild]})
export default class glGroup extends goldenContainer {
	//child properties
	$parent: goldenContainer
	@Prop({default: false}) closable: boolean
	/// Only the layout object centralise the components
	registerComponent(component/*: Vue|()=>any*/, name?: string): string {
		return this.$parent.registerComponent(component, name);
	}
	onGlInitialise(cb: ()=> void) {
		this.$parent.onGlInitialise(cb);
	}
}
</script>
