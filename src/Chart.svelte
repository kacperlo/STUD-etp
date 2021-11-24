<script>
    import Line from "svelte-chartjs/src/Line.svelte"
    export let data;
    let wa = data.waves

    let dataLine = {
        labels: data.map(a => a.waves),
        datasets: [
            {
                label: "Ng0",
                fill: true,
                lineTension: 0.3,
                backgroundColor: "rgba(225, 204,230, .3)",
                borderColor: "rgb(205, 130, 158)",
                borderCapStyle: "butt",
                borderDash: [],
                borderDashOffset: 0.0,
                borderJoinStyle: "miter",
                pointBorderColor: "rgb(205, 130,1 58)",
                pointBackgroundColor: "rgb(255, 255, 255)",
                pointBorderWidth: 1,
                pointHoverRadius: 3,
                pointHoverBackgroundColor: "rgb(0, 0, 0)",
                pointHoverBorderColor: "rgba(220, 220, 220,1)",
                pointHoverBorderWidth: 2,
                pointRadius: 1,
                pointHitRadius: 1,
                data: data.map(a => a.Ng0)
            }
        ]
    };
    let dataLine2 = {
        labels: data.map(a => a.waves),
        datasets: [
            {
                label: "ng0",
                fill: true,
                lineTension: 0.3,
                backgroundColor: "rgba(225, 204,230, .3)",
                borderColor: "rgb(205, 130, 158)",
                borderCapStyle: "butt",
                borderDash: [],
                borderDashOffset: 0.0,
                borderJoinStyle: "miter",
                pointBorderColor: "rgb(205, 130,1 58)",
                pointBackgroundColor: "rgb(255, 255, 255)",
                pointBorderWidth: 1,
                pointHoverRadius: 3,
                pointHoverBackgroundColor: "rgb(0, 0, 0)",
                pointHoverBorderColor: "rgba(220, 220, 220,1)",
                pointHoverBorderWidth: 2,
                pointRadius: 1,
                pointHitRadius: 1,
                data: data.map(a => a.ng0)
            }
        ]
    };


</script>
<div style="width: 50%; float:left">
    <Line data={dataLine} height={200} width={400}  options={{ responsive: true }}/>
</div>
<div style="width: 50%; float:left">
    <Line data={dataLine2} height={200} width={400}  options={{ responsive: true }}/>
</div>