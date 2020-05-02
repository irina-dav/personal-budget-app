<script>
    import CostItem from './CostItem.svelte';
    import {onMount} from "svelte";
    import PieChart from './PieChart.svelte';
    import Grid from './CostsGrid.svelte';
    import CostForm from './CostForm.svelte';

    let hereKitty = false;
    const handleMouseenter = () => hereKitty = true;
    const handleMouseleave = () => hereKitty = false;
</script>

<style>
    img {
        position: absolute;
        left: 0;
        bottom: -60px;
        transform: translate(-80%, 0) rotate(-30deg);
        transform-origin: 100% 100%;
        transition: transform 0.4s;

    }
    .curious {
        transform: translate(-15%, 0) rotate(0deg);
    }
    :global(body) {
        overflow: hidden;
    }
</style>

<!-- creative commons BY-NC http://www.pngall.com/kitten-png/download/7247 -->
<img
        class:curious={hereKitty}
        alt="Kitten wants to know what's going on"
        src="./images/kitten.png"
>
<div class="container">
    <h2>My personal costs</h2>
    <div on:mouseenter={handleMouseenter} on:mouseleave={handleMouseleave}>
        <CostForm/>
    </div>
    <div class="row">
        <div class="col s6"><Grid /></div>
        <div class="col s6"><PieChart/></div>
    </div>
</div>

