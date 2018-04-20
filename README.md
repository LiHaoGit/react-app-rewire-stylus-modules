# react-app-rewire-stylus-modules

Add Stylus and Stylus module support to
[create-react-app](https://github.com/facebookincubator/create-react-app) 2.0 via
[react-app-rewired](https://github.com/timarney/react-app-rewired).

`Create react app 2.0` already supports CSS modules. This extension adds support for regular less files and *.module.styl files.

## Installation

```
npm install --save-dev react-app-rewire-stylus-modules
```

OR

```
yarn add --dev react-app-rewire-stylus-modules
```

## Usage

Use the following file extensions for any Less module styles:

* `*.module.styl`

Files with the following file extensions will load normally, without the CSS
Modules loader:

* `*.styl`

### Example

In your react-app-rewired configuration:

```javascript
/* config-overrides.js */

const rewireStyl = require("react-app-rewire-stylus-modules");

module.exports = function override(config, env) {
  
  config = rewireStyl(config, env);
  
  // with loaderOptions
  // (not yet implemented)
  // config = rewireStyl.withLoaderOptions({
  //     modifyVars: {
  //       "@primary-color": "#1890ff",
  //     },
  //   })(config, env);

  return config;
};
```

In your React application:

```styl
// src/App.module.styl

.app {
  color: aqua;

  &:hover {
    color: lawngreen;
  }
}
```

```jsx harmony
// src/App.js

import React from 'react';
import styles from './App.module.styl';

export default ({text}) => (
    <div className={styles.app}>{text}</div>
)
```
