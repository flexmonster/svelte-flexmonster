<script lang="ts">
    import { Flexmonster } from '$lib';
    import "flexmonster/flexmonster.css";
    import type { Pivot } from 'flexmonster';

    let pivotTable : Pivot;
</script>

<Flexmonster bind:pivot={pivotTable} reportcomplete={true} report={"https://cdn.flexmonster.com/reports/report.json"}></Flexmonster>