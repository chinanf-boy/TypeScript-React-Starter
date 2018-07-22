
这个项目是自助式的[Create React App](https://github.com/facebookincubator/create-react-app). 

您将在下面找到有关如何执行常见任务的一些信息. <br>您可以找到本指南的最新版本[here](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md). 

## 目录

-   [Updating to New Releases](#updating-to-new-releases)
-   [Sending Feedback](#sending-feedback)
-   [Folder Structure](#folder-structure)
-   [Available Scripts](#available-scripts)
    -   [npm start](#npm-start)
    -   [npm test](#npm-test)
    -   [npm run build](#npm-run-build)
    -   [npm run eject](#npm-run-eject)
-   [Syntax Highlighting in the Editor](#syntax-highlighting-in-the-editor)
-   [Displaying Lint Output in the Editor](#displaying-lint-output-in-the-editor)
-   [Changing the Page `<title>`](#changing-the-page-title)
-   [Installing a Dependency](#installing-a-dependency)
-   [Importing a Component](#importing-a-component)
-   [Adding a Stylesheet](#adding-a-stylesheet)
-   [Post-Processing CSS](#post-processing-css)
-   [Adding Images and Fonts](#adding-images-and-fonts)
-   [Using the `public` Folder](#using-the-public-folder)
    -   [Changing the HTML](#changing-the-html)
    -   [Adding Assets Outside of the Module System](#adding-assets-outside-of-the-module-system)
    -   [When to Use the `public` Folder](#when-to-use-the-public-folder)
-   [Using Global Variables](#using-global-variables)
-   [Adding Bootstrap](#adding-bootstrap)
-   [Adding Flow](#adding-flow)
-   [Adding Custom Environment Variables](#adding-custom-environment-variables)
-   [Can I Use Decorators?](#can-i-use-decorators)
-   [Integrating with a Node Backend](#integrating-with-a-node-backend)
-   [Proxying API Requests in Development](#proxying-api-requests-in-development)
-   [Using HTTPS in Development](#using-https-in-development)
-   [Generating Dynamic `<meta>` Tags on the Server](#generating-dynamic-meta-tags-on-the-server)
-   [Running Tests](#running-tests)
    -   [Filename Conventions](#filename-conventions)
    -   [Command Line Interface](#command-line-interface)
    -   [Version Control Integration](#version-control-integration)
    -   [Writing Tests](#writing-tests)
    -   [Testing Components](#testing-components)
    -   [Using Third Party Assertion Libraries](#using-third-party-assertion-libraries)
    -   [Initializing Test Environment](#initializing-test-environment)
    -   [Focusing and Excluding Tests](#focusing-and-excluding-tests)
    -   [Coverage Reporting](#coverage-reporting)
    -   [Continuous Integration](#continuous-integration)
    -   [Disabling jsdom](#disabling-jsdom)
    -   [Experimental Snapshot Testing](#experimental-snapshot-testing)
    -   [Editor Integration](#editor-integration)
-   [Developing Components in Isolation](#developing-components-in-isolation)
-   [Making a Progressive Web App](#making-a-progressive-web-app)
-   [Deployment](#deployment)
    -   [Serving Apps with Client-Side Routing](#serving-apps-with-client-side-routing)
    -   [Building for Relative Paths](#building-for-relative-paths)
    -   [Firebase](#firebase)
    -   [GitHub Pages](#github-pages)
    -   [Heroku](#heroku)
    -   [Modulus](#modulus)
    -   [Netlify](#netlify)
    -   [Now](#now)
    -   [S3 and CloudFront](#s3-and-cloudfront)
    -   [Surge](#surge)
-   [Troubleshooting](#troubleshooting)
    -   [`npm test` hangs on macOS Sierra](#npm-test-hangs-on-macos-sierra)
    -   [`npm run build` silently fails](#npm-run-build-silently-fails)
    -   [`npm run build` fails on Heroku](#npm-run-build-fails-on-heroku)
-   [Something Missing?](#something-missing)

## 更新到新版本

Create React App分为两个包: 

-   `create-react-app`是一个全局命令行实用程序,可用于创建新项目. 
-   `react-scripts`是生成的项目中的开发依赖项 (包括此项) . 

你几乎不需要更新`create-react-app`本身: 它将所有设置委托给`react-scripts`. 

当你跑步`create-react-app`,它始终使用最新版本创建项目`react-scripts`这样您就可以自动获得新创建的应用程序的所有新功能和改进. 

将现有项目更新为新版本`react-scripts`,[open the changelog](https://github.com/facebookincubator/create-react-app/blob/master/CHANGELOG.md),找到你当前所在的版本 (检查`package.json`如果您不确定,请在此文件夹中) ,并应用较新版本的迁移说明. 

在大多数情况下碰撞`react-scripts`版本`package.json`并运行`npm install`在这个文件夹中应该足够了,但最好咨询一下[changelog](https://github.com/facebookincubator/create-react-app/blob/master/CHANGELOG.md)潜在的突破性变化. 

我们承诺将破坏性变化保持在最低限度,以便您可以升级`react-scripts`怕疼. 

## 发送反馈

我们始终愿意接受[your feedback](https://github.com/facebookincubator/create-react-app/issues). 

## 文件夹结构

创建后,您的项目应如下所示: 

    my-app/
      README.md
      node_modules/
      package.json
      public/
        index.html
        favicon.ico
      src/
        App.css
        App.js
        App.test.js
        index.css
        index.js
        logo.svg

对于要构建的项目,**这些文件必须与确切的文件名一起存在**: 

-   `public/index.html`是页面模板;
-   `src/index.js`是JavaScript入口点. 

您可以删除或重命名其他文件. 

您可以在里面创建子目录`src`. 为了更快地重建,只有里面的文件`src`由Webpack处理. <br>你需要**将任何JS和CSS文件放入其中`src`**,或Webpack不会看到它们. 

只有里面的文件`public`可以使用`public/index.html`. <br>阅读以下有关使用JavaScript和HTML资源的说明. 

但是,您可以创建更多顶级目录. <br>它们不会包含在生产版本中,因此您可以将它们用于文档等内容. 

## 可用的脚本

在项目目录中,您可以运行: 

### `npm start`

在开发模式下运行应用程序. <br>打开<http://localhost:3000>在浏览器中查看它. 

如果您进行编辑,页面将重新加载. <br>您还将在控制台中看到任何lint错误. 

### `npm test`

以交互式监视模式启动测试运行器. <br>请参阅有关的部分[running tests](#running-tests)了解更多信息. 

### `npm run build`

构建用于生产的应用程序`build`夹. <br>它正确地将React捆绑在生产模式中并优化构建以获得最佳性能. 

构建被缩小,文件名包含哈希. <br>您的应用已准备好部署!

请参阅有关的部分[deployment](#deployment)了解更多信息. 

### `npm run eject`

**注意: 这是单向操作. 一旦您`eject`,你不能回去!**

如果您对构建工具和配置选择不满意,则可以`eject`随时. 此命令将从项目中删除单个构建依赖项. 

相反,它会将所有配置文件和传递依赖项 (Webpack,Babel,TSLint等) 复制到您的项目中,以便您可以完全控制它们. 除了以外的所有命令`eject`仍然可以工作,但他们会指向复制的脚本,以便您可以调整它们. 在这一点上,你是独立的. 

你不必使用`eject`. 精选功能集适用于中小型部署,您不应觉得有义务使用此功能. 但是,我们知道如果您准备好它时无法自定义此工具将无用. 

## 编辑器中的语法突出显示

要在您喜欢的文本编辑器中配置语法突出显示,请转到[relevant Babel documentation page](https://babeljs.io/docs/editors)并按照说明操作. 一些最受欢迎的编辑被覆盖. 

## 在编辑器中显示Lint输出

> 注意: 此功能适用于`react-scripts@0.2.0`更高. 

一些编辑器,包括Sublime Text,Atom和Visual Studio Code,为TSLint提供插件. 

它们不是褪色所必需的. 您应该在终端和浏览器控制台中看到linter输出. 但是,如果您希望将lint结果显示在编辑器中,则可以执行一些额外的步骤. 

您需要先为编辑器安装TSLint插件. 

## 改变页面`<title>`

您可以在中找到源HTML文件`public`生成的项目的文件夹. 你可以编辑`<title>`标记在其中以将标题从"React App"更改为其他任何内容. 

请注意,通常您不会编辑文件中的文件`public`文件夹经常. 例如,[adding a stylesheet](#adding-a-stylesheet)是在不触及HTML的情况下完成的. 

如果您需要根据内容动态更新页面标题,则可以使用浏览器[`document.title`](https://developer.mozilla.org/en-US/docs/Web/API/Document/title)API. 对于更复杂的场景,当您想要从React组件更改标题时,您可以使用[React Helmet](https://github.com/nfl/react-helmet),第三方图书馆. 

最后,如果您在生产中为自己的应用程序使用自定义服务器,并希望在将标题发送到浏览器之前修改标题,则可以按照以下建议进行操作[this section](#generating-dynamic-meta-tags-on-the-server). 

## 安装依赖项

生成的项目包括React和ReactDOM作为依赖项. 它还包括Create React App用作开发依赖项的一组脚本. 您可以安装其他依赖项 (例如,React Router) `npm`: 

    npm install --save <library-name>

## 导入组件

由于Babel,该项目设置支持ES6模块. <br>虽然你仍然可以使用`require()`和`module.exports`,我们鼓励您使用[`import` and `export`](http://exploringjs.com/es6/ch_modules.html)代替. 

例如: 

### `Button.js`

```js
import React, { Component } from 'react';

class Button extends Component {
  render() {
    // ...
  }
}

export default Button; // Don’t forget to use export default!
```

### `DangerButton.js`

```js
import React, { Component } from 'react';
import Button from './Button'; // Import a component from another file

class DangerButton extends Component {
  render() {
    return <Button color="red" />;
  }
}

export default DangerButton;
```

注意这个[difference between default and named exports](http://stackoverflow.com/questions/36795819/react-native-es-6-when-should-i-use-curly-braces-for-import/36796281#36796281). 这是一个常见的错误来源. 

我们建议您在模块仅导出单个内容 (例如,组件) 时坚持使用默认导入和导出. 这就是你使用时得到的`export default Button`和`import Button from './Button'`. 

命名导出对于导出多个函数的实用程序模块很有用. 一个模块最多可以有一个默认导出和任意多个命名导出. 

了解有关ES6模块的更多信息: 

-   [When to use the curly braces?](http://stackoverflow.com/questions/36795819/react-native-es-6-when-should-i-use-curly-braces-for-import/36796281#36796281)
-   [Exploring ES6: Modules](http://exploringjs.com/es6/ch_modules.html)
-   [Understanding ES6: Modules](https://leanpub.com/understandinges6/read#leanpub-auto-encapsulating-code-with-modules)

## 添加样式表

此项目设置使用[Webpack](https://webpack.github.io/)处理所有资产. Webpack提供了一种"扩展"概念的定制方式`import`超越JavaScript. 要表明JavaScript文件依赖于CSS文件,您需要**从JavaScript文件导入CSS**: 

### `Button.css`

```css
.Button {
  padding: 20px;
}
```

### `Button.js`

```js
import React, { Component } from 'react';
import './Button.css'; // Tell Webpack that Button.js uses these styles

class Button extends Component {
  render() {
    // You can use them as regular CSS styles
    return <div className="Button" />;
  }
}
```

**这不是React所必需的**但很多人发现这个功能很方便. 您可以阅读这种方法的好处[here](https://medium.com/seek-ui-engineering/block-element-modifying-your-javascript-components-d7f99fcab52b). 但是,您应该知道,这使得您的代码比Webpack更不容易移植到其他构建工具和环境. 

在开发过程中,通过这种方式表达依赖关系,可以在编辑样式时动态重新加载样式. 在生产中,所有CSS文件将连接成一个缩小的`.css`构建输出中的文件. 

如果您担心使用特定于Webpack的语义,则可以将所有CSS放入其中`src/index.css`. 它仍然会从中导入`src/index.js`,但如果稍后迁移到其他构建工具,则可以始终删除该导入. 

## 后处理CSS

此项目设置会缩小您的CSS并自动添加供应商前缀[Autoprefixer](https://github.com/postcss/autoprefixer)所以你不必担心它. 

例如,这个: 

```css
.App {
  display: flex;
  flex-direction: row;
  align-items: center;
}
```

成为这个: 

```css
.App {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: horizontal;
  -webkit-box-direction: normal;
      -ms-flex-direction: row;
          flex-direction: row;
  -webkit-box-align: center;
      -ms-flex-align: center;
          align-items: center;
}
```

目前不支持预处理器,如Less,或者用于跨CSS文件共享变量. 

## 添加图像和字体

使用Webpack,使用图像和字体等静态资源的工作方式与CSS类似. 

您可以**`import`JavaScript模块中的图像**. 这告诉Webpack将该图像包含在包中. 与CSS导入不同,导入图像或字体会为您提供字符串值. 此值是您可以在代码中引用的最终图像路径. 

这是一个例子: 

```js
import React from 'react';
import logo from './logo.png'; // Tell Webpack this JS file uses this image

console.log(logo); // /logo.84287d09.png

function Header() {
  // Import result is the URL of your image
  return <img src={logo} alt="Logo" />;
}

export default Header;
```

这确保了在构建项目时,Webpack将正确地将图像移动到构建文件夹中,并为我们提供正确的路径. 

这也适用于CSS: 

```css
.Logo {
  background-image: url(./logo.png);
}
```

Webpack在CSS中查找所有相关模块引用 (它们以`./`) 并用编译的bundle中的最终路径替换它们. 如果输入拼写错误或意外删除重要文件,您将看到编译错误,就像导入不存在的JavaScript模块一样. 编译包中的最终文件名由Webpack从内容哈希生成. 如果文件内容将来发生变化,Webpack将在生产中为其指定一个不同的名称,因此您无需担心资产的长期缓存. 

请注意,这也是Webpack的自定义功能. 

**React不需要它**但很多人都喜欢它 (React Native使用类似的图像机制) . <br>处理静态资产的另一种方法将在下一节中介绍. 

## 使用`public`夹

> 注意: 此功能适用于`react-scripts@0.5.0`更高. 

### 更改HTML

该`public`文件夹包含HTML文件,因此您可以调整它,例如[set the page title](#changing-the-page-title). 该`<script>`带有编译代码的标记将在构建过程中自动添加到其中. 

### 在模块系统之外添加资产

您还可以添加其他资产`public`夹. 

请注意,我们通常会鼓励您`import`相反,JavaScript文件中的资产. 例如,请参阅相关章节[adding a stylesheet](#adding-a-stylesheet)和[adding images and fonts](#adding-images-and-fonts). 这种机制提供了许多好处: 

-   脚本和样式表被缩小并捆绑在一起以避免额外的网络请求. 
-   缺少文件会导致编译错误,而不是用户的404错误. 
-   结果文件名包含内容哈希,因此您无需担心浏览器缓存旧版本. 

但是有一个**逃生舱口**您可以用来在模块系统之外添加资产. 

如果你把文件放入`public`文件夹,它会**不**由Webpack处理. 相反,它将被复制到构建文件夹中. 参考资产`public`在文件夹中,您需要使用一个名为的特殊变量`PUBLIC_URL`. 

内`index.html`,你可以像这样使用它: 

```html
<link rel="shortcut icon" href="%PUBLIC_URL%/favicon.ico">
```

只有里面的文件`public`文件夹将可访问`%PUBLIC_URL%`字首. 如果您需要使用来自的文件`src`要么`node_modules`,您必须将其复制到那里以明确指定您将此文件作为构建的一部分的意图. 

当你跑步`npm run build`,创建React App将替代`%PUBLIC_URL%`使用正确的绝对路径,即使您使用客户端路由或将其托管在非根URL,您的项目仍然有效. 

在JavaScript代码中,您可以使用`process.env.PUBLIC_URL`出于类似目的: 

```js
render() {
  // Note: this is an escape hatch and should be used sparingly!
  // Normally we recommend using `import` for getting asset URLs
  // as described in “Adding Images and Fonts” above this section.
  return <img src={process.env.PUBLIC_URL + '/img/logo.png'} />;
}
```

请记住这种方法的缺点: 

-   没有任何文件`public`文件夹得到后处理或缩小. 
-   在编译时不会调用丢失的文件,并且会导致用户出现404错误. 
-   结果文件名不包含内容哈希值,因此您需要添加查询参数或在每次更改时重命名它们. 

### 何时使用`public`夹

通常我们建议导入[stylesheets](#adding-a-stylesheet),[images, and fonts](#adding-images-and-fonts)来自JavaScript. 该`public`文件夹可用作许多不常见情况的解决方法: 

-   您需要在构建输出中具有特定名称的文件,例如[`manifest.webmanifest`](https://developer.mozilla.org/en-US/docs/Web/Manifest). 
-   您有数千个图像,需要动态引用它们的路径. 
-   你想要包含一个像这样的小脚本[`pace.js`](http://github.hubspot.com/pace/docs/welcome/)在捆绑代码之外. 
-   某些库可能与Webpack不兼容,您没有其他选择,只能将其包含为`<script>`标签. 

请注意,如果添加一个`<script>`声明全局变量,您还需要阅读下一节使用它们. 

## 使用全局变量

当您在HTML文件中包含一个定义全局变量并尝试在代码中使用这些变量之一的脚本时,linter会抱怨,因为它无法看到变量的定义. 

你可以通过从中明确地读取全局变量来避免这种情况`window`对象,例如: 

```js
const $ = window.$;
```

这显然是你故意使用全局变量而不是因为拼写错误. 

或者,您可以通过添加强制linter忽略任何行`// tslint:disable-line`在它之后. 

## 添加Bootstrap

你不必使用[React Bootstrap](https://react-bootstrap.github.io)与React一起,但它是一个流行的库,用于集成Bootstrap和React应用程序. 如果需要,可以按照以下步骤将其与Create React App集成: 

从NPM安装React Bootstrap和Bootstrap. React Bootstrap不包含Bootstrap CSS,所以这也需要安装: 

    npm install react-bootstrap --save
    npm install bootstrap@3 --save

导入Bootstrap CSS和可选的Bootstrap主题CSS`src/index.js`文件: 

```js
import 'bootstrap/dist/css/bootstrap.css';
import 'bootstrap/dist/css/bootstrap-theme.css';
```

在其中导入所需的React Bootstrap组件`src/App.js`文件或您的自定义组件文件: 

```js
import { Navbar, Jumbotron, Button } from 'react-bootstrap';
```

现在,您已准备好在render方法中定义的组件层次结构中使用导入的React Bootstrap组件. 这是一个例子[`App.js`](https://gist.githubusercontent.com/gaearon/85d8c067f6af1e56277c82d19fd4da7b/raw/6158dd991b67284e9fc8d70b9d973efe87659d72/App.js)使用React Bootstrap重做. 

## 添加流量

Flow是一种静态类型检查器,可帮助您编写具有更少错误的代码. 看看这个[introduction to using static types in JavaScript](https://medium.com/@preethikasireddy/why-use-static-types-in-javascript-part-1-8382da1e0adb)如果你是这个概念的新手. 

最近的版本[Flow](http://flowtype.org/)使用Create React App项目开箱即用. 

要将Flow添加到Create React App项目,请按照下列步骤操作: 

1.  跑`npm install --save-dev flow-bin`. 
2.  加`"flow": "flow"`到了`scripts`你的部分`package.json`. 
3.  加`// @flow`到您要键入的任何文件检查 (例如,到`src/App.js`) . 

现在你可以跑了`npm run flow`检查文件的类型错误. 您可以选择使用IDE[Nuclide](https://nuclide.io/docs/languages/flow/)为了更好的综合体验. 在未来,我们计划将其更紧密地集成到Create React App中. 

要了解有关Flow的更多信息,请查看[its documentation](https://flowtype.org/). 

## 添加自定义环境变量

> 注意: 此功能适用于`react-scripts@0.2.3`更高. 

您的项目可以使用在您的环境中声明的变量,就好像它们是在JS文件中本地声明的一样. 默认情况下你会有`NODE_ENV`为您定义,以及以. 开头的任何其他环境变量`REACT_APP_`. 将为您定义这些环境变量`process.env`. 例如,具有名为的环境变量`REACT_APP_SECRET_CODE`将在您的JS中公开`process.env.REACT_APP_SECRET_CODE`, 此外`process.env.NODE_ENV`. 

> 注意: 更改任何环境变量将要求您在运行时重新启动开发服务器. 

这些环境变量可用于根据项目的部署位置有条件地显示信息,或者使用生活在版本控制之外的敏感数据. 

首先,您需要定义环境变量. 例如,假设您想要使用在环境中定义的秘密`<form>`: 

```jsx
render() {
  return (
    <div>
      <small>You are running this application in <b>{process.env.NODE_ENV}</b> mode.</small>
      <form>
        <input type="hidden" defaultValue={process.env.REACT_APP_SECRET_CODE} />
      </form>
    </div>
  );
}
```

在构建期间,`process.env.REACT_APP_SECRET_CODE`将被替换为当前的值`REACT_APP_SECRET_CODE`环境变量. 记得那个`NODE_ENV`变量将自动为您设置. 

在浏览器中加载应用程序并检查时`<input>`,你会看到它的值设置为`abcdef`,粗体文本将显示使用时提供的环境`npm start`: 

```html
<div>
  <small>You are running this application in <b>development</b> mode.</small>
  <form>
    <input type="hidden" value="abcdef" />
  </form>
</div>
```

有权访问`NODE_ENV`对于有条件地执行操作也很有用: 

```js
if (process.env.NODE_ENV !== 'production') {
  analytics.disable();
}
```

上面的表格正在寻找一个名为的变量`REACT_APP_SECRET_CODE`来自环境. 为了消耗这个值,我们需要在环境中定义它. 这可以通过两种方式完成: 在shell中或在`.env`文件. 

### 在Shell中添加临时环境变量

定义环境变量可能因操作系统而异. 同样重要的是要知道这种方式对于shell会话的生命是暂时的. 

#### Windows (cmd.exe) 

```cmd
set REACT_APP_SECRET_CODE=abcdef&&npm start
```

 (注意: 缺少空格是故意的. ) 

#### Linux,OS X (Bash) 

```bash
REACT_APP_SECRET_CODE=abcdef npm start
```

### 添加开发环境变量`.env`

> 注意: 此功能适用于`react-scripts@0.5.0`更高. 

要定义永久环境变量,请创建一个名为的文件`.env`在项目的根目录中: 

    REACT_APP_SECRET_CODE=abcdef

如果机器没有明确设置它们,这些变量将作为默认值. <br>请参考[dotenv documentation](https://github.com/motdotla/dotenv)更多细节. 

> 注意: 如果要为开发定义环境变量,则CI和/或托管平台很可能也需要定义这些变量. 请参阅他们的文档如何执行此操作. 例如,请参阅文档[Travis CI](https://docs.travis-ci.com/user/environment-variables/)要么[Heroku](https://devcenter.heroku.com/articles/config-vars). 

## 我可以使用装饰器吗?

许多流行的图书馆使用[decorators](https://medium.com/google-developers/exploring-es7-decorators-76ecb65fb841)在他们的文件中. <br>创建React App目前不支持装饰器语法,因为: 

-   这是一项实验性提案,可能会有所变化. 
-   Babel不正式支持当前的规范版本. 
-   如果规范发生变化,我们将无法编写codemod,因为我们不会在Facebook内部使用它们. 

但是在许多情况下,您可以在没有装饰器的情况下重写基于装饰器的代码. <br>请参考这两个主题以供参考: 

-   [#214](https://github.com/facebookincubator/create-react-app/issues/214)
-   [#411](https://github.com/facebookincubator/create-react-app/issues/411)

当规范进入稳定阶段时,创建React App将添加装饰器支持. 

## 与节点后端集成

查看[this tutorial](https://www.fullstackreact.com/articles/using-create-react-app-with-a-server/)有关将应用程序与在另一个端口上运行的Node后端集成以及使用的说明`fetch()`访问它. 您可以找到伴随的GitHub存储库[here](https://github.com/fullstackreact/food-lookup-demo). 

## 在开发中代理API请求

> 注意: 此功能适用于`react-scripts@0.2.3`更高. 

人们经常从与后端实现相同的主机和端口提供前端React应用程序. <br>例如,在部署应用程序后,生产设置可能如下所示: 

    /             - static server returns index.html with React app
    /todos        - static server returns index.html with React app
    /api/todos    - server handles any /api/* requests using the backend implementation

这样的设置是**不**需要. 但是,如果你**做**有这样的设置,写入请求很方便`fetch('/api/todos')`在开发过程中不必担心将它们重定向到另一个主机或端口. 

要告诉开发服务器将任何未知请求代理到开发中的API服务器,请添加一个`proxy`你的领域`package.json`, 例如: 

```js
  "proxy": "http://localhost:4000",
```

这样,当你`fetch('/api/todos')`在开发中,开发服务器将识别它不是静态资产,并将代理您的请求`http://localhost:4000/api/todos`作为后备. 开发服务器只会尝试在没有的情况下发送请求`text/html`接受代理的标头. 

方便地,这避免了[CORS issues](http://stackoverflow.com/questions/21854516/understanding-ajax-cors-and-security-considerations)和开发中的这样的错误消息: 

    Fetch API cannot load http://localhost:4000/api/todos. No 'Access-Control-Allow-Origin' header is present on the requested resource. Origin 'http://localhost:3000' is therefore not allowed access. If an opaque response serves your needs, set the request's mode to 'no-cors' to fetch the resource with CORS disabled.

请记住`proxy`只对发展有影响 (有`npm start`) ,并由您来确保URL类似`/api/todos`在生产中指向正确的事物. 你不必使用`/api`字首. 任何无法识别的请求没有`text/html`accept标头将被重定向到指定的`proxy`. 

目前`proxy`选项仅处理HTTP请求,并且不会代理WebSocket连接. <br>如果`proxy`选项是**不**足够灵活,你可以: 

-   在服务器上启用CORS ([here’s how to do it for Express](http://enable-cors.org/server_expressjs.html)) . 
-   使用[environment variables](#adding-custom-environment-variables)将正确的服务器主机和端口注入您的应用程序. 

## 在开发中使用HTTPS

> 注意: 此功能适用于`react-scripts@0.4.0`更高. 

您可能需要开发服务器通过HTTPS提供页面. 这可能有用的一个特殊情况是使用时[the "proxy" feature](#proxying-api-requests-in-development)当API服务器本身为HTTPS服务时,将请求代理到API服务器. 

为此,请设置`HTTPS`环境变量`true`,然后像往常一样启动开发服务器`npm start`: 

#### Windows (cmd.exe) 

```cmd
set HTTPS=true&&npm start
```

 (注意: 缺少空格是故意的. ) 

#### Linux,OS X (Bash) 

```bash
HTTPS=true npm start
```

请注意,服务器将使用自签名证书,因此您的Web浏览器在访问页面时几乎肯定会显示警告. 

## 生成动态`<meta>`服务器上的标签

由于Create React App不支持服务器渲染,因此您可能想知道如何制作`<meta>`标签动态并反映当前的URL. 要解决此问题,我们建议在HTML中添加占位符,如下所示: 

```html
<!doctype html>
<html lang="en">
  <head>
    <meta property="og:title" content="%OG_TITLE%">
    <meta property="og:description" content="%OG_DESCRIPTION%">
```

然后,在服务器上,无论您使用哪个后端,都可以阅读`index.html`进入记忆并取代`%OG_TITLE%`,`%OG_DESCRIPTION%`,以及具有取决于当前URL的值的任何其他占位符. 只需确保清理并转义插值,以便将它们嵌入到HTML中是安全的!

如果使用节点服务器,甚至可以在客户端和服务器之间共享路由匹配逻辑. 然而,重复它也可以在简单的情况下正常工作. 

## 运行测试

> 注意: 此功能适用于`react-scripts@0.3.0`更高. <br>
> [Read the migration guide to learn how to enable it in older projects!](https://github.com/facebookincubator/create-react-app/blob/master/CHANGELOG.md#migrating-from-023-to-030)

创建React App使用[Jest](https://facebook.github.io/jest/)作为其试运行者. 为了准备这种整合,我们做了一个[major revamp](https://facebook.github.io/jest/blog/2016/09/01/jest-15.html)Jest所以,如果你在几年前听到它的坏话,再试一次. 

Jest是一个基于节点的跑步者. 这意味着测试始终在Node环境中运行,而不是在真实的浏览器中运行. 这使我们能够实现快速迭代速度并防止碎片. 

虽然Jest提供了诸如的浏览器全局变量`window`谢谢[jsdom](https://github.com/tmpvar/jsdom),它们只是真实浏览器行为的近似值. Jest旨在用于逻辑和组件的单元测试,而不是DOM怪癖. 

如果您需要,我们建议您使用单独的工具进行浏览器端到端测试. 它们超出了Create React App的范围. 

### 文件名约定

Jest将使用以下任何流行的命名约定来查找测试文件: 

-   文件用`.js`后缀`__tests__`文件夹. 
-   文件用`.test.js`后缀. 
-   文件用`.spec.js`后缀. 

该`.test.js`/`.spec.js`文件 (或`__tests__`文件夹) 可以位于任何深度下`src`顶级文件夹. 

我们建议放置测试文件 (或`__tests__`文件夹) 他们正在测试的代码旁边,以便相对导入显得更短. 例如,如果`App.test.js`和`App.js`在同一个文件夹中,测试只需要`import App from './App'`而不是一个长的相对路径. 主机托管还有助于在大型项目中更快地找到测试. 

### 命令行界面

当你跑步`npm test`,Jest将在观看模式下推出. 每次保存文件时,它都会重新运行测试,就像`npm start`重新编译代码. 

观察者包括一个交互式命令行界面,能够运行所有测试,或专注于搜索模式. 它以这种方式设计,以便您可以保持打开状态并享受快速重新运行. 您可以从每次运行后观察者打印的"Watch Usage"注释中学习命令: 

![Jest watch mode](http://facebook.github.io/jest/img/blog/15-watch.gif)

### 版本控制集成

默认情况下,当您运行时`npm test`,Jest只会运行与上次提交后更改的文件相关的测试. 这是一项优化,旨在使您的测试快速运行,无论您拥有多少测试. 但是,它假定您不经常提交未通过测试的代码. 

Jest将始终明确提到它只运行与自上次提交后更改的文件相关的测试. 你也可以按`a`在监视模式下强制Jest运行所有测试. 

Jest将始终在a上运行所有测试[continuous integration](#continuous-integration)服务器或项目不在Git或Mercurial存储库中. 

### 写测试

要创建测试,请添加`it()` (要么`test()`) 具有测试名称及其代码的块. 您可以选择将它们包装起来`describe()`用于逻辑分组的块,但这既不是必需的也不是推荐的. 

Jest提供内置功能`expect()`断言的全局函数. 基本测试可能如下所示: 

```js
import sum from './sum';

it('sums numbers', () => {
  expect(sum(1, 2)).toEqual(3);
  expect(sum(2, 2)).toEqual(4);
});
```

所有`expect()`Jest支持的匹配器[extensively documented here](http://facebook.github.io/jest/docs/api.html#expect-value). <br>你也可以使用[`jest.fn()` and `expect(fn).toBeCalled()`](http://facebook.github.io/jest/docs/api.html#tobecalled)创建"间谍"或模拟功能. 

### 测试组件

有广泛的组件测试技术. 它们的范围从"冒烟测试"验证组件渲染而不抛出,浅层渲染和测试一些输出,到完全渲染和测试组件生命周期和状态更改. 

不同的项目根据组件更改的频率以及它们包含的逻辑程度来选择不同的测试权衡. 如果您尚未确定测试策略,我们建议您首先为组件创建简单的冒烟测试: 

```js
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

it('renders without crashing', () => {
  const div = document.createElement('div');
  ReactDOM.render(<App />, div);
});
```

此测试将安装一个组件,并确保它在渲染过程中不会抛出. 像这样的测试只需很少的努力即可提供很多价值,因此它们非常适合作为起点,这是您将在`src/App.test.js`. 

当您遇到因更改组件而导致的错误时,您将更深入地了解它们的哪些部分值得在您的应用程序中进行测试. 这可能是引入更具体的测试以确定特定预期输出或行为的好时机. 

如果您希望独立于它们渲染的子组件测试组件,我们建议您使用[`shallow()` rendering API](http://airbnb.io/enzyme/docs/api/shallow.html)从[Enzyme](http://airbnb.io/enzyme/). 你也可以用它来写一个烟雾测试: 

```sh
npm install --save-dev enzyme react-addons-test-utils
```

```js
import React from 'react';
import { shallow } from 'enzyme';
import App from './App';

it('renders without crashing', () => {
  shallow(<App />);
});
```

与以前的烟雾测试不同`ReactDOM.render()`,这个测试只能渲染`<App>`而且不会更深入. 例如,即使`<App>`本身就是一个`<Button>`抛出,这个测试将通过. 浅层渲染非常适合隔离单元测试,但您可能仍希望创建一些完整的渲染测试以确保组件正确集成. 酶支持[full rendering with `mount()`](http://airbnb.io/enzyme/docs/api/mount.html),您还可以使用它来测试状态更改和组件生命周期. 

你可以看看[Enzyme documentation](http://airbnb.io/enzyme/)了解更多测试技术. 酶文档使用Chai和Sinon进行断言,但您不必使用它们,因为Jest提供了内置功能`expect()`和`jest.fn()`对于间谍. 

以下是Enzyme文档中的一个示例,该文档断言特定输出,重写为使用Jest匹配器: 

```js
import React from 'react';
import { shallow } from 'enzyme';
import App from './App';

it('renders welcome message', () => {
  const wrapper = shallow(<App />);
  const welcome = <h2>Welcome to React</h2>;
  // expect(wrapper.contains(welcome)).to.equal(true);
  expect(wrapper.contains(welcome)).toEqual(true);
});
```

所有Jest匹配器都是[extensively documented here](http://facebook.github.io/jest/docs/api.html#expect-value). <br>不过你可以使用第三方断言库[Chai](http://chaijs.com/)如果你愿意,如下所述. 

### 使用第三方断言库

我们建议您使用`expect()`断言和`jest.fn()`对于间谍. 如果您遇到问题,请[file those against Jest](https://github.com/facebook/jest/issues/new),我们将解决它们. 我们打算继续让它们更好地用于React,例如支持[pretty-printing React elements as JSX](https://github.com/facebook/jest/pull/1566). 

但是,如果您习惯了其他库,例如[Chai](http://chaijs.com/)和[Sinon](http://sinonjs.org/),或者如果你有使用它们的现有代码,你想要移植它们,你可以像这样正常导入它们: 

```js
import sinon from 'sinon';
import { expect } from 'chai';
```

然后像往常一样在测试中使用它们. 

### 初始化测试环境

> 注意: 此功能适用于`react-scripts@0.4.0`更高. 

如果您的应用使用了需要在测试中进行模拟的浏览器API,或者在运行测试之前只需要全局设置,请添加`src/setupTests.ts`到你的项目. 它将在运行测试之前自动执行. 

例如: 

#### `src/setupTests.ts`

```js
declare global {
    interface localStorage {
        getItem: any;
        setItem: any;
        clean: any;
    }
}

class LocalStorageMock {
  store = {};
  clear() {
    this.store = {};
  }
  getItem(key: any) {
    return this.store[key];
  }
  setItem(key: any, value: any) {
    this.store[key] = value.toString();
  }
};

global.localStorage = new LocalStorageMock();
```

### 聚焦和排除测试

你可以替换`it()`同`xit()`临时排除测试被执行. <br>同样的,`fit()`让您专注于特定测试而无需运行任何其他测试. 

### 覆盖率报告

Jest有一个集成的覆盖率报告器,可以很好地与ES6配合使用,无需配置. <br>跑`npm test -- --coverage` (另外注意`--`在中间) 包括这样的报道报告: 

![coverage report](http://i.imgur.com/5bFhnTS.png)

请注意,测试运行速度要慢得多,因此建议将其与正常工作流程分开运行. 

### 持续集成

默认`npm test`使用交互式CLI运行观察程序. 但是,您可以强制它运行一次测试并通过设置一个名为的环境变量来完成该过程`CI`. 

使用时创建应用程序的构建`npm run build`默认情况下不会检查linter警告. 喜欢`npm test`,您可以通过设置环境变量强制构建执行linter警告检查`CI`. 如果遇到任何警告,则构建失败. 

流行的CI服务器已经设置了环境变量`CI`默认情况下你也可以自己做: 

### 在CI服务器上

#### 特拉维斯CI

1.  以下[Travis Getting started](https://docs.travis-ci.com/user/getting-started/)将您的GitHub存储库与Travis同步的指南. 您可能需要手动初始化一些设置[profile](https://travis-ci.org/profile)页. 
2.  添加一个`.travis.yml`将文件发送到您的git存储库. 


    language: node_js
    node_js:
      - 4
      - 6
    cache:
      directories:
        - node_modules
    script:
      - npm test
      - npm run build

1.  使用git push触发您的第一个构建. 
2.  [Customize your Travis CI Build](https://docs.travis-ci.com/user/customizing-the-build/)如果需要的话. 

### 在你自己的环境中

##### Windows (cmd.exe) 

```cmd
set CI=true&&npm test
```

```cmd
set CI=true&&npm run build
```

 (注意: 缺少空格是故意的. ) 

##### Linux,OS X (Bash) 

```bash
CI=true npm test
```

```bash
CI=true npm run build
```

测试命令将强制Jest运行一次测试而不是启动观察器. 

> 如果您发现自己经常在开发中这样做,请[file an issue](https://github.com/facebookincubator/create-react-app/issues/new)告诉我们您的用例,因为我们希望让观察者获得最佳体验,并愿意改变其工作方式以适应更多工作流程. 

build命令将检查linter警告,如果找到则告警失败. 

### 禁用jsdom

默认情况下`package.json`生成的项目如下所示: 

```js
  // ...
  "scripts": {
    // ...
    "test": "react-scripts test --env=jsdom"
  }
```

如果你知道你的测试都不依赖于[jsdom](https://github.com/tmpvar/jsdom),你可以安全地删除`--env=jsdom`,您的测试将运行得更快. <br>为了帮助您下定决心,以下是API列表**需要jsdom**: 

-   任何浏览器全局都喜欢`window`和`document`
-   [`ReactDOM.render()`](https://facebook.github.io/react/docs/top-level-api.html#reactdom.render)
-   [`TestUtils.renderIntoDocument()`](https://facebook.github.io/react/docs/test-utils.html#renderintodocument) ([a shortcut](https://github.com/facebook/react/blob/34761cf9a252964abfaab6faf74d473ad95d1f21/src/test/ReactTestUtils.js#L83-L91)对于上述) 
-   [`mount()`](http://airbnb.io/enzyme/docs/api/mount.html)在[Enzyme](http://airbnb.io/enzyme/index.html)

相反,**不需要jsdom**对于以下API: 

-   [`TestUtils.createRenderer()`](https://facebook.github.io/react/docs/test-utils.html#shallow-rendering) (浅渲染) 
-   [`shallow()`](http://airbnb.io/enzyme/docs/api/shallow.html)在[Enzyme](http://airbnb.io/enzyme/index.html)

最后,也不需要jsdom[snapshot testing](http://facebook.github.io/jest/blog/2016/07/27/jest-14.html). 从长远来看,这是我们有兴趣探索的方向,但快照测试是[not fully baked yet](https://github.com/facebookincubator/create-react-app/issues/372)所以我们还没有正式鼓励它的使用. 

### 实验快照测试

快照测试是Jest的一项新功能,可自动生成组件的文本快照并将其保存在磁盘上,因此,如果UI输出发生更改,则无需在组件输出上手动编写任何断言即可获得通知. 

此功能尚未实验[has major usage issues](https://github.com/facebookincubator/create-react-app/issues/372)所以我们只鼓励你使用它,如果你喜欢实验技术. 我们打算逐步改进它并最终将其作为测试React组件的默认解决方案,但这需要时间. [Read more about snapshot testing.](http://facebook.github.io/jest/blog/2016/07/27/jest-14.html)

### 编辑器集成

如果你使用[Visual Studio Code](https://code.visualstudio.com),有一个[Jest extension](https://github.com/orta/vscode-jest)它适用于创建React App开箱即用. 这在使用文本编辑器时提供了许多类似IDE的功能: 显示测试运行的状态,其中包含潜在的内联失败消息,自动启动和停止观察程序,以及提供一键式快照更新. 

![VS Code Jest Preview](https://cloud.githubusercontent.com/assets/49038/20795349/a032308a-b7c8-11e6-9b34-7eeac781003f.png)

## 隔离开发组件

通常,在应用程序中,您有许多UI组件,并且每个组件都有许多不同的状态. 例如,一个简单的按钮组件可能具有以下状态: 

-   带有文字标签. 
-   用表情符号. 
-   在禁用模式下. 

通常,如果没有运行示例应用程序或一些示例,很难看到这些状态. 

默认情况下,创建React App不包含任何工具,但您可以轻松添加[React Storybook](https://github.com/kadirahq/react-storybook)到你的项目. **它是第三方工具,可让您开发组件并独立于应用程序查看其所有状态**. 

![React Storybook Demo](http://i.imgur.com/7CIAWpB.gif)

您还可以将Storybook部署为静态应用程序. 这样,团队中的每个人都可以查看和查看UI组件的不同状态,而无需启动后端服务器或在应用中创建帐户. 

**以下是使用Storybook设置应用的方法: **

首先,全局安装以下npm包: 

```sh
npm install -g getstorybook
```

然后,在应用程序的目录中运行以下命令: 

```sh
getstorybook
```

之后,请按照屏幕上的说明进行操作. 

了解有关React Storybook的更多信息: 

-   截屏: [Getting Started with React Storybook](https://egghead.io/lessons/react-getting-started-with-react-storybook)
-   [GitHub Repo](https://github.com/kadirahq/react-storybook)
-   [Documentation](https://getstorybook.io/docs)
-   [Snapshot Testing](https://github.com/kadirahq/storyshots)与React故事书

## 制作渐进式Web应用程序

您可以将React应用转换为[Progressive Web App](https://developers.google.com/web/progressive-web-apps/)按照以下步骤操作[this repository](https://github.com/jeffposnick/create-react-pwa). 

## 部署

`npm run build`创造一个`build`具有应用程序生产版本的目录. 设置您最喜欢的HTTP服务器,以便为您的网站访问者提供服务`index.html`,以及对静态路径的请求`/static/js/main.<hash>.js`与内容一起提供`/static/js/main.<hash>.js`文件. 例如,Python包含一个可以提供静态文件的内置HTTP服务器: 

```sh
cd build
python -m SimpleHTTPServer 9000
```

如果你正在使用[Node](https://nodejs.org/)和[Express](http://expressjs.com/)作为服务器,它可能看起来像这样: 

```javascript
const express = require('express');
const path = require('path');
const app = express();

app.use(express.static('./build'));

app.get('/', function (req, res) {
  res.sendFile(path.join(__dirname, './build', 'index.html'));
});

app.listen(9000);
```

创建React App并不反对您选择的Web服务器. 任何静态文件服务器都可以. 该`build`具有静态资源的文件夹是Create React App生成的唯一输出. 

但是,如果使用客户端路由,这还不够. 如果您想支持这样的网址,请阅读下一部分`/todos/42`在您的单页应用中. 

### 使用客户端路由服务应用程序

如果您使用使用HTML5的路由器[`pushState` history API](https://developer.mozilla.org/en-US/docs/Web/API/History_API#Adding_and_modifying_history_entries)在引擎盖下 (例如,[React Router](https://github.com/ReactTraining/react-router)同`browserHistory`) ,许多静态文件服务器将失败. 例如,如果您使用React路由器的路由`/todos/42`,开发服务器将响应`localhost:3000/todos/42`正确的,但是如上所述的快速服务生产构建不会. 

这是因为当有一个新页面加载时`/todos/42`,服务器查找该文件`build/todos/42`并没有找到它. 需要配置服务器以响应请求`/todos/42`通过服务`index.html`. 例如,我们可以修改上面的Express示例来提供服务`index.html`对于任何未知路径: 

```diff
 app.use(express.static('./build'));

-app.get('/', function (req, res) {
+app.get('/*', function (req, res) {
   res.sendFile(path.join(__dirname, './build', 'index.html'));
 });
```

现在请求`/todos/42`将在开发和生产中正确处理. 

### 建立相对路径

默认情况下,Create React App会生成一个构建,假设您的应用程序托管在服务器根目录下. <br>要覆盖它,请指定`homepage`在你的`package.json`, 例如: 

```js
  "homepage": "http://mywebsite.com/relativepath",
```

这将使Create React App正确地推断出在生成的HTML文件中使用的根路径. 

### 火力地堡

如果尚未运行,请安装Firebase CLI`npm install -g firebase-tools`. 注册一个[Firebase account](https://console.firebase.google.com/)并创建一个新项目. 跑`firebase login`并使用之前创建的Firebase帐户登录. 

然后运行`firebase init`来自项目根目录的命令. 你需要选择**托管: 配置和部署Firebase托管站点**并选择您在上一步中创建的Firebase项目. 你需要同意`database.rules.json`被创造,选择`build`作为公共目录,也同意**配置为单页面应用程序**回复`y`. 

```sh
    === Project Setup

    First, let's associate this project directory with a Firebase project.
    You can create multiple project aliases by running firebase use --add,
    but for now we'll just set up a default project.

    ? What Firebase project do you want to associate as default? Example app (example-app-fd690)

    === Database Setup

    Firebase Realtime Database Rules allow you to define how your data should be
    structured and when your data can be read from and written to.

    ? What file should be used for Database Rules? database.rules.json
    ✔  Database Rules for example-app-fd690 have been downloaded to database.rules.json.
    Future modifications to database.rules.json will update Database Rules when you run
    firebase deploy.

    === Hosting Setup

    Your public directory is the folder (relative to your project directory) that
    will contain Hosting assets to uploaded with firebase deploy. If you
    have a build process for your assets, use your build's output directory.

    ? What do you want to use as your public directory? build
    ? Configure as a single-page app (rewrite all urls to /index.html)? Yes
    ✔  Wrote build/index.html

    i  Writing configuration info to firebase.json...
    i  Writing project information to .firebaserc...

    ✔  Firebase initialization complete!
```

现在,在您创建生成版本之后`npm run build`,你可以通过运行来部署它`firebase deploy`. 

```sh
    === Deploying to 'example-app-fd690'...

    i  deploying database, hosting
    ✔  database: rules ready to deploy.
    i  hosting: preparing build directory for upload...
    Uploading: [==============================          ] 75%✔  hosting: build folder uploaded successfully
    ✔  hosting: 8 files uploaded successfully
    i  starting release process (may take several minutes)...

    ✔  Deploy complete!

    Project Console: https://console.firebase.google.com/project/example-app-fd690/overview
    Hosting URL: https://example-app-fd690.firebaseapp.com
```

有关更多信息,请参阅[Add Firebase to your JavaScript Project](https://firebase.google.com/docs/web/setup). 

### GitHub页面

> 注意: 此功能适用于`react-scripts@0.2.0`更高. 

#### 第1步: 添加`homepage`至`package.json`

**以下步骤很重要!**<br>
**如果您跳过它,您的应用将无法正确部署. **

打开你的`package.json`并添加一个`homepage`领域: 

```js
  "homepage": "https://myusername.github.io/my-app",
```

创建React App使用`homepage`字段以确定生成的HTML文件中的根URL. 

#### 第2步: 安装`gh-pages`并添加`deploy`至`scripts`在`package.json`

现在,每当你跑步`npm run build`,您将看到一个备忘单,其中包含有关如何部署到GitHub页面的说明. 

要发布它<https://myusername.github.io/my-app>, 跑: 

```sh
npm install --save-dev gh-pages
```

在您的添加中添加以下脚本`package.json`: 

```js
  // ...
  "scripts": {
    // ...
    "deploy": "npm run build&&gh-pages -d build"
  }
```

 (注意: 缺少空格是故意的. ) 

#### 第3步: 通过运行部署站点`npm run deploy`

然后运行: 

```sh
npm run deploy
```

#### 第4步: 确保您的项目设置使用`gh-pages`

最后,确保**GitHub页面**您的GitHub项目设置中的选项设置为使用`gh-pages`科: 

<img src="http://i.imgur.com/HUjEr9l.png" width="500" alt="gh-pages branch setting">

#### 步骤5:  (可选) 配置域

您可以通过添加a来配置GitHub页面的自定义域`CNAME`归档给`public/`夹. 

#### 客户端路由的注意事项

GitHub Pages不支持使用HTML5的路由器`pushState`引擎盖下的历史API (例如,React Router使用`browserHistory`) . 这是因为当网址有新页面加载时`http://user.github.io/todomvc/todos/42`,哪里`/todos/42`是一个前端路由,GitHub页面服务器返回404,因为它什么都不知道`/todos/42`. 如果要将路由器添加到GitHub页面上托管的项目中,可以使用以下几种解决方案: 

-   您可以从使用HTML5历史记录API切换到使用哈希值进行路由. 如果您使用React Router,则可以切换到`hashHistory`为此效果,但URL将更长,更冗长 (例如,`http://user.github.io/todomvc/#/todos/42?_k=yknaj`) . [Read more](https://github.com/reactjs/react-router/blob/master/docs/guides/Histories.md#histories)关于React Router中的不同历史实现. 
-   或者,你可以使用技巧教GitHub页面通过重定向到你的处理404`index.html`具有特殊重定向参数的页面. 你需要添加一个`404.html`带有重定向代码的文件`build`部署项目之前的文件夹,您需要添加处理重定向参数的代码`index.html`. 您可以找到此技术的详细说明[in this guide](https://github.com/rafrex/spa-github-pages). 

### Heroku的

使用[Heroku Buildpack for Create React App](https://github.com/mars/create-react-app-buildpack). <br>你可以在中找到说明[Deploying React with Zero Configuration](https://blog.heroku.com/deploying-react-with-zero-configuration). 

#### 解决"找不到模块: 错误: 无法解析'文件'或'目录'"

有时`npm run build`在本地工作,但在通过Heroku部署期间失败,出现如下错误: 

    remote: Failed to create a production build. Reason:
    remote: Module not found: Error: Cannot resolve 'file' or 'directory'
    MyDirectory in /tmp/build_1234/src  

这意味着您需要确保您的文件或目录的字母大小写`import`匹配您在文件系统或GitHub上看到的那个. 

这很重要,因为Linux (Heroku使用的操作系统) 区分大小写. 所以`MyDirectory`和`mydirectory`是两个不同的目录,因此,即使项目本地建立,情况的差异打破了`import`关于Heroku遥控器的声明. 

### 系数

见[Modulus blog post](http://blog.modulus.io/deploying-react-apps-on-modulus)关于如何将您的反应应用程序部署到Modulus. 

## Netlify

**要手动部署到Netlify的CDN: **

```sh
npm install netlify-cli
netlify deploy
```

选择`build`作为部署的路径. 

**要设置持续交付: **

通过此设置,当您推送git或打开拉取请求时,Netlify将构建和部署: 

1.  [Start a new netlify project](https://app.netlify.com/signup)
2.  选择您的Git托管服务并选择您的存储库
3.  点击`Build your site`

**支持客户端路由: **

支持`pushState`,一定要创建一个`public/_redirects`具有以下重写规则的文件: 

    /*  /index.html  200

在构建项目时,Create React App将放置`public`文件夹内容到构建输出中. 

### 现在

看到[this example](https://github.com/xkawi/create-react-app-now)用于零配置单命令部署[now](https://zeit.co/now). 

### S3和CloudFront

看到这个[blog post](https://medium.com/@omgwtfmarc/deploying-create-react-app-to-s3-or-cloudfront-48dae4ce0af)关于如何将React应用程序部署到Amazon Web Services[S3](https://aws.amazon.com/s3)和[CloudFront](https://aws.amazon.com/cloudfront/). 

### 浪涌

如果尚未运行,请安装Surge CLI`npm install -g surge`. 跑过`surge`命令并登录或创建新帐户. 你只需要指定*建立*文件夹和您的自定义域,您就完成了. 

```sh
              email: email@domain.com
           password: ********
       project path: /path/to/project/build
               size: 7 files, 1.8 MB
             domain: create-react-app.surge.sh
             upload: [====================] 100%, eta: 0.0s
   propagate on CDN: [====================] 100%
               plan: Free
              users: email@domain.com
         IP Address: X.X.X.X

    Success! Project is published and running at create-react-app.surge.sh
```

请注意,为了支持使用HTML5的路由器`pushState`API,您可能想要重命名`index.html`在你的构建文件夹中`200.html`在部署到Surge之前. 这个[ensures that every URL falls back to that file](https://surge.sh/help/adding-a-200-page-for-client-side-routing). 

## 故障排除

### `npm test`挂在macOS Sierra上

如果你跑`npm test`并且打印后控制台卡住了`react-scripts test --env=jsdom`到控制台可能有问题[Watchman](https://facebook.github.io/watchman/)如上所述的安装[facebookincubator/create-react-app#713](https://github.com/facebookincubator/create-react-app/issues/713). 

我们建议删除`node_modules`在你的项目和运行中`npm install` (要么`yarn`如果你使用它) 首先. 如果它没有帮助,您可以尝试这些问题中提到的众多变通方法之一: 

-   [facebook/jest#1767](https://github.com/facebook/jest/issues/1767)
-   [facebook/watchman#358](https://github.com/facebook/watchman/issues/358)
-   [ember-cli/ember-cli#6259](https://github.com/ember-cli/ember-cli/issues/6259)

据报道,安装Watchman 4.7.0或更新版本修复了这个问题. 如果你使用[Homebrew](http://brew.sh/),您可以运行这些命令来更新它: 

    watchman shutdown-server
    brew update
    brew reinstall watchman

你可以找到[other installation methods](https://facebook.github.io/watchman/docs/install.html#build-install)在Watchman文档页面上. 

如果这仍然没有帮助,请尝试运行`launchctl unload -F ~/Library/LaunchAgents/com.github.facebook.watchman.plist`. 

还有报道说*卸载*守望者解决了这个问题. 因此,如果没有其他帮助,请将其从系统中删除,然后重试. 

### `npm run build`默默地失败了

据悉`npm run build`在没有交换空间的计算机上可能会失败,这在云环境中很常见. 如果[the symptoms are matching](https://github.com/facebookincubator/create-react-app/issues/1133#issuecomment-264612171),考虑为您正在构建的计算机添加一些交换空间,或在本地构建项目. 

### `npm run build`Heroku失败了

这可能是区分大小写的文件名的问题. 请参阅[this section](#resolving-module-not-found-error-cannot-resolve-file-or-directory). 

## 有什么遗失?

如果您有关于此页面上应该有更多"如何"食谱的想法,[let us know](https://github.com/facebookincubator/create-react-app/issues)要么[contribute some!](https://github.com/facebookincubator/create-react-app/edit/master/packages/react-scripts/template/README.md)
