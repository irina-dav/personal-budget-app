<script>
    import CostItem from './CostItem.svelte';
    import {onMount} from "svelte";
    import PieChart from './PieChart.svelte';
    import Grid from './CostsGrid.svelte';
    import CostForm from './CostForm.svelte';

    let currentFilter = 'all';
    let pieChart;
</script>

<div class="container">
    <h2>My costs</h2>
    <div>
        <CostForm/>
    </div>
    <div class="row">
        <div class="col s6"><Grid/></div>
        <div class="col s6"><PieChart/></div>
    </div>
</div>

