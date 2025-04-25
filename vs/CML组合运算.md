

# CML组合运算

在标记工作的协议场景下，CML字符串的可运算特征，可以支持自由拆分—>还原。

## 语义运算规则

两个CML字符串组合，代表的是语义上下文的组合。

由于关系分割符`空格`的语义优先级最低，对明文格式的两个CML字符串使用空格自然拼接成一个新的CML字符串，不丢失其原本分别包含的语义，也不破坏原本的语义结构。
$$
plaintext(A)+space+plaintext(B) = plaintext(A+space+B)
$$



## 示例

假如需要对某个知识进行上下文标记，由A、B两人借助不同的工具独立负责，最终C负责最终的组合。

#### 明文标记

如果ABC都采用明文编写、传输、存储。

A输出第一个CML字符串

```markdown
`token1`.`token2`@`token3`+`token4`
```

B写下了第二个CML字符串

```markdown
`token5`:`token6`
```

那么，C拿到两份后，使用空格组合，就可以完美的还原成完全符合语义结构规范的新的CML字符串

```markdown
`token1`.`token2`@`token3`+`token4` `token5`:`token6`
```

#### base58编码标记

如果上述标记明文，ABC都采用base58编码、传输、存储。

A经过两轮base58编码，输出第一个CML字符串

```text
DDnjTutfdHQhhUhM9e18dLRtK9dkPHeXdgrmyHYQXPJHk5qr
```

同理，B输出第二个CML字符串

```text
29kfEQEV7nym45bezqMRVHqr
```

C拿到两份标记之后，直接拼接是不对的，但也不需要完全解码。只需要先将AB的输出，分别进行一轮base58解码还原出整体结构，再进行空格拼接。

```text
（整体解码A）zyvFCwFy zyvFCwFz:zyvFCwG1
（整体解码B）zyvFCwFz:zyvFCwG1
（空格拼接）zyvFCwFv.zyvFCwFw@zyvFCwFx+zyvFCwFy zyvFCwFz:zyvFCwG1
```

最终，重新进行base58整体编码，即可用于最终的传输、存储。

```text
3EkzyE8r5SqnU6KSbLS98LVLJxFoNvskzaazkuEEryWminqaGwJz13YoatvfoRWoDyrofwUCQ
```

#### 混合标记

如果AB输出不同格式，C统一使用编码格式存储。

A输出第一个CML字符串

```markdown
`token1`.`token2`@`token3`+`token4`
```

B整体编码输出第二个CML字符串

```text
29kfEQEV7nym45bezqMRVHqr
```

C拿到两份标记之后。只需要先对A进行第一次token级的base58编码，同时对B进行一轮整体base58解码，再进行空格拼接。

```text
zyvFCwFy zyvFCwFz:zyvFCwG1
zyvFCwFz:zyvFCwG1
zyvFCwFv.zyvFCwFw@zyvFCwFx+zyvFCwFy zyvFCwFz:zyvFCwG1
```

最终，对拼接结果重新进行base58编码，即可用于最终的传输、存储。