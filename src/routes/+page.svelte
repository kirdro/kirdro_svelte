<script lang="ts">
    import FirstComponent from "../components/FirstComponent.svelte";
    import ButtonsBox from "../components/ButtonsBox.svelte";
    import DerivedComponent from "../components/DerivedComponent.svelte";
    import GlobalStore from "../components/GlobalStore.svelte";
    import EachComponent from "../components/EachComponent.svelte";

    // Ссылки на тестовые страницы - просто добавляй новые объекты в массив
    const pages = [
        { href: '/blocks', title: 'Blocks', category: 'basics' },
        { href: '/async', title: 'Async', category: 'basics' },
        { href: '/box', title: 'Box', category: 'components' },
        { href: '/input', title: 'Input', category: 'forms' },
        { href: '/capturing', title: 'Capture', category: 'events' },
        { href: '/transition', title: 'Transition', category: 'animation' },
        { href: '/custom_transition', title: 'Custom Transition', category: 'animation' },
        { href: '/animation_values', title: 'Animation Values', category: 'animation' },
        { href: '/springs', title: 'Springs', category: 'animation' },
        { href: '/react_class', title: 'Reactive Class', category: 'reactivity' },
        { href: '/snippets_props', title: 'Snippets Props', category: 'snippets' },
        { href: '/snippets_render', title: 'Snippets Render', category: 'snippets' },
        { href: '/any_snippet', title: 'Implicit Snippets', category: 'snippets' },
        { href: '/tooltip', title: 'Tooltip', category: 'components' },
        { href: '/each_block_binding', title: 'Each Block Bindings', category: 'bindings' },
        { href: '/bind_this', title: 'Bind This', category: 'bindings' },
        { href: '/bind_component', title: 'Bind Components', category: 'bindings' },
        { href: '/size', title: 'Size', category: 'bindings' },
        { href: '/bind_component_instances', title: 'Bind component instances', category: 'bindings' },
        { href: '/binding_to_component_instances', title: 'Bind to component instances', category: 'bindings' },
        { href: '/context', title: 'Context', category: 'context' },
    ];

    const categories: Record<string, string> = {
        basics: 'Basics',
        components: 'Components',
        forms: 'Forms',
        events: 'Events',
        animation: 'Animation',
        reactivity: 'Reactivity',
        snippets: 'Snippets',
        bindings: 'Bindings',
        context: 'Context'
    };

    const categoryColors: Record<string, string> = {
        basics: 'from-blue-500 to-blue-600',
        components: 'from-purple-500 to-purple-600',
        forms: 'from-green-500 to-green-600',
        events: 'from-yellow-500 to-orange-500',
        animation: 'from-pink-500 to-rose-500',
        reactivity: 'from-cyan-500 to-teal-500',
        snippets: 'from-indigo-500 to-violet-500',
        bindings: 'from-emerald-500 to-green-500',
        context: 'from-amber-500 to-yellow-500'
    };

    // Группировка по категориям
    const groupedPages = $derived(
        Object.keys(categories).map(cat => ({
            name: categories[cat],
            key: cat,
            items: pages.filter(p => p.category === cat)
        })).filter(g => g.items.length > 0)
    );
</script>

<div class="min-h-screen">
    <!-- Header -->
    <header class="mb-8 text-center">
        <h1 class="text-4xl font-bold bg-gradient-to-r from-cyan-400 to-blue-500 bg-clip-text text-transparent mb-2">
            Svelte 5 Playground
        </h1>
        <p class="text-gray-400">Learning & Testing Components</p>
    </header>

    <!-- Navigation Grid -->
    <section class="mb-12">
        <h2 class="text-xl font-semibold text-gray-300 mb-4 flex items-center gap-2">
            <span class="w-8 h-0.5 bg-gradient-to-r from-cyan-500 to-transparent"></span>
            Test Pages
        </h2>

        <div class="grid gap-6 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4">
            {#each groupedPages as group (group.key)}
                <div class="rounded-xl bg-gray-800/50 p-4 backdrop-blur-sm border border-gray-700/50">
                    <h3 class="text-sm font-medium text-gray-400 mb-3 uppercase tracking-wider">
                        {group.name}
                    </h3>
                    <div class="flex flex-wrap gap-2">
                        {#each group.items as page (page.href)}
                            <a
                                href={page.href}
                                class="px-3 py-1.5 rounded-lg text-sm font-medium text-white bg-gradient-to-r {categoryColors[page.category]}
                                       hover:shadow-lg hover:shadow-cyan-500/20 hover:-translate-y-0.5 transition-all duration-200"
                            >
                                {page.title}
                            </a>
                        {/each}
                    </div>
                </div>
            {/each}
        </div>
    </section>

    <!-- Demo Components -->
    <section>
        <h2 class="text-xl font-semibold text-gray-300 mb-4 flex items-center gap-2">
            <span class="w-8 h-0.5 bg-gradient-to-r from-pink-500 to-transparent"></span>
            Demo Components
        </h2>

        <div class="grid gap-4 md:grid-cols-2 lg:grid-cols-3">
            <div class="rounded-xl bg-gray-800/50 p-4 border border-gray-700/50">
                <span class="text-xs text-gray-500 mb-2 block">FirstComponent</span>
                <FirstComponent />
            </div>

            <div class="rounded-xl bg-gray-800/50 p-4 border border-gray-700/50">
                <span class="text-xs text-gray-500 mb-2 block">ButtonsBox</span>
                <ButtonsBox />
            </div>

            <div class="rounded-xl bg-gray-800/50 p-4 border border-gray-700/50">
                <span class="text-xs text-gray-500 mb-2 block">DerivedComponent</span>
                <DerivedComponent />
            </div>

            <div class="rounded-xl bg-gray-800/50 p-4 border border-gray-700/50">
                <span class="text-xs text-gray-500 mb-2 block">GlobalStore</span>
                <GlobalStore />
            </div>

            <div class="rounded-xl bg-gray-800/50 p-4 border border-gray-700/50">
                <span class="text-xs text-gray-500 mb-2 block">EachComponent</span>
                <EachComponent />
            </div>
        </div>
    </section>
</div>
