class: middle, center

# Proposal Decorators

Stage 2

---
class: center,middle
# 文法 (使い方)

---
class: middle
メソッドデコレータ

```js
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

```js
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

```js
class Class {
  @hogehoge
  field = 1
}
```
---
class: middle
プライベートも可能

```js
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
# その他 補足
- static method / field はデコレート不可 (たしか)
- function, function parameter, 変数などの decorator は案としてはある
- => follow-on proposals というものがいろいろあって, そちらで個別で検討されている
  - 例. iddan/proposal-function-expression-decorators (stage 1)
---
class: middle
- 使う側の仕様はほぼ確定してる
- decorators を作る/実装する側の仕様がなかなか固まらないという問題がある
---
class: middle, center
# 歴史の話

proposal decorators は歴史が長い!!

---
# 歴史

- 2014-2015 素朴デコレータ
- 2016-2019 descriptor-based decorator
- 2019 static decorator

---
# 2014-2015 素朴デコレータ
- Champion: Yehuda Katz
- typescript の "experimental" decorator, babel の "legacy" decorator として実装されているもの
- 今みんなが使ってるのはコレ (mobx, angular)
- babel 5 なんかではデフォルトで入ってた. 割と普通にこれが入ると思われていた節があった.

=> class properties proposal が進捗し, class 内要素の評価順に関する議論の過程で reject された

---
# 2016-2019<br/> descriptor-based デコレータ

- Champion: @littledan
- デコレータの descriptor というものを精密に定義することで, update されたクラスを"正しく"デコレート出来るようになった
- babel 7.1 で plugin-proposal-decorator として transpiler が実装された
---
# 2016-2019<br/> descriptor-based デコレータ
- descriptor が複雑になりすぎた => 理解が困難
- 仕様を精密化しすぎたせいで transpile されたコードが巨大だった => 結果遅かった
- 自由度が高すぎ => class の形を改変できすぎる => Native パフォーマンス (JIT) に悪影響

2019 Jan 以降に突然打ち捨てられる<br/><small>(このへんの経緯知ってる人いたら教えてください)</small>
---
# 2019 March - 現在<br />Static デコレータ
- 静的に解析可能なデコレータ
- 出来ることを強く制限して, ネイティブ実装/トランスパイル/デコレータ実装をシンプルにするという考え方
---
# 2019 March - 現在<br />Static デコレータ
- @wrap @register @expose @initialize という4つのビルトインデコレータとその組み合わせでデコレータを表現するというシステム

```js
decorator @myDeco {
  @wrap(f) @register(g)
}
```
<small>↑ ここで f, g は関数</small>
---
# 2019 March - 現在<br />Static デコレータ
- @wrap @register @expose @initialize それぞれができることはすごい限られている, が champion によるユースケース観察の結果これらがあれば十分という判断
- 詳細は tc39/proposal-decorators 参照
---
# 2019 March - 現在<br />Static デコレータ
- babel プラグインは現在実装中 [babel/babel/pull/10388](https://github.com/babel/babel/pull/10388)
- がんばれ Nicolo
---
# まとめ
- いろいろあったけど今は Static デコレータという仕様になっています
- がんばれ proposal decorators
---
class: center, middle

ご清聴ありがとうございました
