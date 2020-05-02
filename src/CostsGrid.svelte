<script>
    import {categories, costsOrdered} from './Store.js';
    import moment from 'moment';
    import {paginate, LightPaginationNav} from 'svelte-paginate'

    $:  items = $costsOrdered
    let currentPage = 1
    let pageSize = 10
    $: paginatedItems = paginate({items, pageSize, currentPage})

</script>
<table>
    <thead>
    <tr>
        <th>#</th>
        <th>Date</th>
        <th>Category</th>
        <th>Value</th>
    </tr>
    </thead>
    <tbody>
    {#each paginatedItems as cost, idx}
        <tr>
            <td>{(currentPage - 1)*pageSize + idx + 1}</td>
            <td>{moment(cost.date).format('DD.MM.yyyy')}</td>
            <td>{$categories.find(c => +c.id === +cost.category).name}</td>
            <td>{cost.value}</td>
        </tr>
    {/each}
    </tbody>
</table>
<LightPaginationNav
        totalItems="{items.length}"
        pageSize="{pageSize}"
        currentPage="{currentPage}"
        limit="{1}"
        showStepOptions="{true}"
        on:setPage="{(e) => currentPage = e.detail.page}"
/>