## How to get the current logged in user in Kibana

### kibana.json

```javascript
"optionalPlugins": ["security"]
```

### plugin.ts

```javascript
// import SecurityPluginSetup
import { SecurityPluginSetup } from '../../../x-pack/plugins/security/public';

// set interface
interface PluginSetupDeps {
  security: SecurityPluginSetup;
}

// add security
public setup(core: CoreSetup, { security }: PluginSetupDeps): BarePluginSetup

// deconstruct to getCurrentUser
const { getCurrentUser } = security.authc;

// get it
getCurrentUser().then(user => {
    console.log(user);
});

```