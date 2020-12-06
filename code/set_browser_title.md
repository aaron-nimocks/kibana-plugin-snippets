## How to set the browser title in a Kibana Plugin

### plugin.ts

```javascript
import { CoreStart } from '../../../src/core/public';

async mount(params: AppMountParameters) {
    const { renderApp } = await import('./application');
    const [coreStart, depsStart ] = await core.getStartServices();

    // deconstuct coreStart to get docTitle
    const {
        chrome: { docTitle },
    } = coreStart;

    // Change the title
    docTitle.change("Title of Plugin");

    return renderApp(coreStart, depsStart as AppPluginStartDependencies, params);
}
```