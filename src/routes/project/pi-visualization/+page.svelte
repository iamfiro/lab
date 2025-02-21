<script lang="ts">
	import { onMount } from 'svelte';

	const PI = Math.PI;
	let time = 0;

    let trailPositions: { x: number; y: number }[] = [];

	const drawCircle = (ctx: CanvasRenderingContext2D, x: number, y: number, radius: number, isFill?: boolean) => {
		ctx.beginPath();
		ctx.arc(x, y, radius, 0, 2 * PI);
		isFill ? ctx.fill() : ctx.stroke();
		ctx.stroke();
	};

	onMount(() => {
		const canvas = document.querySelector('canvas') as HTMLCanvasElement;
		const ctx = canvas.getContext('2d') as CanvasRenderingContext2D;

		const dpr = window.devicePixelRatio || 1;
		const rect = canvas.getBoundingClientRect();

		canvas.width = rect.width * dpr;
		canvas.height = rect.height * dpr;
		ctx?.scale(dpr, dpr);

		const canvasCenterX = rect.width / 2;
		const canvasCenterY = rect.height / 2;

		function animate() {
			// Clear canvas
			ctx.clearRect(0, 0, canvas.width, canvas.height);

			// Draw center point
			drawCircle(ctx, canvasCenterX, canvasCenterY, 5, true);

			// Draw rotating line
			ctx.beginPath();
			ctx.moveTo(canvasCenterX, canvasCenterY);
			const lineLength = 100;
			const firstLineToX = canvasCenterX + lineLength * Math.cos(time);
			const firstLineToY = canvasCenterY + lineLength * Math.sin(time);
			ctx.lineTo(firstLineToX, firstLineToY);
            ctx.lineWidth = 2;
			ctx.stroke();

            // Draw rotating line 2
            ctx.beginPath();
            ctx.moveTo(firstLineToX, firstLineToY);
            const secondLineToX = firstLineToX + (lineLength * 0.7) * Math.cos(time * PI);
            const secondLineToY = firstLineToY + (lineLength * 0.8) * Math.sin(time * PI);
            ctx.lineTo(secondLineToX, secondLineToY);
            ctx.lineWidth = 2;
            ctx.stroke();

            // Draw circle 2
            drawCircle(ctx, secondLineToX, secondLineToY, 1.5, true);

            // Draw circle 2 trail
            const trailX = secondLineToX ;
            const trailY = secondLineToY;

            trailPositions.push({ x: trailX, y: trailY });

            ctx.beginPath();
            trailPositions.forEach((pos, index) => {
                if (index === 0) {
                    ctx.moveTo(pos.x, pos.y);
                } else {
                    ctx.lineTo(pos.x, pos.y);
                }
            });
            ctx.lineWidth = 1;
            ctx.stroke();

			// Update time
			time += 0.05;
			requestAnimationFrame(animate);
		}

		animate();
	});
</script>

<canvas> </canvas>

<style>
	canvas {
		width: 100%;
		height: 100%;
	}
</style>
