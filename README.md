### 校对✅ [![translate-svg]][translate-list]

[translate-svg]: http://llever.com/translate.svg
[translate-list]: https://github.com/chinanf-boy/chinese-translate-list


欢迎 `Issue` 和 `Pull` ❤️, 最好 `Pull` 👏 

- ⏰ 2018 7.25 开始/结束

## 生活

[help me live , live need money 💰](https://github.com/chinanf-boy/live-need-money)

<details>

<summary> 目录 </summary>

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [TypeScript React Starter](#typescript-react-starter)
- [安装create-react-app](#%E5%AE%89%E8%A3%85create-react-app)
- [创建我们的新项目](#%E5%88%9B%E5%BB%BA%E6%88%91%E4%BB%AC%E7%9A%84%E6%96%B0%E9%A1%B9%E7%9B%AE)
- [运行项目](#%E8%BF%90%E8%A1%8C%E9%A1%B9%E7%9B%AE)
- [测试项目](#%E6%B5%8B%E8%AF%95%E9%A1%B9%E7%9B%AE)
- [创建生产构建](#%E5%88%9B%E5%BB%BA%E7%94%9F%E4%BA%A7%E6%9E%84%E5%BB%BA)
- [创建组件](#%E5%88%9B%E5%BB%BA%E7%BB%84%E4%BB%B6)
  - [类型断言](#%E7%B1%BB%E5%9E%8B%E6%96%AD%E8%A8%80)
- [添加style 😎](#%E6%B7%BB%E5%8A%A0style-)
- [用Jest写测试](#%E7%94%A8jest%E5%86%99%E6%B5%8B%E8%AF%95)
- [添加状态管理](#%E6%B7%BB%E5%8A%A0%E7%8A%B6%E6%80%81%E7%AE%A1%E7%90%86)
  - [通用状态管理](#%E9%80%9A%E7%94%A8%E7%8A%B6%E6%80%81%E7%AE%A1%E7%90%86)
  - [为 actions 设定阶段](#%E4%B8%BA-actions-%E8%AE%BE%E5%AE%9A%E9%98%B6%E6%AE%B5)
  - [安装Redux](#%E5%AE%89%E8%A3%85redux)
  - [简单说明 Redux 流程](#%E7%AE%80%E5%8D%95%E8%AF%B4%E6%98%8E-redux-%E6%B5%81%E7%A8%8B)
    - [Redux 本身需要设置的](#redux-%E6%9C%AC%E8%BA%AB%E9%9C%80%E8%A6%81%E8%AE%BE%E7%BD%AE%E7%9A%84)
    - [设置好Redux后,与组件混合成为容器](#%E8%AE%BE%E7%BD%AE%E5%A5%BDredux%E5%90%8E%E4%B8%8E%E7%BB%84%E4%BB%B6%E6%B7%B7%E5%90%88%E6%88%90%E4%B8%BA%E5%AE%B9%E5%99%A8)
  - [定义我们应用程序的状态](#%E5%AE%9A%E4%B9%89%E6%88%91%E4%BB%AC%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F%E7%9A%84%E7%8A%B6%E6%80%81)
  - [添加action](#%E6%B7%BB%E5%8A%A0action)
  - [添加 减速机-reducer](#%E6%B7%BB%E5%8A%A0-%E5%87%8F%E9%80%9F%E6%9C%BA-reducer)
  - [制作一个容器](#%E5%88%B6%E4%BD%9C%E4%B8%80%E4%B8%AA%E5%AE%B9%E5%99%A8)
  - [创建存储](#%E5%88%9B%E5%BB%BA%E5%AD%98%E5%82%A8)
- [弹出-Ejecting](#%E5%BC%B9%E5%87%BA-ejecting)
- [下一步](#%E4%B8%8B%E4%B8%80%E6%AD%A5)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

</details>

# TypeScript React Starter

本快速入门指南将教您如何连接TypeScript与[React](http://facebook.github.io/react/). 到最后,你会有

-   一个使用 React和TypeScript 的项目
-   [TSLint](https://github.com/palantir/tslint)代码规范
-   用[Jest](https://facebook.github.io/jest/)和[Enzyme](http://airbnb.io/enzyme/)测试,和
-   状态管理[Redux](https://github.com/reactjs/react-redux)

我们将使用[create-react-app](https://github.com/facebookincubator/create-react-app)工具去快速设置. 

我们假设您已经在使用[Node.js](https://nodejs.org/)同[npm](https://www.npmjs.com/). 您可能还想了解一下[React 基础](https://facebook.github.io/react/docs/hello-world.html). 

# 安装create-react-app

我们将使用create-react-app,因为它为 React项目设置了 一些有用的工具和规范默认值. 这只是一个命令行实用程序来构建 新的React项目. 

```shell
npm install -g create-react-app
```

# 创建我们的新项目

我们将创建一个名为的新项目`my-app`: 

```shell
create-react-app my-app --scripts-version=react-scripts-ts
```

[react-scripts-ts](https://www.npmjs.com/package/react-scripts-ts)是一组调整,以采用 标准的create-react-app项目管道 并将 TypeScript 引入混合. 

此时,您的项目布局应如下所示: 

```text
my-app/
├─ .gitignore
├─ node_modules/
├─ public/
├─ src/
│  └─ ...
├─ package.json
├─ tsconfig.json
└─ tslint.json
```

值得注意的是

-   `tsconfig.json` 包含我们项目的 TypeScript特定选项. 
-   `tslint.json`存储我们的[TSLint](https://github.com/palantir/tslint)设置.
-   `package.json`包含我们的依赖项,以及 我们想要运行的命令的一些快捷方式,用于 测试,预览和部署 我们的应用程序. 
-   `public`包含静态资产,例如我们计划部署到的 HTML页面或图像. 您可以删除 此文件夹中的任何文件 除了`index.html`. 
-   `src`包含我们的 TypeScript和CSS代码. `index.tsx`是我们文件的入口点,是必填项. 

# 运行项目

运行项目一样简单

```sh
npm run start
```

这运行`start`,是位于我们`package.json`的`script`字段中 ,并将在我们保存文件时 重新生成 与 重新加载 页面的服务器. 通常,服务器运行于`http://localhost:3000`,但应该自动为您打开了. 

这允许我们快速预览更改,从而 收紧迭代循环. 

# 测试项目

测试也只是一个命令: 

```sh
npm run test
```

此命令针对扩展名`.test.ts`要么`.spec.ts`结尾的所有文件运行 Jest,这是一个非常有用的测试实用程序. 像`npm run start`命令, Jest会在检测到更改后立即自动运行. 如果你愿意,你可以让`npm run start`和`npm run test`并排运行,以便您可以预览更改 并 同时测试它们. 

# 创建生产构建

用`npm run start`运行项目时,我们最终没有得到优化的构建. 通常,我们希望我们发送给 用户的代码 尽可能快速和小巧. 缩小 等.为了可以实现优化这一目标,通常需要更多时间. 我们称之为"生产"构建的构建 (与开发构建相对) . 

要运行生产构建,只需运行即可

```sh
npm run build
```

这将创建一个 优化的 JS和CSS 分别构建在`./build/static/js`和`./build/static/css`. 

您不需要在大多数时间运行生产构建,但如果您需要测量应用程序的最终大小等内容,则非常有用. 

# 创建组件

我们要写一个`Hello`组件. 该组件将采用我们想要 问候的名称变量 (我们将称之为`name`) ,以及可选的感叹号数量 (`enthusiasmLevel`) . 

当我们写类似`<Hello name="Daniel" enthusiasmLevel={3} />`,组件应该呈现类似的东西`<div>Hello Daniel!!!</div>`. 如果`enthusiasmLevel`未指定,组件应默认显示一个感叹号. 如果`enthusiasmLevel`是`0`或者否定,它应该抛出一个错误. 

我们会写一个`Hello.tsx`: 

```ts
// src/components/Hello.tsx

import * as React from 'react';

export interface Props {
  name: string;
  enthusiasmLevel?: number;
}

function Hello({ name, enthusiasmLevel = 1 }: Props) {
  if (enthusiasmLevel <= 0) {
    throw new Error('You could be a little more enthusiastic. :D');
  }

  return (
    <div className="hello">
      <div className="greeting">
        Hello {name + getExclamationMarks(enthusiasmLevel)}
      </div>
    </div>
  );
}

export default Hello;

// helpers

function getExclamationMarks(numChars: number) {
  return Array(numChars + 1).join('!');
}
```

请注意,我们定义了一个名为`Props`的类型`interface`,它指定了我们的组件将采用的属性. `name`是必需的`string`,和`enthusiasmLevel`是可选的`number` (你可以从中`?`得知,`enthusiasmLevel?: number;`). 

我们也写了`Hello`作为无状态功能组件 (SFC) . 再具体一点,`Hello`是一个需要`Props`对象接口的函数,并对其进行解构. 如果`enthusiasmLevel`我们没有值,它将默认为`1`. 

编写函数是两个主要[React 建组件的方式]((https://facebook.github.io/react/docs/components-and-props.html#functional-and-class-components)之一. 如果我们想要,我们*可以*把它写成一个类如下: 

```ts
class Hello extends React.Component<Props, object> {
  render() {
    const { name, enthusiasmLevel = 1 } = this.props;

    if (enthusiasmLevel <= 0) {
      throw new Error('You could be a little more enthusiastic. :D');
    }

    return (
      <div className="hello">
        <div className="greeting">
          Hello {name + getExclamationMarks(enthusiasmLevel)}
        </div>
      </div>
    );
  }
}
```

类是有用的[当 我们 组件实例  有一些状态时 ](https://facebook.github.io/react/docs/state-and-lifecycle.html). 但是在这个例子中我们并不需要考虑 状态 - 事实上,我们将其指定为`object`在`React.Component<Props, object>`,因此 编写SFC 往往会更短. 在创建 可以在库之间 共享的通用UI元素 时,本地组件状态 在 表示组件级别上 更有用. 对于我们的应用程序的生命周期,我们将 重新审视应用程序 如何使用Redux管理 通用状态. 

现在我们已经编写了我们的组件,让我们深入研究`index.tsx`并替换我们的渲染`<App />`与渲染`<Hello ... />`. 

首先,我们将它导入文件的顶部: 

```ts
import Hello from './components/Hello';
```

然后改变我们的`render`: 

```ts
ReactDOM.render(
  <Hello name="TypeScript" enthusiasmLevel={10} />,
  document.getElementById('root') as HTMLElement
);
```

## 类型断言

我们在本节中,需要指出的最后一件事就是这条`document.getElementById('root') as HTMLElement`. 此语法称为一个*类型断言*,有时也称为*cast*. 当 你 比 类型检查器 更清楚 类型 时,这是告诉 TypeScript表达式的真实类型的有用方法. 

在这种情况下我们需要这样做的原因是 `getElementById`的回归类型是`HTMLElement | null`. 简单地说,`getElementById`回报`null`,当它找不到给定的`id`元素时. 我们假设那样`getElementById`实际上会成功,所以我们需要使用`as`语法来说服TypeScript. 

TypeScript还有一个尾随"bang"语法 (`!`) ,从前面的表达式删除`null`和`undefined`. 所以我们*可以*已经写了`document.getElementById('root')!`,但在这种情况下,我们想要更明确一点. 

# 添加style 😎

使用我们的设置,添加组件样式很简单. 对于我们的`Hello`组件,我们可以创建一个CSS文件`src/components/Hello.css`. 

```css
.hello {
  text-align: center;
  margin: 20px;
  font-size: 48px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.hello button {
  margin-left: 25px;
  margin-right: 25px;
  font-size: 40px;
  min-width: 50px;
}
```

create-react-app 使用的工具 (即Webpack和各种加载器) 允许我们只导入我们感兴趣的样式表. 当我们的构建运行时,任何导入的`.css`文件 将 连接到输出文件中. 所以`src/components/Hello.tsx`,我们将添加以下导入. 

```ts
import './Hello.css';
```

# 用Jest写测试

我们有一些关于我们`Hello`组件的假设. 让我们重申它们是什么: 


> -   当我们写类似类似`<Hello name="Daniel" enthusiasmLevel={3} />`的东西,组件应该呈现`<div>Hello Daniel!!!</div>`

> -   如果未指定,组件应默认显示一个感叹号. `enthusiasmLevel`

> -   如果`enthusiasmLevel`为 `0`或者否定,它应该抛出一个错误.

我们可以使用这些要求为我们的组件编写一些测试. 

但首先,让我们安装 Enzyme. [Enzyme](http://airbnb.io/enzyme/)是React生态系统中的常用工具,可以更轻松地编写 组件行为 方式的测试. 默认情况下,我们的应用程序包含一个名为 jsdom 的库,允许我们模拟DOM 并在没有浏览器的情况下 测试其运行时 行为. 

Enzyme类似,但建立在jsdom上,可以更容易地对我们的组件进行某些查询. 让我们将其 安装 为 开发依赖项. 

```sh
npm install -D enzyme @types/enzyme enzyme-adapter-react-16 @types/enzyme-adapter-react-16 react-test-renderer
```

注意我们安装了包`enzyme`以及`@types/enzyme`. 该`enzyme`指的是包含实际运行的JavaScript代码的包,而`@types/enzyme`是一个包含声明文件(`.d.ts`文件)的包 以便 TypeScript可以理解如何使用Enzyme. 您可以了解更多信息`@types`包[here](https://www.typescriptlang.org/docs/handbook/declaration-files/consumption.html). 

我们还必须安装`enzyme-adapter-react-16 and react-test-renderer`. 这是事情`enzyme`期望安装. 

在编写第一个测试之前,我们必须配置 Enzyme以使用React 16 的适配器. 我们将创建一个名为 `src/setupTests.ts`的文件, 这会在运行测试时自动加载:

```ts
import * as enzyme from 'enzyme';
import * as Adapter from 'enzyme-adapter-react-16';

enzyme.configure({ adapter: new Adapter() });
```

现在我们已经设置了Enzyme,让我们开始编写测试!
让我们创建一个名为`src/components/Hello.test.tsx`的文件,毗邻我们早先的`Hello.tsx`文件. 

```ts
// src/components/Hello.test.tsx

import * as React from 'react';
import * as enzyme from 'enzyme';
import Hello from './Hello';

it('renders the correct text when no enthusiasm level is given', () => {
  const hello = enzyme.shallow(<Hello name='Daniel' />);
  expect(hello.find(".greeting").text()).toEqual('Hello Daniel!')
});

it('renders the correct text with an explicit enthusiasm of 1', () => {
  const hello = enzyme.shallow(<Hello name='Daniel' enthusiasmLevel={1}/>);
  expect(hello.find(".greeting").text()).toEqual('Hello Daniel!')
});

it('renders the correct text with an explicit enthusiasm level of 5', () => {
  const hello = enzyme.shallow(<Hello name='Daniel' enthusiasmLevel={5} />);
  expect(hello.find(".greeting").text()).toEqual('Hello Daniel!!!!!');
});

it('throws when the enthusiasm level is 0', () => {
  expect(() => {
    enzyme.shallow(<Hello name='Daniel' enthusiasmLevel={0} />);
  }).toThrow();
});

it('throws when the enthusiasm level is negative', () => {
  expect(() => {
    enzyme.shallow(<Hello name='Daniel' enthusiasmLevel={-1} />);
  }).toThrow();
});
```

这些测试非常基础,但你应该能够掌握一切. 

# 添加状态管理

此时,如果您使用React,能获取一次数据并显示它,您可以认为自己完成了. 

但是,如果您正在开发一个更具交互性的应用程序,那么您可能需要添加 状态管理. 

## 通用状态管理

React本身就是一个用于创建 可组合视图 的有用库. 

但是,React 没有任何用于 在您的应用程序之间 同步数据的工具. 就React组件而言,数据通过您在子元素上指定的 props 向下流动. 

由于React本身不提供对 状态管理的 内置支持,因此React社区使用 Redux和MobX 等库. 
 

[Redux](http://redux.js.org)依赖于通过 集中且不可变的数据存储 来 同步数据,对该数据的更新 将 触发 我们的应用程序的 重新呈现.通过发送由称为reducers 的 函数处理 的 显式操作消息,以 不可变的方式 更新状态. 由于具有明确的性质,通常更容易推 断某个操作 将 如何影响您的程序状态. 



[MobX](https://mobx.js.org/)依赖于函数反应模式,其中 状态通过 可观察包装 和 作为 props 传递. 通过简单地将 状态标记为可观察状态 来保持 状态完全同步 以 用于任何观察者. 更好的是,该库已经用 TypeScript编写. 两者都有各种优点和权衡. 

通常Redux 倾向于看到更广泛的用法,因此为了本教程的目的,我们将专注于添加Redux;但是,你应该感到鼓励去探索两者. 

以下部分可能有一个陡峭的学习曲线. 我们强烈建议你[通过其文档熟悉Redux](http://redux.js.org/)

## 为 actions 设定阶段

除非我们的应用程序状态发生变化,否则 添加Redux 是没有意义的. 

我们需要一个可以触发更改的操作源. 

这可以是计时器,也可以是U I中的某个按钮. 为了我们的目的,我们将添加两个按钮来控制我们`Hello`组件的热情程度. 

## 安装Redux

要添加Redux,我们将首先安装`redux`和`react-redux`,以及它们的类型,作为依赖. 

```sh
npm install -S redux react-redux @types/react-redux
```

在这种情况下,我们不需要安装`@types/redux`因为Redux已经附带了自己的定义文件 (`.d.ts`文件) . 

## 简单说明 Redux 流程

### Redux 本身需要设置的

1. 要有 基础状态的存储 - [`Store`](#%E5%AE%9A%E4%B9%89%E6%88%91%E4%BB%AC%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F%E7%9A%84%E7%8A%B6%E6%80%81)

2. 要有 对应更改存储的 操作名/类型 - [`actions`](#%E6%B7%BB%E5%8A%A0action)

3. 而 过滤 `不同操作-actions.type`后, 返回 对应更改状态 - [`reducer`](#%E6%B7%BB%E5%8A%A0-%E5%87%8F%E9%80%9F%E6%9C%BA-reducer)

4. 为了 闭合 状态管理的回路, 状态有了, 操作有了, 怎么更改有了, 就是缺了 触发 - `dispatch` 由Redux本身提供

5. 组合Redux 所有定义的- [createStore](#%E5%88%9B%E5%BB%BA%E5%AD%98%E5%82%A8)

### 设置好Redux后,与组件混合成为容器

1. 为了 组件的状态 与 Redux 的状态 联系起来有 [`mapStateToProps`](#%E5%88%B6%E4%BD%9C%E4%B8%80%E4%B8%AA%E5%AE%B9%E5%99%A8)

2. 为了 组件与Redux 的 `触发操作-dispatch` 联系有 [`mapDispatchToProps`](#%E5%88%B6%E4%BD%9C%E4%B8%80%E4%B8%AA%E5%AE%B9%E5%99%A8)

3. 上面两种是配置定义, 而 混合的运行 交由 [`connect`](#%E5%88%B6%E4%BD%9C%E4%B8%80%E4%B8%AA%E5%AE%B9%E5%99%A8)

4. 最后, 把 整个 store 扔进 React 渲染流程 - [Provider](#%E5%88%9B%E5%BB%BA%E5%AD%98%E5%82%A8)

## 定义我们应用程序的状态

我们需要定义 Redux 将存储的 状态形状. 为此,我们可以创建一个名为`src/types/index.tsx`的文件,它将包含我们 可能在整个程序中 使用的 类型定义. 

```ts
// src/types/index.tsx

export interface StoreState {
    languageName: string;
    enthusiasmLevel: number;
}
```

说明: `languageName`将是这个应用程序编写的编程语言 (即 TypeScript或JavaScript) 和`enthusiasmLevel`会有所不同. 当我们编写第一个容器时,我们会理解,为什么我们故意使 我们的状态与我们的 props 略有不同. 

## 添加action

让我们从创建一组我们的应用可以响应的消息类型开始`src/constants/index.tsx`. 

```ts
// src/constants/index.tsx

export const INCREMENT_ENTHUSIASM = 'INCREMENT_ENTHUSIASM';
export type INCREMENT_ENTHUSIASM = typeof INCREMENT_ENTHUSIASM;


export const DECREMENT_ENTHUSIASM = 'DECREMENT_ENTHUSIASM';
export type DECREMENT_ENTHUSIASM = typeof DECREMENT_ENTHUSIASM;
```

这个`const`/`type`默认允许我们,以 易于访问和可重构的方式 使用TypeScript的字符串文字类型. 

接下来,我们将创建一组 actions 和功能,可以在其中创建这些 actions. `src/actions/index.tsx`. 

```ts
import * as constants from '../constants'

export interface IncrementEnthusiasm {
    type: constants.INCREMENT_ENTHUSIASM;
}

export interface DecrementEnthusiasm {
    type: constants.DECREMENT_ENTHUSIASM;
}

export type EnthusiasmAction = IncrementEnthusiasm | DecrementEnthusiasm;

export function incrementEnthusiasm(): IncrementEnthusiasm {
    return {
        type: constants.INCREMENT_ENTHUSIASM
    }
}

export function decrementEnthusiasm(): DecrementEnthusiasm {
    return {
        type: constants.DECREMENT_ENTHUSIASM
    }
}
```

我们创建了两种类型来描述*增量*和*减量*`actions-操作`应该是什么样子. 我们还创建了一个类型 (`EnthusiasmAction`) 描述一个 action 可以是增量或减量的情况. 最后,我们制作了两个函数,来实际制作我们可以使用的 action ,而不是写出庞大的对象文字. 

这里有明显的样板,所以你应该随意查看类似[redux-actions](https://www.npmjs.com/package/redux-actions),一旦你掌握了一切. 

## 添加 减速机-reducer

我们准备好写第一台减速机了! Reducers **过滤** 创建应用程序状态 来 生成对应的更改状态,但却是*无副作用*. 换句话说,他们就是我们所说的*[纯函数](https://en.wikipedia.org/wiki/Pure_function)*. 

我们的减速机将进入`src/reducers/index.tsx`. 它的函数是确保 增量 将 热情水平 提高1,而 减量 将 热情水平 降低1,但热情从不低于1. 

```ts
// src/reducers/index.tsx

import { EnthusiasmAction } from '../actions';
import { StoreState } from '../types/index';
import { INCREMENT_ENTHUSIASM, DECREMENT_ENTHUSIASM } from '../constants/index';

export function enthusiasm(state: StoreState, action: EnthusiasmAction): StoreState {
  switch (action.type) { // 选择 或者说 过滤
    case INCREMENT_ENTHUSIASM:
      return { ...state, enthusiasmLevel: state.enthusiasmLevel + 1 };
    case DECREMENT_ENTHUSIASM:
      return { ...state, enthusiasmLevel: Math.max(1, state.enthusiasmLevel - 1) };
  }
  return state;
}
```

请注意,我们正在使用*对象传播* (`...state`) 它允许我们创建一个浅层的状态,同时替换`enthusiasmLevel`. 要注意的是`enthusiasmLevel`属性是最后的,因为否则它将被我们旧的属性所覆盖. 

您可能想为减速器编写一些测试. 由于 reducer 是纯函数,因此可以传递 任意数据. 对于每个输入,可以通过检查 其新生成的状态 来测试减速器. 考虑一下Jest的[toEqual](https://facebook.github.io/jest/docs/expect.html#toequalvalue)方法,去实现这一目标. 

## 制作一个容器

使用 Redux编写时,我们经常会编写 组件和容器. 组件通常与数据无关,并且主要在 表示级别 工作. *容器*通常包装组件并向其提供 显示和修改状态 所需的任何数据. 您可以阅读有关此概念的更多信息[Dan Abramov's 文章*演示和容器组件*](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0). 

首先让我们更新`src/components/Hello.tsx`这样它就可以修改状态. 我们`Props`将添加两个可选的回调属性命名`onIncrement`和`onDecrement`: 

```ts
export interface Props {
  name: string;
  enthusiasmLevel?: number;
  onIncrement?: () => void;
  onDecrement?: () => void;
}
```

然后我们将这些回调,绑定 两个 我们将添加到组件中 的 新按钮. 

```ts
function Hello({ name, enthusiasmLevel = 1, onIncrement, onDecrement }: Props) {
  if (enthusiasmLevel <= 0) {
    throw new Error('You could be a little more enthusiastic. :D');
  }

  return (
    <div className="hello">
      <div className="greeting">
        Hello {name + getExclamationMarks(enthusiasmLevel)}
      </div>
      <div>
        <button onClick={onDecrement}>-</button>
        <button onClick={onIncrement}>+</button>
      </div>
    </div>
  );
}
```

一般来说,为`onIncrement`和`onDecrement`编写一些触发测试,是个好主意比如 单击各自按钮. 试一试为您的组件编写测试. 

现在我们的组件已更新,我们已准备好将 其 包装到容器中. 让我们创建一个`src/containers/Hello.tsx`,并从以下导入开始. 

```ts
import Hello from '../components/Hello';
import * as actions from '../actions/';
import { StoreState } from '../types/index';
import { connect, Dispatch } from 'react-redux';
```

这里真正的两个关键部分是,原`Hello`组件以及`connect`函数来自react-redux. `connect`将能够真正转换 我们的原`Hello`组件 为 能使用两个函数的容器: 

-   `mapStateToProps`它将来自当前存储的数据,按摩到我们组件部分所需的形状. 
-   `mapDispatchToProps`它创建回调,将 给定的action 和 触发存储的`dispatch`函数结合,使得正常使用 action 同时能 `dispath`存储. 

如果我们记得,我们的应用程序状态包含两个属性: `languageName`和`enthusiasmLevel`. 另一方面我们的`Hello`组件预期一个`name`和`enthusiasmLevel`. `mapStateToProps`将从存储 获取 相关数据,并在必要时对 我们组件的 props 进行调整. 让我们继续写下来吧. 

```ts
export function mapStateToProps({ enthusiasmLevel, languageName }: StoreState) {
  return {
    enthusiasmLevel,
    name: languageName,
  }
}
```

注意`mapStateToProps`仅创建4个属性中的2个给了`Hello`组件期望. 也就是说,我们仍然希望传入`onIncrement`和`onDecrement`. 

> 但 `onIncrement`和`onDecrement` 是 触发 Redux 存储更改的 函数, 往下看

`mapDispatchToProps`是一个采用 dispatcher-调度程序 功能的函数. 此调度程序功能 可以将 action 传递到我们的存储以进行更新,因此 我们把 dispatch 与 两个`on***` 函数联系起来

```ts
export function mapDispatchToProps(dispatch: Dispatch<actions.EnthusiasmAction>) {
  return {
    onIncrement: () => dispatch(actions.incrementEnthusiasm()),
    onDecrement: () => dispatch(actions.decrementEnthusiasm()),
  }
}
```

最后,我们准备好了`connect`. `connect`将首先采取`mapStateToProps`和`mapDispatchToProps`,然后返回另一个我们可以用来 包装我们的组件 的函数. 我们生成的容器使用以下代码定义: 

```ts
export default connect(mapStateToProps, mapDispatchToProps)(Hello);
```

完成后,我们的文件应如下所示: 

```ts
// src/containers/Hello.tsx

import Hello from '../components/Hello';
import * as actions from '../actions/';
import { StoreState } from '../types/index';
import { connect, Dispatch } from 'react-redux';

export function mapStateToProps({ enthusiasmLevel, languageName }: StoreState) {
  return {
    enthusiasmLevel,
    name: languageName,
  }
}

export function mapDispatchToProps(dispatch: Dispatch<actions.EnthusiasmAction>) {
  return {
    onIncrement: () => dispatch(actions.incrementEnthusiasm()),
    onDecrement: () => dispatch(actions.decrementEnthusiasm()),
  }
}

export default connect(mapStateToProps, mapDispatchToProps)(Hello);
```

## 创建存储

我们回去吧`src/index.tsx`. 要把这些放在一起,我们需要创建一个具有初始状态的存储,并使用我们所有的reducer 进行设置. 

```ts
import { createStore } from 'redux';
import { enthusiasm } from './reducers/index';
import { StoreState } from './types/index';

const store = createStore<StoreState>(enthusiasm, {
  enthusiasmLevel: 1,
  languageName: 'TypeScript',
});
```

正如您可能已经猜到的那样,`store`就是,我们的应用程序的全球状态的中央存储. 

接下来,我们将把`./src/components/Hello`变成`./src/containers/Hello`,并使用 react-redux'的`Provider`用 我们的容器 连接我们的 props . 导入: 

```ts
import Hello from './containers/Hello';
import { Provider } from 'react-redux';
```

并通过我们的`store`通过`Provider`的属性: 

```ts
ReactDOM.render(
  <Provider store={store}>
    <Hello />
  </Provider>,
  document.getElementById('root') as HTMLElement
);
```

请注意`Hello`不再需要 *props* ,因为我们使用了`connect`函数,使我们的应用程序的状态,来适应我们包装的`Hello`组件的 props . 

# 弹出-Ejecting

如果在任何时候,您觉得 某些自定义设置 使 创建 React应用程序 变得困难,您可以随时选择退出,并获取所需的各种配置选项. 例如,如果您想添加 Webpack插件,可能需要利用 create-react-app 提供的"Ejecting"功能. 

简单地

```sh
npm run eject
```

你应该好好注意注意!

一开始,您可能希望在运行弹出之前,提交所有工作. 您无法撤消弹出命令,因此选择退出是永久性的,除非您可以在运行弹出之前,从提交中恢复. 

# 下一步

create-react-app 附带了很多很棒的东西. 其中大部分都记录在项目的`README.md`,所以请快速阅读. 

如果您仍想了解有关Redux的更多信息,您可以[Redux官方网址](http://redux.js.org/)用于文档. 同样的道理[MobX官方网址](https://mobx.js.org/). 

如果你想在某些时候弹出,你可能需要更多地了解 Webpack. 你可以看看我们的[React & Webpack 携手合奏](https://www.typescriptlang.org/docs/handbook/react-&-webpack.html). 

在某些时候,您可能需要`路由-router`. 有几种解决方案,但是[react-router](https://github.com/ReactTraining/react-router)可能是 Redux项目中 最受欢迎的,并且经常与[react-router-redux](https://github.com/reactjs/react-router-redux)结合使用. 
