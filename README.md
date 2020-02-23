# ts-specific-declarations-webpack-plugin

This Webpack plugin generates a single TypeScript *.d.ts declaration file.
Either for all or a specified list of entries.

### Installation

```shell
$ npm install ts-specific-declarations-webpack-plugin --save-dev
```

### Usage

* Simply add the plugin to `webpack.config.js`:

    ```javascript
    const TsSpecificDeclarationWebpackPlugin = require('ts-specific-declarations-webpack-plugin');

    module.exports = {
        entry: {
            app: './src/app.ts',
            component: './src/component.tsx',
            admin: './src/adminPanel/index.tsx',
        },
        output: {
            path: path.resolve('./dist'),
            filename: '[name].js',
        },
        plugins: [
            // if no arguments are passed, default behavior is to create *.d.ts per entry.
            new TsSpecificDeclarationWebpackPlugin(), 
        ]
    }
    ```
* Will generate `app.d.ts`, `component.d.ts` and `admin.d.ts` in the root directory

### Arguments

* `[entries]` - An optional array of objects which inludes the entries to generate the bundled *.d.ts for. If this argument is used, entries which are not in this list will be **exlucded**
    ```js
        ...
        plugins: [
            new TsSpecificDeclarationWebpackPlugin(
                 [
                    {
                        name: 'app',
                    },
                    {
                        name: 'admin',
                        dir: './admin/'
                    }
                ]
            ),
        ]

    ```
* Will generare `./app.d.ts`, `./admin/admin.d.ts` and will **exclude** the `component` entry since it was not specified


### Have Fun!
