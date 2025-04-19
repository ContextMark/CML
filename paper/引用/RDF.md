*RDF is a standard model for data interchange on the Web*

RDF是Web上数据交换的标准模型



[RDF - Semantic Web Standards](https://www.w3.org/RDF/)

标记，语义网络标准

RDF Schema 为 RDF 数据提供了数据建模词汇表。 它由几个配套文件补充，这些文档 描述 RDF 的基本概念和抽象语法 [[RDF11-CONCEPTS\]](https://www.w3.org/TR/rdf-schema/#bib-RDF11-CONCEPTS)、RDF [[RDF11-MT](https://www.w3.org/TR/rdf-schema/#bib-RDF11-MT)] 的形式语义，以及 RDF 的各种具体语法，例如 Turtle [[TURTLE](https://www.w3.org/TR/rdf-schema/#bib-TURTLE)]、 TriG、[[TRIG](https://www.w3.org/TR/rdf-schema/#bib-TRIG)] 和 JSON-LD [[JSON-LD](https://www.w3.org/TR/rdf-schema/#bib-JSON-LD)]。RDF 引物 [[RDF11-PRIMER\]](https://www.w3.org/TR/rdf-schema/#bib-RDF11-PRIMER) 提供了一个非正式的介绍和 本文档中指定概念的使用示例。

本文档旨在提供 RDF 的明确规范 Schema 给那些找到正式语义的人 规格 [[RDF11-MT](https://www.w3.org/TR/rdf-schema/#bib-RDF11-MT)] 艰巨。因此，本文档复制了 RDF 语义规范。如果 this 之间存在分歧 公文 以及 RDF 语义规范、RDF 语义规范 应该 被认为是正确的。

RDF Schema 是一种[语义 RDF 的扩展](https://www.w3.org/TR/rdf11-mt/#semantic-extensions-and-entailment-regimes)。它提供了描述以下组的机制 related resources 以及这些资源之间的关系。RDF Schema 是用 RDF 编写的 使用本文档中描述的术语。这些资源用于 确定其他资源的特征，例如属性的[域](https://www.w3.org/TR/rdf-schema/#ch_domain)和[范围](https://www.w3.org/TR/rdf-schema/#ch_range)。

RDF Schema 类和属性系统类似于 面向对象的编程语言系统，例如 Java。RDF Schema 与许多此类系统的不同之处在于，它不是定义 类 其实例可能具有的属性的术语、RDF 架构 根据 资源。这是本规范中描述的 [domain](https://www.w3.org/TR/rdf-schema/#ch_domain) 和 [range](https://www.w3.org/TR/rdf-schema/#ch_range) 机制的作用。例如，我们可以 定义属性以具有 domain of 和 range of ，而经典的面向对象系统可能 通常使用名为 type 的属性定义类。使用 RDF 方法，其他人随后很容易定义额外的 属性域为 eg： 或范围为 .这无需重新定义即可完成 的原始描述 这些类。RDF 以属性为中心的方法的一个好处是 它 允许任何人扩展现有资源的描述，即 这 Web 的架构原则 [[BERNERS-LEE98](https://www.w3.org/TR/rdf-schema/#bib-BERNERS-LEE98)]



**RDF** 全称是 **Resource Description Framework**，是 **W3C（万维网联盟）** 提出的一个用于**表示资源及其关系**的**数据模型（不是标记模型）**。

------

### 📌 它的核心作用是：

> **以统一的方式描述信息之间的语义关系**，常用于构建知识图谱、语义网、元数据等。

------

### 🧱 RDF 的基本结构是：

它是一种**三元组（Triple）模型**：

```text
(subject, predicate, object)
```

举个例子：

```text
(张三, 喜欢, 篮球)
```

或者用 RDF 的标准表示方法（Turtle）写就是：

```turtle
<http://example.org/张三> <http://example.org/喜欢> <http://example.org/篮球> .
```

这代表一个语义事实：“张三喜欢篮球”。

------

### 📘 那 RDF 是不是标记模型？

不是。虽然它**可以用 XML 格式来表示**（比如 RDF/XML），但本质上 RDF 是一种**数据模型**，而不是一种“标记语言”或“标记模型”。

你可以理解成：

| 概念                             | 是不是                                 |
| -------------------------------- | -------------------------------------- |
| RDF 是一种标记语言               | ❌ 否                                   |
| RDF 可以用标记语言（如 XML）表示 | ✅ 是                                   |
| RDF 是一种语义模型/数据结构      | ✅ 是                                   |
| RDF 是一种架构/规范              | ✅ 是                                   |
| RDF 用于定义语法规则             | ❌ 否（但它可以作为语法规则的数据基础） |

------

### 🤔 那它能不能用于设计标记格式或变成语言的语法？

- 它**本身不是用来设计编程语言语法**的东西，但……
- 它**可以描述语言元素之间的语义关系**（比如你设计一种 DSL，要表达哪些关键词、命令之间有什么语义联系，这时候 RDF 可以出场）

所以说：

> **RDF 不是设计语言语法的工具，但是描述语言含义的利器。**

