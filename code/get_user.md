## How to get the current logged in user in Kibana

`kibana.json`

```javascript
"optionalPlugins": ["security"]
```

`plugin.ts`

```javascript
import { SecurityPluginSetup } from '../../../x-pack/plugins/security/public';

interface PluginSetupDeps {
  security: SecurityPluginSetup;
}

public setup(core: CoreSetup, { security }: PluginSetupDeps): BarePluginSetup

const { getCurrentUser } = security.authc;

getCurrentUser().then(user => {
    console.log(user);
});
```