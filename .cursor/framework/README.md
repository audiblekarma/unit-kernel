# Unit Kernel

移植できる操作核です。when が一致した Feature だけ開きます。

## 置き場

```
.cursor/framework/     核・階層・地図・台帳・成長・目的
.cursor/rules/         各 Feature の spec
```

## 読む順

1. `HIERARCHY.txt` — 階層の本文
2. `map.json` — 照合用の索引（安い）
3. `KERNEL.md` — 核の定義
4. `PORT.md` — 他のシステムへ移す手順
5. `purpose.json` — この場の目的。移植時は差し替え
6. `FEATURES.txt` — 機能の説明
7. `GROWTH.txt` — 単位が少しずつどう育ったかの写像
8. `growth/` — 成長の索引と過程。`portable: true` だけ持っていく
9. `ledger/` — 事実・実験・成否。`portable: true` だけ持っていく

## 単位

Dispatch: Feature Registry、Unit Map  
Kernel: Unit Kernel  
Record: Field Ledger、Growth Map  
Purpose: Purpose Pack  
Protocol: Settle Prompt  
Mark: Voice Mark、Read Ease  

`when` が一致した spec だけ開きます。矛盾は `map.json` の `contradictions` です。
