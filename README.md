# vue-ueditor-ireader

A vue component wrapper for UEditor.

## install

```bash
npm install --save vue-ueditor-ireader
```

## use

In Vue

```javascript
import ue from 'vue-ueditor-ireader';

<ue 
    :config="config"
    :id="ueId"
    ref="ue"
    v-model="ueContent"
>
</ue>

```

webpack.config.js

```javascript
const CopyWebpackPlugin = require('copy-webpack-plugin')

const config = {
    plugins: [
        new CopyWebpackPlugin([
            {
                from: path.resolve(__dirname, '../node_modules/vue-ueditor-ireader/src/static/dialogs'),
                to: config.assetsSubDirectory + '/dialogs'
            }
        ])
    ]
}

```
