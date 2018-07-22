
# TypeScript React Starter

本快速入门指南将教您如何连接TypeScript[React](http://facebook.github.io/react/). 到最后,你会有

-   一个使用React和TypeScript的项目
-   linting with[TSLint](https://github.com/palantir/tslint)
-   用. 测试[Jest](https://facebook.github.io/jest/)和[Enzyme](http://airbnb.io/enzyme/),和
-   国家管理[Redux](https://github.com/reactjs/react-redux)

我们将使用[create-react-app](https://github.com/facebookincubator/create-react-app)快速设置的工具. 

我们假设您已经在使用[Node.js](https://nodejs.org/)同[npm](https://www.npmjs.com/). 您可能还想了解一下[the basics with React](https://facebook.github.io/react/docs/hello-world.html). 

# 安装create-react-app

我们将使用create-react-app,因为它为React项目设置了一些有用的工具和规范默认值. 这只是一个命令行实用程序来构建新的React项目. 

```shell
npm install -g create-react-app
```

# 创建我们的新项目

我们将创建一个名为的新项目`my-app`: 

```shell
create-react-app my-app --scripts-version=react-scripts-ts
```

[react-scripts-ts](https://www.npmjs.com/package/react-scripts-ts)是一组调整,以采用标准的create-react-app项目管道并将TypeScript引入混合. 

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

-   `tsconfig.json`包含我们项目的TypeScript特定选项. 
-   `tslint.json`存储我们的linter设置,[TSLint](https://github.com/palantir/tslint), 将使用. 
-   `package.json`包含我们的依赖项,以及我们想要运行的命令的一些快捷方式,用于测试,预览和部署我们的应用程序. 
-   `public`包含静态资产,例如我们计划部署到的HTML页面或图像. 您可以删除此文件夹中的任何文件`index.html`. 
-   `src`包含我们的TypeScript和CSS代码. `index.tsx`是我们文件的入口点,是必填项. 

# 运行项目

运行项目就像运行一样简单

```sh
npm run start
```

这运行了`start`我们指定的脚本`package.json`,并将在我们保存文件时生成重新加载页面的服务器. 通常,服务器运行于`http://localhost:3000`,但应自动为您打开. 

这允许我们快速预览更改,从而收紧迭代循环. 

# 测试项目

测试也只是一个命令: 

```sh
npm run test
```

此命令针对扩展名结尾的所有文件运行Jest,这是一个非常有用的测试实用程序`.test.ts`要么`.spec.ts`. 喜欢的`npm run start`命令,Jest会在检测到更改后立即自动运行. 如果你愿意,你可以跑`npm run start`和`npm run test`并排,以便您可以预览更改并同时测试它们. 

# 创建生产构建

用它运行项目时`npm run start`,我们最终没有得到优化的构建. 通常,我们希望我们发送给用户的代码尽可能快速和小巧. 缩小等某些优化可以实现这一目标,但通常需要更多时间. 我们称之为"生产"构建的构建 (与开发构建相对) . 

要运行生产构建,只需运行即可

```sh
npm run build
```

这将创建一个优化的JS和CSS构建`./build/static/js`和`./build/static/css`分别. 

您不需要在大多数时间运行生产构建,但如果您需要测量应用程序的最终大小等内容,则非常有用. 

# 创建组件

我们要写一个`Hello`零件. 该组件将采用我们想要问候的任何名称 (我们将称之为`name`) ,以及可选的感叹号数量 (`enthusiasmLevel`) . 

当我们写类似的东西`<Hello name="Daniel" enthusiasmLevel={3} />`,组件应该呈现类似的东西`<div>Hello Daniel!!!</div>`. 如果`enthusiasmLevel`如果未指定,组件应默认显示一个感叹号. 如果`enthusiasmLevel`是`0`或者否定,它应该抛出一个错误. 

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

请注意,我们定义了一个名为的类型`Props`它指定了我们的组件将采用的属性. `name`是必需的`string`,和`enthusiasmLevel`是可选的`number` (你可以从中得知`?`我们在其名字后写出来的. 

我们也写了`Hello`作为无状态功能组件 (SFC) . 再具体一点,`Hello`是一个需要的功能`Props`对象,并对其进行解构. 如果`enthusiasmLevel`我们没有给出`Props`对象,它将默认为`1`. 

写作功能是两个主要功能之一[ways React allows us to make components]((https://facebook.github.io/react/docs/components-and-props.html#functional-and-class-components)). 如果我们想要,我们*可以*把它写成一个类如下: 

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

类是有用的[when our component instances have some state](https://facebook.github.io/react/docs/state-and-lifecycle.html). 但是在这个例子中我们并不需要考虑状态 - 事实上,我们将其指定为`object`在`React.Component<Props, object>`,因此编写SFC往往会更短. 在创建可在库之间共享的通用UI元素时,本地组件状态在表示级别更有用. 对于我们的应用程序的生命周期,我们将重新审视应用程序如何使用Redux管理一般状态. 

现在我们已经编写了我们的组件,让我们深入研究`index.tsx`并替换我们的渲染`<App />`与渲染`<Hello ... />`. 

首先,我们将它导入文件的顶部: 

```ts
import Hello from './components/Hello';
```

然后改变我们的`render`呼叫: 

```ts
ReactDOM.render(
  <Hello name="TypeScript" enthusiasmLevel={10} />,
  document.getElementById('root') as HTMLElement
);
```

## 输入断言

我们在本节中将指出的最后一件事就是这条线`document.getElementById('root') as HTMLElement`. 此语法称为a*类型断言*,有时也称为*投*. 当你比类型检查器更清楚时,这是告诉TypeScript表达式的真实类型的有用方法. 

在这种情况下我们需要这样做的原因是`getElementById`的回归类型是`HTMLElement | null`. 简单地说,`getElementById`回报`null`当它找不到给定的元素时`id`. 我们假设那样`getElementById`实际上会成功,所以我们需要使用the来说服TypeScript`as`句法. 

TypeScript还有一个尾随"bang"语法 (`!`) ,删除`null`和`undefined`从前面的表达式. 所以我们*可以*已经写了`document.getElementById('root')!`,但在这种情况下,我们想要更明确一点. 

# 添加风格😎

使用我们的设置设置组件样式很简单. 我们的风格`Hello`组件,我们可以创建一个CSS文件`src/components/Hello.css`. 

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

create-react-app使用的工具 (即Webpack和各种加载器) 允许我们只导入我们感兴趣的样式表. 当我们的构建运行时,任何导入的文件将连接到输出文件中. `.css`所以,我们将添加以下导入. `src/components/Hello.tsx`用Jest写测试

```ts
import './Hello.css';
```

# 我们有一些关于我们的假设

零件. `Hello`让我们重申它们是什么: 当我们写类似的东西

> -   ,组件应该呈现类似的东西`<Hello name="Daniel" enthusiasmLevel={3} />`. `<div>Hello Daniel!!!</div>`如果
> -   如果未指定,组件应默认显示一个感叹号. `enthusiasmLevel`如果
> -   是`enthusiasmLevel`或者否定,它应该抛出一个错误. `0`我们可以使用这些要求为我们的组件编写一些测试. 

但首先,让我们安装Enzyme. 

是React生态系统中的常用工具,可以更轻松地编写组件行为方式的测试. [Enzyme](http://airbnb.io/enzyme/)默认情况下,我们的应用程序包含一个名为jsdom的库,允许我们模拟DOM并在没有浏览器的情况下测试其运行时行为. 酶类似,但建立在jsdom上,可以更容易地对我们的组件进行某些查询. 让我们将其安装为开发时依赖项. 

注意我们安装了包

```sh
npm install -D enzyme @types/enzyme enzyme-adapter-react-16 @types/enzyme-adapter-react-16 react-test-renderer
```

以及`enzyme`. `@types/enzyme`该`enzyme`package指的是包含实际运行的JavaScript代码的包`@types/enzyme`是一个包含声明文件的包 (`.d.ts`文件) 以便TypeScript可以理解如何使用Enzyme. 您可以了解更多信息`@types`包[here](https://www.typescriptlang.org/docs/handbook/declaration-files/consumption.html). 

我们还必须安装`enzyme-adapter-react-16 and react-test-renderer`. 这是事情`enzyme`期望安装. 

在编写第一个测试之前,我们必须配置Enzyme以使用React 16的适配器. 我们将创建一个名为的文件在运行测试时自动加载: `src/setupTests.ts`现在我们已经设置了酶,让我们开始编写测试!

```ts
import * as enzyme from 'enzyme';
import * as Adapter from 'enzyme-adapter-react-16';

enzyme.configure({ adapter: new Adapter() });
```

让我们创建一个名为的文件,毗邻我们的`src/components/Hello.test.tsx`来自早先的文件. `Hello.tsx`这些测试非常基础,但你应该能够掌握一切. 

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

添加状态管理

# 此时,如果您使用React for只获取一次数据并显示它,您可以认为自己完成了. 

但是,如果您正在开发一个更具交互性的应用程序,那么您可能需要添加状态管理. 一般的国家管理

## React本身就是一个用于创建可组合视图的有用库. 

但是,React没有任何用于在您的应用程序之间同步数据的工具. 就React组件而言,数据通过您在子元素上指定的道具向下流动. 由于React本身不提供对状态管理的内置支持,因此React社区使用Redux和MobX等库. 

依赖于通过集中且不可变的数据存储来同步数据,对该数据的更新将触发我们的应用程序的重新呈现. 

[Redux](http://redux.js.org)通过发送必须由称为reducers的函数处理的显式操作消息,以不可变的方式更新状态. 由于具有明确的性质,通常更容易推断某个操作将如何影响您的程序状态. 依赖于功能反应模式,其中状态通过可观察量包裹并作为道具传递. 

[MobX](https://mobx.js.org/)通过简单地将状态标记为可观察状态来保持状态完全同步以用于任何观察者. 作为一个很好的奖励,该库已经用TypeScript编写. 两者都有各种优点和权衡. 

通常Redux倾向于看到更广泛的用法,因此为了本教程的目的,我们将专注于添加Redux;但是,你应该感到鼓励去探索两者. 以下部分可能有一个陡峭的学习曲线. 

我们强烈建议你. [familiarize yourself with Redux through its documentation](http://redux.js.org/)为行动设定阶段

## 除非我们的应用程序状态发生变化,否则添加Redux是没有意义的. 

我们需要一个可以触发更改的操作源. 

这可以是计时器,也可以是UI中的某个按钮. 为了我们的目的,我们将添加两个按钮来控制我们的热情程度`Hello`零件. 

## 安装Redux

要添加Redux,我们将首先安装`redux`和`react-redux`,以及它们的类型,作为依赖. 

```sh
npm install -S redux react-redux @types/react-redux
```

在这种情况下,我们不需要安装`@types/redux`因为Redux已经附带了自己的定义文件 (`.d.ts`文件) . 

## 定义我们的应用程序状态

我们需要定义Redux将存储的状态的形状. 为此,我们可以创建一个名为的文件`src/types/index.tsx`它将包含我们可能在整个程序中使用的类型的定义. 

```ts
// src/types/index.tsx

export interface StoreState {
    languageName: string;
    enthusiasmLevel: number;
}
```

我们的意图是`languageName`将是这个应用程序编写的编程语言 (即TypeScript或JavaScript) 和`enthusiasmLevel`会有所不同. 当我们编写第一个容器时,我们会理解为什么我们故意使我们的状态与我们的道具略有不同. 

## 添加动作

让我们从创建一组我们的应用可以响应的消息类型开始`src/constants/index.tsx`. 

```ts
// src/constants/index.tsx

export const INCREMENT_ENTHUSIASM = 'INCREMENT_ENTHUSIASM';
export type INCREMENT_ENTHUSIASM = typeof INCREMENT_ENTHUSIASM;


export const DECREMENT_ENTHUSIASM = 'DECREMENT_ENTHUSIASM';
export type DECREMENT_ENTHUSIASM = typeof DECREMENT_ENTHUSIASM;
```

这个`const`/`type`pattern允许我们以易于访问和可重构的方式使用TypeScript的字符串文字类型. 

接下来,我们将创建一组可以在其中创建这些操作的操作和功能`src/actions/index.tsx`. 

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

我们创建了两种类型来描述增量操作和减量操作应该是什么样子. 我们还创建了一个类型 (`EnthusiasmAction`) 描述一个动作可以是增量或减量的情况. 最后,我们制作了两个函数来实际制作我们可以使用的动作,而不是写出庞大的对象文字. 

这里有明显的样板,所以你应该随意查看类似的库[redux-actions](https://www.npmjs.com/package/redux-actions)一旦你掌握了一切. 

## 添加减速机

我们准备好写第一台减速机了!Reducers只是通过创建应用程序状态的修改副本来生成更改的函数,但具有*无副作用*. 换句话说,他们就是我们所说的*[pure functions](https://en.wikipedia.org/wiki/Pure_function)*. 

我们的减速机将进入`src/reducers/index.tsx`. 它的功能是确保增量将热情水平提高1,而减量将热情水平降低1,但水平从不低于1. 

```ts
// src/reducers/index.tsx

import { EnthusiasmAction } from '../actions';
import { StoreState } from '../types/index';
import { INCREMENT_ENTHUSIASM, DECREMENT_ENTHUSIASM } from '../constants/index';

export function enthusiasm(state: StoreState, action: EnthusiasmAction): StoreState {
  switch (action.type) {
    case INCREMENT_ENTHUSIASM:
      return { ...state, enthusiasmLevel: state.enthusiasmLevel + 1 };
    case DECREMENT_ENTHUSIASM:
      return { ...state, enthusiasmLevel: Math.max(1, state.enthusiasmLevel - 1) };
  }
  return state;
}
```

请注意,我们正在使用*对象传播* (`...state`) 它允许我们创建一个浅层的状态,同时替换`enthusiasmLevel`. 重要的是`enthusiasmLevel`财产是最后的,因为否则它将被我们旧州的财产所覆盖. 

您可能想为减速器编写一些测试. 由于reducer是纯函数,因此可以传递任意数据. 对于每个输入,可以通过检查其新生成的状态来测试减速器. 考虑一下Jest的观点[toEqual](https://facebook.github.io/jest/docs/expect.html#toequalvalue)实现这一目标的方法. 

## 制作一个容器

使用Redux编写时,我们经常会编写组件和容器. 组件通常与数据无关,并且主要在表示级别工作. *集装箱*通常包装组件并向其提供显示和修改状态所需的任何数据. 您可以阅读有关此概念的更多信息[Dan Abramov's article *Presentational and Container Components*](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0). 

首先让我们更新`src/components/Hello.tsx`这样它就可以修改状态. 我们将添加两个可选的回调属性`Props`命名`onIncrement`和`onDecrement`: 

```ts
export interface Props {
  name: string;
  enthusiasmLevel?: number;
  onIncrement?: () => void;
  onDecrement?: () => void;
}
```

然后我们将这些回调绑定到两个我们将添加到组件中的新按钮. 

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

一般来说,编写一些测试是个好主意`onIncrement`和`onDecrement`单击各自按钮时触发. 试一试为您的组件编写测试. 

现在我们的组件已更新,我们已准备好将其包装到容器中. 让我们创建一个名为的文件`src/containers/Hello.tsx`并从以下导入开始. 

```ts
import Hello from '../components/Hello';
import * as actions from '../actions/';
import { StoreState } from '../types/index';
import { connect, Dispatch } from 'react-redux';
```

这里真正的两个关键部分是原始的`Hello`组件以及`connect`函数来自react-redux. `connect`将能够真正采取我们的原创`Hello`组件并使用两个函数将其转换为容器: 

-   `mapStateToProps`它将来自当前商店的数据按摩到我们组件所需的部分形状. 
-   `mapDispatchToProps`它创建回调道具,使用给定的操作将动作泵送到我们的商店`dispatch`功能. 

如果我们记得,我们的应用程序状态包含两个属性: `languageName`和`enthusiasmLevel`. 我们的`Hello`另一方面,组件预期a`name`和`enthusiasmLevel`. `mapStateToProps`将从商店获取相关数据,并在必要时对我们组件的道具进行调整. 让我们继续写下来吧. 

```ts
export function mapStateToProps({ enthusiasmLevel, languageName }: StoreState) {
  return {
    enthusiasmLevel,
    name: languageName,
  }
}
```

注意`mapStateToProps`仅创建4个属性中的2个a`Hello`组件期望. 也就是说,我们仍然希望传入`onIncrement`和`onDecrement`回调. `mapDispatchToProps`是一个采用调度程序功能的函数. 此调度程序功能可以将操作传递到我们的商店以进行更新,因此我们可以创建一对将根据需要调用调度程序的回调. 

```ts
export function mapDispatchToProps(dispatch: Dispatch<actions.EnthusiasmAction>) {
  return {
    onIncrement: () => dispatch(actions.incrementEnthusiasm()),
    onDecrement: () => dispatch(actions.decrementEnthusiasm()),
  }
}
```

最后,我们准备打电话了`connect`. `connect`将首先采取`mapStateToProps`和`mapDispatchToProps`,然后返回另一个我们可以用来包装我们的组件的函数. 我们生成的容器使用以下代码行定义: 

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

## 创建商店

我们回去吧`src/index.tsx`. 要把这些放在一起,我们需要创建一个具有初始状态的商店,并使用我们所有的reducer进行设置. 

```ts
import { createStore } from 'redux';
import { enthusiasm } from './reducers/index';
import { StoreState } from './types/index';

const store = createStore<StoreState>(enthusiasm, {
  enthusiasmLevel: 1,
  languageName: 'TypeScript',
});
```

`store`正如您可能已经猜到的那样,我们的应用程序的全球状态的中央存储. 

接下来,我们将交换我们的使用`./src/components/Hello`同`./src/containers/Hello`并使用react-redux's`Provider`用我们的容器连接我们的道具. 我们将导入每个: 

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

请注意`Hello`不再需要道具,因为我们使用了道具`connect`功能使我们的应用程序的状态适应我们的包装`Hello`组件的道具. 

# 弹出

如果在任何时候,您觉得某些自定义设置使创建反应应用程序设置变得困难,您可以随时选择退出并获取所需的各种配置选项. 例如,如果您想添加Webpack插件,可能需要利用create-react-app提供的"弹出"功能. 

简单地跑

```sh
npm run eject
```

你应该好好去!

作为抬头,您可能希望在运行弹出之前提交所有工作. 您无法撤消弹出命令,因此选择退出是永久性的,除非您可以在运行弹出之前从提交中恢复. 

# 下一步

create-react-app附带了很多很棒的东西. 其中大部分都记录在默认情况下`README.md`这是为我们的项目生成的,所以请快速阅读. 

如果您仍想了解有关Redux的更多信息,您可以[check out the official website](http://redux.js.org/)用于文档. 同样的道理[for MobX](https://mobx.js.org/). 

如果你想在某些时候弹出,你可能需要更多地了解Webpack. 你可以看看我们的[React & Webpack walkthrough here](https://www.typescriptlang.org/docs/handbook/react-&-webpack.html). 

在某些时候,您可能需要路由. 有几种解决方案,但是[react-router](https://github.com/ReactTraining/react-router)可能是Redux项目中最受欢迎的,并且经常与之结合使用[react-router-redux](https://github.com/reactjs/react-router-redux). 
