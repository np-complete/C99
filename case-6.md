## ケース6: 配送依頼

ここまでノータッチだった配送依頼をする現場を考えてみましょう。
住所が書けないということは、今までと同じように簡単に配達先の指定ができないということです。

### 登場人物

#### 送信者
荷物を出す人です。
`配達業者` が読み取れる住所トークンを持っています。

#### 配達業者
荷物を配達する人です。

#### 集荷業者
宛名印刷、集荷などをする人です。
具体的にはコンビニなどがこの役目を果たすことになると思います。

### 送り状
荷物に貼り付ける、配達先を指定するための書類です。

### ポイント

住所トークン自体は、人間が読み書きできる文字列で表現されていますが、
正確に手で書き写すことは不可能なランダムな長い文字列であり、また読み取る側も機械化を考えなくてはなりません。
そこで、バーコードやQRコードのような **機械で読み取りやすいフォーマット** が使われた `送り状` を印刷し、
荷物に貼り付けるという方法が主流になると思われます。

もちろん、一般の家庭にはそのような印刷機は存在せず[^1]、コンビニや郵便局が印刷機能を担うことになるでしょう。
また、住所トークンには送信者の情報が含まれ、本人であることが確認できなくてはいけません。

[^1]: するべきではない

### シーケンス

1. `送信者` は住所トークンを取得します。
2. `送信者` は `集荷業者` へ行き、端末を操作します。
3. 端末はQRコードを読み取れるようになっており、当システムの住所トークンページに表示される印刷用QRコードを読み取らせます。
4. 端末は `送り状` を印刷し、`送信者` は荷物に貼り付けます。
5. `集荷業者` は `送り状` のQRコードと `送信者` マイページのQRコードを読み取り、当システムに問い合わせるなどして **本人確認** をします。
6. 本人確認ができた場合、集荷を引き受け、配送業者に配送依頼します。

### 懸念点

この方式での懸念点は、QRコードという **共有しやすい画像** を経由するところです。
正当に得たQRコードを、悪意のある第三者に渡すことにより、不正に荷物が送れてしまいます。
QRコードでなくても、人間が機械に入力しやすい形式という時点で他の手段も大差ありません。

この危険性を避けるために、QRコードに有効期間をもたせ、かなり短めにするという対策が考えられます。
`送り状` 自体も、印刷からコンビニレジに渡すまでの時間を制限することが可能でしょう。
ただし、悪意のある第三者に **アカウントごと共有** された場合は対処できません。