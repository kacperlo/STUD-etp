<script>
    import Chart from "../Chart.svelte";
    import SvelteTable from "svelte-table";
    import Chart2 from "../Chart2.svelte";

    let d = [];
    let deltas = [];
    let data = [];

    function toFixed(x) {
        if (Math.abs(x) < 1.0) {
            var e = parseInt(x.toString().split('e-')[1]);
            if (e) {
                x *= Math.pow(10,e-1);
                x = '0.' + (new Array(e)).join('0') + x.toString().substring(2);
            }
        } else {
            var o = parseInt(x.toString().split('+')[1]);
            if (o > 20) {
                o -= 20;
                x /= Math.pow(10,e);
                x += (new Array(e+1)).join('0');
            }
        }
        return x;
    }

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
            value: v => v.delta,
        }
    ];


</script>

<Chart2 data={data}/>
<div style="width: 500px; margin-left: auto; margin-right: auto">
    <SvelteTable columns="{columns}" rows="{data}" />
</div>
