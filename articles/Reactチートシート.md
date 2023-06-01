# React チートシート
## JSX の基本文法
- JavaScript のユーザ定義コンポーネント
  ```js
  React.createElement('MyComponent', { foo: 'bar' }, 'bar');
  ```
- JSX でユーザ定義のコンポーネント
  ```jsx
  <MyComponent foo='bar'>bar</MyComponent>
  ```

## JSX における引数の扱い
JSX では ```<>``` の中で指定された引数が ```props``` として，そのコンポーネントに渡される．

呼び出し側：
```jsx
<MyComponent arg1='name' arg2={4} />
```

呼び出される側：
```jsx
type Props = {
    arg1: string
    arg2?: number
};

const MyComponent: React.FC<Props> = (props) => {
    conat { arg1, arg2 = 1 } = props;

    // 何かしらの処理
}
```

呼び出される側は以下のようにも書ける．
```jsx
type Props = {
    arg1: string
    arg2?: number
};

const MyComponent: React.FC<Props> = ({ arg1, arg2 = 1 }) => {
    // 何かしらの処理
}
```

## JSX における子コンポーネントの扱い
子コンポーネントは暗黙の引数 ```children``` として渡される．

呼び出し側：
```jsx
<MyComponent arg1='name' arg2={4} >
    <p>hogehoge</p>
</MyComponent>
```

呼び出される側：
```jsx
import type { PropsWithChildren } from 'react';
type Props = { arg1: string; arg2?: number } & PropsWithChildren;

const MyComponent: React.FC<Props> = ({ arg1, arg2 = 1, children }) => {
    // 何かしらの処理
}
```

## 式の展開
```{}``` を使って式を展開できる．

```jsx
<ul>
    {list.map((name) => (
        <li>Hello, {name}!</li>
    ))}
</ul>
```