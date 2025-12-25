<script lang="ts">
    import FirstComponent from "../components/FirstComponent.svelte";
    import ButtonsBox from "../components/ButtonsBox.svelte";
    import DerivedComponent from "../components/DerivedComponent.svelte";
    import GlobalStore from "../components/GlobalStore.svelte";
    import EachComponent from "../components/EachComponent.svelte";
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

<div class="grid grid-cols-2 gap-4">
    <div class="grid gap-2 p-4">
        <a href="/blocks">Blocks</a>
        <a href="/async">Async</a>
        <a href="/box">Box</a>
        <a href="/transition">Transition</a>
        <a href="/react_class">React class</a>
        <a href="/snippets_props">Snippets props</a>
        <a href="/animation_values">Animation values</a>
        <a href="/each_block_binding">Each block bindings</a>
        <img {src} alt="{name} Logo">
        <h1>Hello {name}!</h1>
        <p>This is a paragraph</p>
        <FirstComponent />
    </div>
    <div class="grid gap-2 p-4">
        <a href="/capturing">Capture</a>
        <a href="/input">Input</a>
        <a href="/tooltip">Tooltip</a>
        <a href="/custom_transition">Custom Transition</a>
        <a href="/snippets_render">Snippets Render</a>
        <a href="/any_snippet">Implicit snippet props</a>
        <a href="/springs">Springs</a>
        <a href="/size">Size</a>
        <ButtonsBox/>
        <DerivedComponent/>
        <GlobalStore/>
        <EachComponent/>
    </div>
</div>
