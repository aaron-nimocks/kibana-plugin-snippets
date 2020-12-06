## How to set the breadcrumbs in a Kibana Plugin

### plugin.ts

```javascript
import { CoreStart } from '../../../src/core/public';

async mount(params: AppMountParameters) {
    const { renderApp } = await import('./application');
    const [coreStart, depsStart ] = await core.getStartServices();

    // deconstuct coreStart to get setBreadcrumbs
    const {
        chrome: { setBreadcrumbs },
    } = coreStart;

    // Change the breadcumbs
    setBreadcrumbs([{ text: 'first' }, { text: 'second' }]);

    return renderApp(coreStart, depsStart as AppPluginStartDependencies, params);
}
```