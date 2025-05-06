<script lang="ts">
    import { onMount, onDestroy } from "svelte";
    import type { Params, Pivot } from "flexmonster";

    let gridContainer;
    // A reference to the Flexmonster instance
    export let pivot: Pivot;
    // Events
    export let afterchartdraw: () => void;
    export let aftergriddraw: (param: object) => void
    export let beforegriddraw: (param: object) => void
    export let beforetoolbarcreated: (toolbar: Flexmonster.Toolbar) => void;
    export let cellclick: (cell: Flexmonster.CellData) => void;
    export let celldoubleclick: (cell: Flexmonster.CellData) => void;
    export let chartclick: (data: Flexmonster.ChartData) => void;
    export let datachanged: (param: object) => void;
    export let dataerror: (event?: ErrorEvent) => void;
    export let datafilecancelled: () => void;
    export let dataloaded: () => void;
    export let drillthroughclose: () => void;
    export let drillthroughopen: (cell: Flexmonster.CellData | Flexmonster.ChartData) => void;
    export let exportcomplete: () => void;
    export let exportstart: () => void;
    export let fieldslistclose: () => void;
    export let fieldslistopen: () => void;
    export let filterclose: () => void;
    export let filteropen: (param: object) => void;
    export let loadingdata: () => void;
    export let loadinglocalization: () => void;
    export let loadingolapstructure: () => void;
    export let loadingreportfile: () => void;
    export let localizationerror: () => void;
    export let localizationloaded: () => void;
    export let olapstructureerror: (event?: ErrorEvent) => void;
    export let olapstructureloaded: () => void;
    export let openingreportfile: () => void;
    export let printcomplete: () => void;
    export let printstart: () => void;
    export let querycomplete: () => void;
    export let queryerror: (event?: ErrorEvent) => void;
    export let ready: () => void;
    export let reportchange: () => void;
    export let reportcomplete: () => void;
    export let reportfilecancelled: () => void;
    export let reportfileerror: () => void;
    export let runningquery: () => void;
    export let unauthorizederror: (done: Flexmonster.UnauthorizedErrorHandler) => void;
    export let update: () => void;
    // Parameters
    export let toolbar: boolean;
    export let licenseKey: string | string[];
    export let licenseFilePath: string;
    export let width: string | number;
    export let height: string | number;
    export let componentFolder: string;
    export let report: Flexmonster.Report | string;
    export let shareReportConnection: Flexmonster.APIClientOptions;
    export let global: Flexmonster.Report;
    export let accessibility: Flexmonster.AccessibilityOptions;
    export let customizeAPIRequest: (request: Object) => Object;
    export let customizeCell: (cell: Flexmonster.CellBuilder, data: Flexmonster.CellData) => void;
    export let customizeChartElement: (element: Element, data: Flexmonster.ChartData | Flexmonster.ChartLegendItemData) => void;
    export let customizeContextMenu: (cell: Flexmonster.ContextMenuItem[], data: Flexmonster.CellData | Flexmonster.ChartData, viewType: string) => Flexmonster.ContextMenuItem[];
    export let sortFieldsList: (first: Flexmonster.FieldsListSortingItem, second: Flexmonster.FieldsListSortingItem, fieldsListType: string) => number;

    onMount(async () => {
        const module = await import("flexmonster");
        const Flexmonster = module.default;

        pivot = new Flexmonster({
            afterchartdraw,
            aftergriddraw,
            beforegriddraw,
            beforetoolbarcreated,
            cellclick,
            celldoubleclick,
            chartclick,
            datachanged,
            dataerror,
            datafilecancelled,
            dataloaded,
            drillthroughclose,
            drillthroughopen,
            exportcomplete,
            exportstart,
            fieldslistclose,
            fieldslistopen,
            filterclose,
            filteropen,
            loadingdata,
            loadinglocalization,
            loadingolapstructure,
            loadingreportfile,
            localizationerror,
            localizationloaded,
            olapstructureerror,
            olapstructureloaded,
            openingreportfile,
            printcomplete,
            printstart,
            querycomplete,
            queryerror,
            ready,
            reportchange,
            reportcomplete,
            reportfilecancelled,
            reportfileerror,
            runningquery,
            unauthorizederror,
            update,
            toolbar,
            licenseKey,
            licenseFilePath,
            width,
            height,
            componentFolder,
            report,
            shareReportConnection,
            global,
            accessibility,
            customizeAPIRequest,
            customizeCell,
            customizeChartElement,
            customizeContextMenu,
            sortFieldsList,
            container: gridContainer,
        });
    });

    onDestroy(() => {
        if (pivot) {
            pivot.dispose();
        }
    });
</script>

<div bind:this={gridContainer}></div>
