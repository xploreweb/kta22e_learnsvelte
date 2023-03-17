<script>
    import { bind } from "svelte/internal";
    import ItemList from "./components/ItemList.svelte";
    import Modal from "./components/Modal.svelte";

    let modalActive = false;

    let counter = 0;
    let message = '';
    let items = [
        {name:'piim', done: false},
        {name:'sai', done: true},
        {name:'viin', done: false},
        {name:'õlu', done: true},
    ];

    // pikem ja vanem versioon listide välja toomiseks:
    // $: doneItems = items.filter(function (item)
    // {
    //     return item.done;
    // })

    // lühem ja kaasaegsem viis:
    // $: doneItems = items.filter((item) => {
    //     return item.done;
    // })
    
    // kui on üks parameeter  saab sulud eemaldada
    //     $: doneItems = items.filter(item => {
    //     return item.done;
    // })

    //lihtne versioon ühe parameetri jaoks
    $: doneItems = items.filter(item => item.done);

    $: toDoItems = items.filter(item => !item.done);

    function add(){
        items.push({name: message, done: false});
        items = items;
        message = '';
    }
</script>

<button class="button" on:click={()=>{modalActive=true;}}>Click Me!</button>
<Modal bind:active={modalActive} on:close={()=>{modalActive=false;}}></Modal>


<div class="content">
    <input type="text" class="input" bind:value={message}>
    <button class="button is-primary" on:click={add}>Add</button>
    <ItemList bind:items={items} title="All Items"></ItemList>
    <ItemList bind:items={doneItems} title="Done Items"></ItemList>
    <ItemList bind:items={toDoItems} title="To Do Items"></ItemList>
</div>


<style>

</style>