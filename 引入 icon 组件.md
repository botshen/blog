## 引入 icon 组件

```tsx
import ReactDOM from 'react-dom';
import React from 'react';
import Icon from './icon';

ReactDOM.render(<div>
    <Icon name="wechat"/>
</div>, document.body);
```

##  普通的函数组件

```tsx
import React from 'react'

function Icon{
    return (
    <span>icon</span>
    );
}

export default Icon
```

## 可以引入参数的函数组件

interface 表示函数类型

下面是 react 如何声明带有 props 的函数组件

```tsx
import React from 'react';
import './importIcons';

interface IconProps {
    name: string;
}
// Icon 的类型是 React.FunctionComponent 是一个 react 函数组件
// 他的属性类型是 IconProps 
const Icon: React.FunctionComponent<IconProps> = (props) => {
    return (
        <span>
      <svg>
        <use xlinkHref={`#${props.name}`}/>
      </svg>
    </span>
    );
};

export default Icon;

```

## 自动引入所有的 svg 的帮助函数

```js
let importAll = (requireContext) => requireContext.keys().forEach(requireContext)
try {
  importAll(require.context('./icons/', true, /\.svg$/))
} catch (error) {
  console.log(error)
}
```

## 声明 svg 的类型

告诉 ts 如果 svg 导出，类型是 any

```ts
declare module '*.svg' {
  const content: any;
  export default content;
}
```

## 使用 svg-sprite-loader 引入 svg 文件

```js
// "svg-sprite-loader": "^4.1.3", 
module: {
    rules: [
      {
        test: /\.tsx?$/,
        loader: 'awesome-typescript-loader'
      },
      {
        test: /\.svg$/,
        loader: 'svg-sprite-loader',
      },
    ]
  },
```

## tsconfig 分析指定目录

两个 ** 是多层

```json
"include": [
    //只分析这个目录下的所有文件
    "lib/**/*"
  ],
```



