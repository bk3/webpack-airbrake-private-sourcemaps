# Webpack Airbrake Private Sourcemaps Plugin

Basic webpack plugin that uploads all sourcemap files from user defined directories to Airbrake after compilation is complete.

Meant to help with [Airbrake private sourcemapping](https://airbrake.io/docs/features/private-sourcemaps/) implementation.

Implementation Example:

```javascript
// require plugin
const AirbrakePlugin = require('webpack-airbrake-private-sourcemaps');

// webpack plugin definition
plugins: [
  new AirbrakePlugin({
    projectId: '123', // airbrake project id
    projectKey: 'a1b2c3', // airbrake project/auth key
    host: 'https://www.github.com/dist', // your website url where the distribution files will be hosted
    patternForFile: (_path, file) => file.replace(/\.map$/, ''), // (optional) for server side files (return `undefined` when file do not need a pattern)
    directories: ['wwwroot', 'dist'], // directories to scan and upload sourcemaps from
    logging: false, // boolean to show or hide plugin logs
  })
]
```
