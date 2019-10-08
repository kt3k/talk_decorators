class: middle, center

# Proposal Decorators

---
class: center,middle
# 文法

---
class: middle
メソッドデコレータ

```
class Class {
  @hogehoge
  method() {
    // めそっど定義
  }
}
```
---
class: middle
クラスデコレータ

```
@fugafuga
class Class {
  method() {
    // メソッド定義
  }
}
```
---
class: middle
フィールドデコレータ

```
class Class {
  @hogehoge
  field = 1
}
```
---
class: middle
プライベートも可能

```
class Class {
  @hoge
  #field = 1

  @huga
  #method () {
    // メソッド定義
  }
}
```

---
# その他
- static method / field はデコレート不可 (たしか)
- function, function parameter, 変数などの decorator は案としてはある
- => follow-on proposals というものがいろいろあって, そちらで個別で検討されている
  - 例. iddan/proposal-function-expression-decorators (stage 1)

---
# 歴史

- 2014-2015 素朴デコレータ
- 2016-2019 descriptor-based decorator
- 2019 static decorator

---
# 2014-2015 素朴デコレータ
- typescript の "experimental" decorator, babel の "legacy" decorator として実装されているもの
- 今みんなが使ってるのはコレ
- babel 5 なんかではデフォルトで入ってた. 割と普通にこれが入ると思われている節があった.

クラスの
