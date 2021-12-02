<script>
    import Chart from "../Chart.svelte";
    import SvelteTable from "svelte-table";

    let waves = [];
    let Ng0 = [];
    let ng0 = [];
    let data = [];

    for(let i=400; i<=1600; i+=10)
    {
        waves.push(i);
        const N = 287.6155 + 4.8866 / (i / 1000) ** 2 + 0.0680 / (i / 1000) ** 4;
        const n = (N / (10 ** 6) + 1)
        Ng0.push(N)
        ng0.push(n)
        data.push({waves: i, Ng0: N, ng0: n})
    }

    const columns = [
        {
            key: "Waves",
            title: "Waves",
            value: v => v.waves,
        },
        {
            key: "Ng0",
            title: "Ng0",
            value: v => parseFloat(v.Ng0).toFixed(2),
        },
        {
            key: "ng0",
            title: "ng0",
            value: v => parseFloat(v.ng0).toFixed(8),
        },
    ];


</script>

<Chart data={data}/>
<div style="width: 500px; margin-left: auto; margin-right: auto">
    <SvelteTable columns="{columns}" rows="{data}" />
</div>
