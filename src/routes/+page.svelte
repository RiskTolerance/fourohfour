<script lang="ts">
	import * as rive from '@rive-app/canvas';
	import { onMount } from 'svelte';
	let canvas: HTMLCanvasElement;
	onMount(() => {
		const riveInstance = new rive.Rive({
			src: '/404.riv',
			canvas: canvas,
			autoplay: true,
			onLoad: () => {
				riveInstance.resizeDrawingSurfaceToCanvas();
				riveInstance.stateMachineNames.forEach((stateMachine) => {
					riveInstance.play(stateMachine);
				});
			}
		});
	});
</script>

<div class="flex h-screen w-full flex-col items-center justify-center">
	<canvas
		bind:this={canvas}
		class="h-full max-h-[1024px] w-full max-w-[1440px]"
		style="aspect-ratio: 1440 / 1024"
	></canvas>
</div>
