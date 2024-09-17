好的！既然你已经掌握了 **HTML**、**CSS**、**JavaScript**、**Git**、**Node.js** 和 **npm** 的基础，我们现在就开始学习 **Vue.js 入门**。Vue.js 是一个流行的前端框架，结合 Vite 可以帮助你快速构建现代化的前端应用。

我们将按以下步骤进行：

1. **使用 Vite 创建 Vue 项目**
2. **了解项目结构**
3. **运行开发服务器**
4. **了解 Vue 的基本概念**
5. **创建和使用 Vue 组件**
6. **数据绑定与指令**
7. **响应式数据与计算属性**
8. **事件处理**
9. **练习与项目实战**

让我们一步步深入学习！

---

## 一、使用 Vite 创建 Vue 项目

### 1.1 什么是 Vite？

**Vite** 是一个由 Vue.js 的作者尤雨溪（Evan You）开发的前端构建工具，具有快速的冷启动和热模块替换（HMR）功能。它支持多种前端框架，包括 Vue.js、React 等。

### 1.2 使用 Vite 创建 Vue 项目

#### 步骤：

1. **全局安装 Vite（可选）**

   虽然 Vite 推荐使用 `npm create` 命令来创建项目，但你也可以全局安装 Vite。这里我们使用推荐的方式，不需要全局安装。

2. **创建 Vue 项目**

   打开终端，导航到你想要创建项目的目录，然后运行以下命令：

   ```bash
   npm create vite@latest my-vue-app -- --template vue
   ```

   **解释**：
   - `npm create vite@latest`：使用最新版本的 Vite 创建项目。
   - `my-vue-app`：项目名称，你可以根据需要修改。
   - `--template vue`：指定使用 Vue 模板。

3. **进入项目目录并安装依赖**

   ```bash
   cd my-vue-app
   npm install
   ```

4. **启动开发服务器**

   ```bash
   npm run dev
   ```

   **解释**：
   - `npm run dev`：启动 Vite 的开发服务器，默认地址为 `http://localhost:5173/`（端口可能会有所不同）。

#### 完整步骤总结：

```bash
# 使用 Vite 创建 Vue 项目
npm create vite@latest my-vue-app -- --template vue

# 进入项目目录
cd my-vue-app

# 安装项目依赖
npm install

# 启动开发服务器
npm run dev
```

### 1.3 验证项目是否成功创建

1. **浏览器访问**：

   打开浏览器，访问 `http://localhost:5173/`（或终端中提示的地址）。你应该能看到一个默认的 Vue.js 欢迎页面。

