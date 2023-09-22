<script>
    import Menu from './components/Menu.svelte';
    import ProductColumn from './components/ProductColumn.svelte';
    import './components/global.css';
</script>
<!-- inspiration - https://www.google.com/search?sca_esv=567351978&rlz=1C5CHFA_enUS1030US1030&q=User+dashboard+web+design&tbm=isch&source=lnms&sa=X&ved=2ahUKEwj6xafSwryBAxWMMjQIHSA2B58Q0pQJegQIEBAB&biw=1920&bih=995&dpr=1#imgrc=Jwo1_SR3S8d8RM -->

<div class='app'>
    <div class='app-row'>
        <Menu />
        <ProductColumn />
    </div>
    
</div>

<style>

.app {
    background-color: #f1f5fe;
    padding: 25px;
    height: 100vh;
    width: 100vw;
}


.app-row {
    display: flex;
    flex-direction: row;
    gap: 25px;
}

@media screen and (max-width: 1000px) {
       .app-row {
        flex-direction: column;
       }
    }


</style>