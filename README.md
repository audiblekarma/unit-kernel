# Unit Kernel

移植できる操作核です。when が一致した Feature だけ開きます。

## 置き場

```
.cursor/framework/   核・階層・地図・台帳・成長・目的
.cursor/rules/       各 Feature の spec
```

## 使い方

1. このツリーを、使うプロジェクトへコピーします。
2. `.cursor/framework/purpose.json` を、その場の目的に差し替えます。
3. その場のクリック手順が要るときは、Protocol の単位を足します。
4. `portable` が true の記録と成長だけ持っていきます。

詳細は `.cursor/framework/PORT.md` です。階層は `.cursor/framework/HIERARCHY.txt` です。