2. **项目结构**：

   打开你的代码编辑器（推荐使用 [Visual Studio Code](https://code.visualstudio.com/)），浏览项目目录结构。你会看到以下主要文件和文件夹：

   ```
   my-vue-app/
   ├── index.html
   ├── package.json
   ├── src/
   │   ├── assets/
   │   │   └── vue.svg
   │   ├── components/
   │   │   └── HelloWorld.vue
   │   ├── App.vue
   │   └── main.js
   ├── vite.config.js
   └── ...
   ```

---

## 二、了解项目结构

了解项目结构有助于你快速上手和定位代码。以下是主要文件和文件夹的介绍：

### 2.1 主要文件和文件夹

- **`index.html`**：

  项目的入口 HTML 文件。Vite 会自动注入脚本和样式。

- **`package.json`**：

  项目配置文件，记录了项目的依赖、脚本等信息。

- **`src/`**：

  存放源代码的目录。

  - **`assets/`**：

    存放静态资源，如图片、字体等。

  - **`components/`**：

    存放 Vue 组件的目录。默认包含一个 `HelloWorld.vue` 组件。

  - **`App.vue`**：

    根组件，是所有 Vue 组件的父组件。

  - **`main.js`**：

    项目的入口 JavaScript 文件，用于初始化 Vue 应用并挂载到 DOM。

- **`vite.config.js`**：

  Vite 的配置文件，用于自定义构建和开发服务器的行为。

### 2.2 关键文件解释

#### 2.2.1 `main.js`

```javascript
import { createApp } from 'vue'
import App from './App.vue'

createApp(App).mount('#app')
```

**解释**：
- **导入 Vue 的创建应用函数**。
- **导入根组件 `App.vue`**。
- **创建 Vue 应用并挂载到 `#app` 元素**。

#### 2.2.2 `App.vue`

```vue
<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/vue.svg">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  text-align: center;
}
</style>
```

**解释**：
- **模板部分**：定义了 HTML 结构，包含一个图片和 `HelloWorld` 组件。
- **脚本部分**：导入 `HelloWorld` 组件，并在组件选项中注册。
- **样式部分**：定义了 `#app` 元素的样式。

#### 2.2.3 `HelloWorld.vue`

```vue
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://vitejs.dev/guide/features.html" target="_blank" rel="noopener">Vite documentation</a>.
    </p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<style scoped>
h1 {
  color: #42b983;
}
</style>
```

**解释**：
- **模板部分**：显示传递的 `msg` 属性和一段介绍文本。
- **脚本部分**：定义了组件名称和接收的 `props`（属性）。
- **样式部分**：定义了局部样式（使用 `scoped` 关键字，仅作用于当前组件）。

---

## 三、运行开发服务器

### 3.1 启动开发服务器

确保你已经在项目目录下，并且安装了所有依赖。运行以下命令启动开发服务器：

```bash
npm run dev
```

### 3.2 了解开发服务器的功能

- **热模块替换（HMR）**：

  当你修改源代码时，开发服务器会自动刷新浏览器中的内容，而无需手动刷新。

- **错误提示**：

  如果代码中有错误，开发服务器会在终端或浏览器中显示详细的错误信息，帮助你快速定位和修复问题。

### 3.3 关闭开发服务器

在终端中按下 `Ctrl + C` 可以停止开发服务器。

---

## 四、了解 Vue 的基本概念

在深入编写 Vue 应用之前，了解一些 Vue 的基本概念非常重要。

### 4.1 什么是 Vue.js？

**Vue.js** 是一个用于构建用户界面的渐进式 JavaScript 框架。它的核心库专注于视图层，易于上手，并且能够与其它库或现有项目进行集成。

**主要特点**：

- **响应式数据绑定**：数据变化会自动更新到视图。
- **组件化开发**：将界面拆分为可复用的组件。
- **简洁的模板语法**：使用 HTML 模板语法，易于理解和编写。
- **强大的生态系统**：包括路由管理（Vue Router）、状态管理（Vuex/Pinia）等。

### 4.2 Vue 实例

Vue 应用由一个根实例（Root Instance）组成，该实例通过 `createApp` 创建并挂载到 DOM 元素。

#### 示例：

```javascript
import { createApp } from 'vue'
import App from './App.vue'

createApp(App).mount('#app')
```

**解释**：
- **`createApp`**：创建一个新的 Vue 应用实例。
- **`.mount('#app')`**：将 Vue 应用挂载到具有 `id="app"` 的 DOM 元素上。

### 4.3 组件

组件是 Vue 应用的基本构建块。每个组件都有自己的模板、逻辑和样式，可以相互嵌套和复用。

#### 示例：

```vue
<template>
  <div>
    <h1>{{ title }}</h1>
    <p>{{ description }}</p>
  </div>
</template>

<script>
export default {
  name: 'MyComponent',
  props: {
    title: String,
    description: String
  }
}
</script>

<style scoped>
h1 {
  color: blue;
}
</style>
```

**解释**：
- **模板部分**：定义了组件的 HTML 结构，使用了 `{{ title }}` 和 `{{ description }}` 进行数据绑定。
- **脚本部分**：定义了组件的名称和接收的 `props`（属性）。
- **样式部分**：定义了局部样式，仅作用于当前组件。

---

## 五、创建和使用 Vue 组件

### 5.1 创建一个新的 Vue 组件

让我们创建一个新的 Vue 组件，名为 `Greeting.vue`，用于显示问候消息。

#### 步骤：

1. **在 `src/components/` 目录下创建 `Greeting.vue` 文件**。

2. **编写 `Greeting.vue` 内容**：

   ```vue
   <template>
     <div class="greeting">
       <h2>{{ greetingMessage }}</h2>
       <button @click="changeGreeting">更改问候语</button>
     </div>
   </template>

   <script>
   export default {
     name: 'Greeting',
     data() {
       return {
         greetingMessage: '你好，欢迎使用 Vue.js！'
       }
     },
     methods: {
       changeGreeting() {
         this.greetingMessage = '感谢点击按钮！';
       }
     }
   }
   </script>

   <style scoped>
   .greeting {
     border: 1px solid #ccc;
     padding: 20px;
     margin: 20px 0;
     text-align: center;
   }

   button {
     padding: 10px 20px;
     background-color: #42b983;
     color: white;
     border: none;
     cursor: pointer;
     border-radius: 4px;
   }

   button:hover {
     background-color: #369870;
   }
   </style>
   ```

   **解释**：
   - **模板部分**：包含一个标题和一个按钮。按钮绑定了 `click` 事件，触发 `changeGreeting` 方法。
   - **脚本部分**：
     - **`data`**：定义了一个响应式的数据属性 `greetingMessage`。
     - **`methods`**：定义了一个方法 `changeGreeting`，用于更改 `greetingMessage` 的值。
   - **样式部分**：定义了组件的局部样式。

### 5.2 使用新创建的组件

接下来，我们将在 `App.vue` 中使用刚刚创建的 `Greeting` 组件。

#### 步骤：

1. **打开 `App.vue`**。

2. **导入 `Greeting` 组件并注册**：

   ```vue
   <script>
   import HelloWorld from './components/HelloWorld.vue'
   import Greeting from './components/Greeting.vue'

   export default {
     name: 'App',
     components: {
       HelloWorld,
       Greeting
     }
   }
   </script>
   ```

3. **在模板中使用 `Greeting` 组件**：

   ```vue
   <template>
     <div id="app">
       <img alt="Vue logo" src="./assets/vue.svg">
       <HelloWorld msg="Welcome to Your Vue.js App"/>
       <Greeting />
     </div>
   </template>
   ```

4. **保存文件**，查看浏览器中的变化。

   你应该会看到新的 `Greeting` 组件显示的问候消息和按钮。点击按钮后，问候语会发生变化。

---

## 六、数据绑定与指令

### 6.1 数据绑定

Vue.js 提供了强大的数据绑定功能，使得数据和视图能够自动同步。

#### 6.1.1 插值绑定（Interpolation）

使用双大括号 `{{ }}` 将数据绑定到模板中。

#### 示例：

```vue
<template>
  <div>
    <h1>{{ message }}</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: 'Hello, Vue!'
    }
  }
}
</script>
```

**解释**：
- **`{{ message }}`**：在模板中显示 `data` 中定义的 `message`。
- **响应式**：如果 `message` 的值发生变化，视图会自动更新。

#### 6.1.2 属性绑定（v-bind）

使用 `v-bind` 指令将数据绑定到元素的属性上。简写为 `:`。

#### 示例：

```vue
<template>
  <div>
    <img :src="imageSrc" alt="动态图片">
  </div>
</template>

<script>
export default {
  data() {
    return {
      imageSrc: './assets/vue.svg'
    }
  }
}
</script>
```

**解释**：
- **`:src="imageSrc"`**：将 `imageSrc` 绑定到 `img` 元素的 `src` 属性上。
- **动态更新**：如果 `imageSrc` 的值改变，图片会自动更新。

### 6.2 指令

Vue.js 提供了多种指令，用于在模板中绑定数据、条件渲染、列表渲染等。

#### 6.2.1 条件渲染（v-if, v-else-if, v-else）

根据条件决定是否渲染某个元素。

#### 示例：

```vue
<template>
  <div>
    <p v-if="isLoggedIn">欢迎回来，用户！</p>
    <p v-else>请登录。</p>
    <button @click="toggleLogin">切换登录状态</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isLoggedIn: false
    }
  },
  methods: {
    toggleLogin() {
      this.isLoggedIn = !this.isLoggedIn
    }
  }
}
</script>
```

**解释**：
- **`v-if="isLoggedIn"`**：如果 `isLoggedIn` 为 `true`，显示第一段文本。
- **`v-else`**：否则，显示第二段文本。
- **按钮**：点击按钮会切换 `isLoggedIn` 的值，从而切换显示的文本。

#### 6.2.2 列表渲染（v-for）

基于一个数组渲染一组元素。

#### 示例：

```vue
<template>
  <div>
    <ul>
      <li v-for="(item, index) in items" :key="index">{{ item }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: ['苹果', '香蕉', '橘子']
    }
  }
}
</script>
```

**解释**：
- **`v-for="(item, index) in items"`**：遍历 `items` 数组，生成每个 `item` 对应的 `li` 元素。
- **`:key="index"`**：为每个列表项提供一个唯一的 `key`，有助于 Vue 高效地更新 DOM。

#### 6.2.3 事件绑定（v-on）

使用 `v-on` 指令绑定事件，简写为 `@`。

#### 示例：

```vue
<template>
  <div>
    <button @click="handleClick">点击我</button>
  </div>
</template>

<script>
export default {
  methods: {
    handleClick() {
      alert('按钮被点击了！')
    }
  }
}
</script>
```

**解释**：
- **`@click="handleClick"`**：当按钮被点击时，触发 `handleClick` 方法。

---

## 七、响应式数据与计算属性

### 7.1 响应式数据

Vue.js 的响应式系统能够自动跟踪数据的变化，并在数据变化时更新视图。

#### 示例：

```vue
<template>
  <div>
    <p>当前计数：{{ count }}</p>
    <button @click="increment">增加</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0
    }
  },
  methods: {
    increment() {
      this.count += 1
    }
  }
}
</script>
```

**解释**：
- **`count`**：定义了一个响应式数据属性。
- **`increment` 方法**：每次点击按钮，`count` 增加 1，视图会自动更新显示新的值。

### 7.2 计算属性（Computed Properties）

计算属性用于基于已有数据计算出新的值，且会根据依赖自动更新。

#### 示例：

```vue
<template>
  <div>
    <p>原始价格：{{ price }}</p>
    <p>折扣后价格：{{ discountedPrice }}</p>
    <button @click="applyDiscount">应用折扣</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      price: 100,
      discount: 0.1
    }
  },
  computed: {
    discountedPrice() {
      return this.price - this.price * this.discount
    }
  },
  methods: {
    applyDiscount() {
      this.discount = 0.2
    }
  }
}
</script>
```

**解释**：
- **`price` 和 `discount`**：定义了两个响应式数据属性。
- **`discountedPrice`**：计算属性，根据 `price` 和 `discount` 计算出折扣后的价格。
- **`applyDiscount` 方法**：修改 `discount` 的值，计算属性 `discountedPrice` 会自动更新。

### 7.3 侦听器（Watchers）

侦听器用于观察 Vue 实例上的数据变动，并在数据变化时执行一些操作。

#### 示例：

```vue
<template>
  <div>
    <input v-model="searchQuery" placeholder="搜索...">
    <p>搜索内容：{{ searchQuery }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: ''
    }
  },
  watch: {
    searchQuery(newQuery, oldQuery) {
      console.log(`搜索内容从 "${oldQuery}" 变更为 "${newQuery}"`)
      // 可以在这里执行 API 调用或其他操作
    }
  }
}
</script>
```

**解释**：
- **`searchQuery`**：定义了一个响应式数据属性，并通过 `v-model` 双向绑定到输入框。
- **`watch`**：侦听 `searchQuery` 的变化，当其值发生变化时，打印日志。

---

## 八、事件处理

### 8.1 绑定事件

Vue.js 通过 `v-on` 指令（简写为 `@`）绑定事件处理器。

#### 示例：

```vue
<template>
  <div>
    <button @click="handleClick">点击我</button>
    <button @mouseover="handleMouseOver">鼠标悬停</button>
  </div>
</template>

<script>
export default {
  methods: {
    handleClick() {
      alert('按钮被点击了！')
    },
    handleMouseOver() {
      console.log('鼠标悬停在按钮上！')
    }
  }
}
</script>
```

**解释**：
- **`@click="handleClick"`**：绑定点击事件，触发 `handleClick` 方法。
- **`@mouseover="handleMouseOver"`**：绑定鼠标悬停事件，触发 `handleMouseOver` 方法。

### 8.2 事件修饰符

Vue.js 提供了一些事件修饰符，帮助你更简洁地处理事件。

#### 示例：

```vue
<template>
  <div>
    <!-- 阻止默认行为 -->
    <a href="https://www.example.com" @click.prevent="handleClick">点击链接</a>

    <!-- 阻止事件冒泡 -->
    <button @click.stop="handleClick">点击按钮</button>

    <!-- 使用 once 修饰符 -->
    <button @click.once="handleOnce">只触发一次</button>
  </div>
</template>

<script>
export default {
  methods: {
    handleClick() {
      alert('事件被触发！')
    },
    handleOnce() {
      alert('只触发一次！')
    }
  }
}
</script>
```

**解释**：
- **`.prevent`**：阻止事件的默认行为。
- **`.stop`**：阻止事件冒泡。
- **`.once`**：事件只触发一次。

---

## 九、练习与互动

通过以下练习，将巩固你对 Vue.js 基本概念的理解和应用。

### 练习 1：扩展 `Greeting` 组件

**目标**：让 `Greeting` 组件能够输入用户的名字，并显示个性化的问候语。

#### 步骤：

1. **打开 `Greeting.vue`**。

2. **修改模板**：

   ```vue
   <template>
     <div class="greeting">
       <h2>{{ greetingMessage }}</h2>
       <input v-model="name" placeholder="输入你的名字">
       <button @click="changeGreeting">更改问候语</button>
     </div>
   </template>
   ```

   **解释**：
   - 添加了一个输入框，使用 `v-model` 双向绑定 `name`。

3. **修改脚本**：

   ```javascript
   export default {
     name: 'Greeting',
     data() {
       return {
         greetingMessage: '你好，欢迎使用 Vue.js！',
         name: ''
       }
     },
     methods: {
       changeGreeting() {
         if (this.name.trim() !== '') {
           this.greetingMessage = `你好，${this.name}！感谢点击按钮！`
         } else {
           this.greetingMessage = '你好，感谢点击按钮！'
         }
       }
     }
   }
   ```

   **解释**：
   - 添加了一个响应式数据属性 `name`。
   - 在 `changeGreeting` 方法中，根据 `name` 的值修改 `greetingMessage`。

4. **修改样式（可选）**：

   ```css
   input {
     padding: 8px;
     margin-top: 10px;
     border: 1px solid #ccc;
     border-radius: 4px;
   }

   button {
     margin-top: 10px;
   }
   ```

5. **保存文件**，查看浏览器中的变化。

   你应该能看到一个输入框。输入你的名字，点击按钮后，问候语会变成“你好，[你的名字]！感谢点击按钮！”

### 练习 2：创建一个计数器组件

**目标**：创建一个新的组件 `Counter.vue`，实现增加和减少计数的功能。

#### 步骤：

1. **在 `src/components/` 目录下创建 `Counter.vue` 文件**。

2. **编写 `Counter.vue` 内容**：

   ```vue
   <template>
     <div class="counter">
       <h3>计数器</h3>
       <p>当前计数：{{ count }}</p>
       <button @click="increment">增加</button>
       <button @click="decrement">减少</button>
     </div>
   </template>

   <script>
   export default {
     name: 'Counter',
     data() {
       return {
         count: 0
       }
     },
     methods: {
       increment() {
         this.count += 1
       },
       decrement() {
         this.count -= 1
       }
     }
   }
   </script>

   <style scoped>
   .counter {
     border: 1px solid #ccc;
     padding: 20px;
     margin: 20px 0;
     text-align: center;
   }

   button {
     padding: 5px 10px;
     margin: 5px;
     border: none;
     background-color: #42b983;
     color: white;
     cursor: pointer;
     border-radius: 4px;
   }

   button:hover {
     background-color: #369870;
   }
   </style>
   ```

   **解释**：
   - **`count`**：定义了一个响应式数据属性，用于存储计数值。
   - **`increment` 和 `decrement` 方法**：分别用于增加和减少 `count` 的值。
   - **模板部分**：显示计数值和两个按钮，绑定点击事件。

3. **在 `App.vue` 中使用 `Counter` 组件**：

   ```vue
   <template>
     <div id="app">
       <img alt="Vue logo" src="./assets/vue.svg">
       <HelloWorld msg="Welcome to Your Vue.js App"/>
       <Greeting />
       <Counter />
     </div>
   </template>

   <script>
   import HelloWorld from './components/HelloWorld.vue'
   import Greeting from './components/Greeting.vue'
   import Counter from './components/Counter.vue'

   export default {
     name: 'App',
     components: {
       HelloWorld,
       Greeting,
       Counter
     }
   }
   </script>
   ```

4. **保存文件**，查看浏览器中的变化。

   你应该能看到新的 `Counter` 组件，显示当前计数值和增加、减少按钮。点击按钮，计数值会相应变化。

### 练习 3：使用计算属性实现双倍计数

**目标**：在 `Counter.vue` 中添加一个计算属性，显示计数值的双倍。

#### 步骤：

1. **打开 `Counter.vue`**。

2. **修改模板**：

   ```vue
   <template>
     <div class="counter">
       <h3>计数器</h3>
       <p>当前计数：{{ count }}</p>
       <p>双倍计数：{{ doubleCount }}</p>
       <button @click="increment">增加</button>
       <button @click="decrement">减少</button>
     </div>
   </template>
   ```

3. **修改脚本**：

   ```javascript
   export default {
     name: 'Counter',
     data() {
       return {
         count: 0
       }
     },
     computed: {
       doubleCount() {
         return this.count * 2
       }
     },
     methods: {
       increment() {
         this.count += 1
       },
       decrement() {
         this.count -= 1
       }
     }
   }
   ```

   **解释**：
   - **`doubleCount`**：计算属性，根据 `count` 的值计算出双倍的计数。

4. **保存文件**，查看浏览器中的变化。

   你应该能看到“双倍计数”显示为当前计数的两倍，并且随着计数值的变化自动更新。

---

## 十、总结与下一步

### 10.1 总结

在本节中，你学习了：

- 使用 Vite 创建 Vue 项目
- 了解项目结构
- 运行开发服务器
- Vue.js 的基本概念
- 创建和使用 Vue 组件
- 数据绑定与指令
- 响应式数据与计算属性
- 事件处理

通过这些学习和练习，你已经能够构建基本的 Vue.js 应用，并理解 Vue 的核心机制。

### 10.2 下一步：学习 Vue.js 进阶主题

接下来，我们将深入学习 **Vue.js 的进阶主题**，包括：

1. **路由管理（Vue Router）**
2. **状态管理（Vuex 或 Pinia）**
3. **与后端 API 交互（使用 Axios）**
4. **组件库的使用（如 Element Plus）**
5. **综合项目实战**

你可以根据自己的学习节奏和需求，选择逐步深入这些主题。

### 10.3 准备开始 Vue Router

如果你准备好了，我们将继续学习 **Vue Router**，它是 Vue.js 的官方路由管理库，帮助你构建单页应用（SPA），实现页面导航和路由控制。

请告诉我你是否准备好了，或者如果有任何问题或需要复习的部分，请随时告知！

祝学习愉快！