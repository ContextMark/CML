一般来说，[JSON-LD 文档](https://www.w3.org/TR/json-ld11/#dfn-json-ld-document)描述的数据模型是一个带标签的有向[图](https://www.w3.org/TR/rdf11-concepts/#dfn-rdf-graph)。 该图包含由定向圆弧连接的[节点](https://www.w3.org/TR/rdf11-concepts/#dfn-node)。 节点可以是具有[属性](https://www.w3.org/TR/rdf11-concepts/#dfn-property)[的资源](https://www.w3.org/TR/rdf11-concepts/#dfn-resource)，也可以是这些属性的数据值，包括[字符串](https://infra.spec.whatwg.org/#javascript-string)、[数字](https://tc39.es/ecma262/#sec-terms-and-definitions-number-value)、[键入的值](https://www.w3.org/TR/json-ld11/#dfn-typed-value)（如日期和时间）和 [IRI](https://tools.ietf.org/html/rfc3987#section-2)。

在有向图中，节点是[资源](https://www.w3.org/TR/rdf11-concepts/#dfn-resource)，并且可能 *未命名*，即未由 [IRI](https://tools.ietf.org/html/rfc3987#section-2) 识别; 这些节点称为[空白节点](https://www.w3.org/TR/rdf11-concepts/#dfn-blank-node)， 并且可以使用[空白节点标识符](https://www.w3.org/TR/rdf11-concepts/#dfn-blank-node-identifier)进行标识。 可能需要这些标识符来表示完全连接的图形 使用树结构（如 JSON），但其他方面没有 内在意义。 文本值（例如[字符串](https://infra.spec.whatwg.org/#javascript-string)和[数字](https://tc39.es/ecma262/#sec-terms-and-definitions-number-value)）也被视为[资源](https://www.w3.org/TR/rdf11-concepts/#dfn-resource)。 JSON-LD 区分[了 node 对象](https://www.w3.org/TR/json-ld11/#dfn-node-object)和 [value 对象](https://www.w3.org/TR/json-ld11/#dfn-value-object)，以区分不同的 类型的[资源](https://www.w3.org/TR/rdf11-concepts/#dfn-resource)。

这个简单的数据模型令人难以置信 灵活而强大，能够对几乎任何类型的 数据。有关数据模型的更深入说明，请参阅 第 [8 节。 数据模型](https://www.w3.org/TR/json-ld11/#data-model)。





> **JSON-LD 是一种符合 JSON 格式的数据结构，用来表达语义信息（Linked Data）。**

换句话说：

| 名称    | 本质                                                         |
| ------- | ------------------------------------------------------------ |
| JSON    | 一种轻量级的数据交换格式（纯粹的数据结构）                   |
| JSON-LD | 基于 JSON 的一种语义网格式，用来表达**关联数据**（Linked Data） |

也就是说：**JSON-LD 是 JSON 的一个“语义增强版”。**

------

### 🤔 那什么是 Linked Data？

Linked Data 的核心思想是：

> 用统一的方式描述数据和它之间的关系，并在网络上互相关联起来。

比如描述“张三喜欢篮球”，不仅仅写死字面量，而是说：

```json
{
  "@context": "http://schema.org",
  "@type": "Person",
  "name": "张三",
  "likes": {
    "@type": "Sport",
    "name": "篮球"
  }
}
```

注意这些：

- `@context` 告诉你使用哪个语义定义（schema.org 是一个常用的标准）
- `@type` 明确指出这个对象是一个人、一个运动
- 这是 JSON，但加入了语义信息！

------

### 🧠 简单类比帮助你理解：

| 比喻   | JSON     | JSON-LD                                  |
| ------ | -------- | ---------------------------------------- |
| 文章   | 普通文字 | 带标签的语义标注（如 Word 样式）         |
| 数据   | 值 + 键  | 值 + 键 + 意图、含义                     |
| 字符串 | "apple"  | "apple" 是一个水果，编号是什么，链接在哪 |

------

### 📦 JSON-LD 常见用途：

- 在网页中嵌入结构化数据，帮助搜索引擎理解页面内容（SEO）
- 在语义网、知识图谱中作为数据交换格式
- 被 [schema.org](https://schema.org/) 官方支持
- Google 搜索、Google 知识图谱、Facebook 等都用 JSON-LD

------

### ✅ 所以总结一下：

- JSON 是数据的容器，通用格式
- JSON-LD 是语义增强的 JSON，用于表达“谁是什么”“与谁相关联”
- 它们**语法兼容**，但**语义目标不同**