## biome の思想
意図的に強制するルールを作成し、コードの書き方を統一させることで無駄な議論を生まないようにする

これは prettier (formatter) の思想を受け継いでいるが、linter として使う際も同じようなことが言える。
ルールで強制させることは今後 AI にコードを書かせる際にも、統一感のあるコードを書けるという点で非常に有用です

## Installation
bun add -D -E @biomejs/biome
(minor patch version の違いで開発者間で異なる設定になる恐れがあるため固定します)

## Editor settings
https://biomejs.dev/reference/vscode/

## recommended で on になるルールは何？
default で recommended が on になっている

## default の recommended ルールについて見てみる
```ts
const n: {} = 0;
```
↑のコードを書いてみると `lint/complexity/noBannedTypes` が warning で出る
(ref: https://biomejs.dev/linter/rules/no-banned-types/)

## ルールを追加する
- noConsole のルールを error で追加してみる
```ts
console.log("Hello Biome!");
```
↑のコードを書いてみると `lint/suspicious/noConsole` が error で出る
(ref: https://biomejs.dev/linter/rules/no-console/)

## Plugins でカスタムルールを作成

## ルールの基準
error: 可読性が下がるので必ず修正してほしいもの
warn: 統一できててないと迷いが出るもの & 修正もそんなに大変じゃないはずのもの
info: 統一できてなくても気にならないレベル(人による)。できたら対応してほしいもの
