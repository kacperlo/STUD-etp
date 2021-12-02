<script>
    let dlFali = 910;
    let temp_dry = 5;
    let temp_wet = 5;
    let pa = 1013.25;
    let d = 1000;

    let T_ns=288.15
    let P_ns=1013.25
    let e_ns=10.87

    $: poprawka = ((287.6155 + (4.8866 / ((dlFali / 1000) ** 2) + 0.0680 / ((dlFali / 1000) ** 4)))*0.269578*P_ns/T_ns - (11.27*e_ns/T_ns)) - ((287.6155 + (4.8866 / ((dlFali / 1000) ** 2) + 0.0680 / ((dlFali / 1000) ** 4))) * 0.269578 * pa / (temp_dry + 273.15) - (11.27 * ((6.1078 * (Math.E ** ((17.269 * temp_wet) / (237.30 + temp_wet)))) - (0.000662 * pa * (temp_dry - temp_wet))) / (temp_dry + 273.15)))

</script>

<div style="width: 50%; float: left">
    <h3>Długość fali [nm]</h3>
    <label>
        <input type=number bind:value={dlFali} min=1 max=3000>
        <input style='width: 600px' type=range bind:value={dlFali} min=1 max=3000>
    </label>
    <h3>Temperatura sucha [C]</h3>
    <label>
        <input type=number bind:value={temp_dry} min=-50 max=100>
        <input style='width: 600px' type=range bind:value={temp_dry} min=-50 max=100>
    </label>
    <h3>Temperatura mokra [C]</h3>
    <label>
        <input type=number bind:value={temp_wet} min=-50 max=100>
        <input style='width: 600px' type=range bind:value={temp_wet} min=-50 max=100>
    </label>
    <h3>Ciśnienie [hPa]</h3>
    <label>
        <input type=number bind:value={pa} min=900 max=1200>
        <input style='width: 600px' type=range bind:value={pa} min=900 max=1200>
    </label>
    <h3>Zmierzona odległość [m]</h3>
    <label>
        <input type=number bind:value={d} min=1 max=1000>
        <input style='width: 600px' type=range bind:value={d} min=0 max=100000>
    </label>
</div>
<div style="width: 50%; float: left">
    <h2>Poprawka na km [mm]:</h2><p>{poprawka.toFixed(2)}</p>
    <h2>Poprawka do mierzonej długości [mm]:</h2><p>{(poprawka*d/1000).toFixed(2)}</p>
    <h2>Długość poprawiona [m]:</h2><p>{(d + (poprawka*d/1000000)).toFixed(2)}</p>
</div>