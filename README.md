next-transpile-vendor-styles
---------------------

[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release)
[![GitHub license badge](https://badgen.net/github/license/freshcells/next-transpile-vendor-styles)](https://opensource.org/licenses/MIT)
[![npm](https://badgen.net/github/release/freshcells/next-transpile-vendor-styles)](https://www.npmjs.com/package/@freshcells/apollo-link-field-keep)

Adds support for vendor style transpilation for next.js.
Based on https://github.com/martpie/next-transpile-modules.

## Install

```
yarn add @freshcells/next-transpile-vendor-styles
```

## Usage

In your `nextjs.config.mjs`

```js
import { PHASE_PRODUCTION_SERVER } from 'next/constants.js'

export default async (phase) => {
    if (phase === PHASE_PRODUCTION_SERVER) {
        return { /* your nextjs config */ }
    }

    // Lazy load modules we require for the compilation only.
    // This way we can later omit the package for production
    
    const transpileVendorStyles = await import('@freshcells/next-transpile-vendor-styles')

    return withTransform = transpileVendorStyles.default([
        '@your-namespace/module-1',
        '@your-namespace/module-2'
    ])
    
    return withTransform({
        /* your nextjs config */
    })
}
```


