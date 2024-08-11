<script>
    import { onMount } from "svelte";
    
    export let x_items

    let time_max = 0

    onMount(() => {
        // find the max time
        for (const item of x_items) {
            if (time_max < item.time) {
                time_max = item.time
            }
        }

        // get the closest number disivible by 4
        if (time_max == 4*60) {
            pass
        }
        else {
            time_max = time_max/60
            let q = Math.floor(time_max/4)
            let n = 4*(q+1)
            time_max = n*60
        }
    })
</script>

    <div class='container'>
        <div class='container-row'>
            <div class='y-axis'>
                <p class='y-axis-item y-item-first'>{time_max/60}h</p>
                <p class='y-axis-item'>{(time_max/60)*0.75}h</p>
                <p class='y-axis-item'>{(time_max/60)*0.5}h</p>
                <p class='y-axis-item'>{(time_max/60)*0.25}h</p>
                <p class='y-axis-item'>{(time_max/60)*0}h</p>
            </div>
            <div class='graph'>
                {#each x_items as item}
                <div class='bar-container' style='height:{(item.time/time_max)*100}%'>
                    <div class='bar'></div>
                    <p class='bar-label'>{item.title}</p>
                </div>
                {/each}
            </div>
        </div>
    </div>



<style>
    * {
        padding: 0;
        margin: 0;
    }

    .container {
        display: flex;
        flex-direction: column;
        height: fit-content;
        width: fit-content;
        align-items: center;
        justify-content: center;
        padding-left: 1rem;
        padding-bottom: 4rem;
    }

    .container-row {
        display: flex;
        flex-direction: row;
    }
    
    .graph {
        display: flex;
        flex-direction: row;
        align-items: end;
        justify-content: start;
        border-bottom: 2px solid black;
        border-left: 2px solid black;
        padding: .5rem;
        padding-bottom: 0;
        width:fit-content;
    }

    .bar {
        height: 100%;
        width: 2rem;
        margin-right: 1rem;
        background-color: blue;
    }

    .bar-label {
        rotate: -60deg;
        margin-top: 1rem;
    
    }

    .y-axis {
        padding-right: 0.5rem;
    }

    .y-axis-item {
        margin-top: 2rem;
    }

    .y-item-first {
        margin-top: 0;
    }
</style>

