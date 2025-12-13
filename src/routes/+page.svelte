<script>
    import FirstComponent from "../components/FirstComponent.svelte";
    import ButtonsBox from "../components/ButtonsBox.svelte";
    import DerivedComponent from "../components/DerivedComponent.svelte";
    let name = 'Svelte'
    name = name.toUpperCase()
    const src = 'https://i.pinimg.com/originals/5d/c3/0d/5dc30d4ba8f3008f6dee639456b73aed.png'
</script>

<style>
    p {
        color: #555ab9;
        font-size: 24px;
        font-family: "Source Code Pro", monospace;
    }
</style>

<div>
    <img {src} alt="{name} Logo">
    <h1>Hello {name}!</h1>
    <p>This is a paragraph</p>
    <FirstComponent />
    <ButtonsBox/>
    <DerivedComponent/>
</div>
