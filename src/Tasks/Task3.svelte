<script>
    import SvelteTable from "svelte-table";
    import Chart2 from "../Chart2.svelte";

    let d = [];
    let deltas = [];
    let data = [];

    for(let i=1; i<=100; i++)
    {
        d.push(i);
        deltas.push( (-(i ** 3) * 1000000 / (24 * ((6378 * 8) ** 2)).toPrecision(12)))
        data.push({d: i, delta: deltas[i-1]})
    }

    const columns = [
        {
            key: "d",
            title: "d",
            value: v => v.d,
        },
        {
            key: "delta",
            title: "delta",
            value: v => parseFloat(v.delta).toFixed(2),
        }
    ];


</script>

<Chart2 data={data}/>
<div style="width: 500px; margin-left: auto; margin-right: auto">
    <SvelteTable columns="{columns}" rows="{data}" />
</div>
