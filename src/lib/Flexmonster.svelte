<script lang="ts">
    import { onMount, onDestroy } from "svelte";
    import type { Params, Pivot } from "flexmonster";

    let gridContainer;
    // A reference to the Flexmonster instance
    export let pivot: Pivot = undefined;
    // Events
    export let afterchartdraw: () => void = undefined;
    export let aftergriddraw: (param: object) => void = undefined;
    export let beforegriddraw: (param: object) => void = undefined;
    export let beforetoolbarcreated: (
        toolbar: Flexmonster.Toolbar,
    ) => void = undefined;
    export let cellclick: (cell: Flexmonster.CellData) => void = undefined;
    export let celldoubleclick: (cell: Flexmonster.CellData) => void = undefined;
    export let chartclick: (data: Flexmonster.ChartData) => void = undefined;
    export let datachanged: (param: object) => void = undefined;
    export let dataerror: (event?: ErrorEvent) => void = undefined;
    export let datafilecancelled: () => void = undefined;
    export let dataloaded: () => void = undefined;
    export let drillthroughclose: () => void = undefined;
    export let drillthroughopen: (
        cell: Flexmonster.CellData | Flexmonster.ChartData,
    ) => void = undefined;
    export let exportcomplete: () => void = undefined;
    export let exportstart: () => void = undefined;
    export let fieldslistclose: () => void = undefined;
    export let fieldslistopen: () => void = undefined;
    export let filterclose: () => void = undefined;
    export let filteropen: (param: object) => void = undefined;
    export let loadingdata: () => void = undefined;
    export let loadinglocalization: () => void = undefined;
    export let loadingolapstructure: () => void = undefined;
    export let loadingreportfile: () => void = undefined;
    export let localizationerror: () => void = undefined;
    export let localizationloaded: () => void = undefined;
    export let olapstructureerror: (event?: ErrorEvent) => void = undefined;
    export let olapstructureloaded: () => void = undefined;
    export let openingreportfile: () => void = undefined;
    export let printcomplete: () => void = undefined;
    export let printstart: () => void = undefined;
    export let querycomplete: () => void = undefined;
    export let queryerror: (event?: ErrorEvent) => void = undefined;
    export let ready: () => void = undefined;
    export let reportchange: () => void = undefined;
    export let reportcomplete: () => void = undefined;
    export let reportfilecancelled: () => void = undefined;
    export let reportfileerror: () => void = undefined;
    export let runningquery: () => void = undefined;
    export let unauthorizederror: (
        done: Flexmonster.UnauthorizedErrorHandler,
    ) => void = undefined;
    export let update: () => void = undefined;
    // Parameters
    export let toolbar: boolean = false;
    export let licenseKey: string | string[] = undefined;
    export let licenseFilePath: string = undefined;
    export let width: string | number = undefined;
    export let height: string | number = undefined;
    export let componentFolder: string = undefined;
    export let report: Flexmonster.Report | string = undefined;
    export let shareReportConnection: Flexmonster.APIClientOptions = undefined;
    export let global: Flexmonster.Report = undefined;
    export let accessibility: Flexmonster.AccessibilityOptions = undefined;
    export let customizeAPIRequest: (request: Object) => Object = undefined;
    export let customizeCell: (
        cell: Flexmonster.CellBuilder,
        data: Flexmonster.CellData,
    ) => void = undefined;
    export let customizeChartElement: (
        element: Element,
        data: Flexmonster.ChartData | Flexmonster.ChartLegendItemData,
    ) => void = undefined;
    export let customizeContextMenu: (
        cell: Flexmonster.ContextMenuItem[],
        data: Flexmonster.CellData | Flexmonster.ChartData,
        viewType: string,
    ) => Flexmonster.ContextMenuItem[] = undefined;
    export let sortFieldsList: (
        first: Flexmonster.FieldsListSortingItem,
        second: Flexmonster.FieldsListSortingItem,
        fieldsListType: string,
    ) => number = undefined;

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
