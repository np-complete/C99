# 住所の危険性

住所は大変危険な存在です。
と言われても、多くの人は普段から当たり前のように扱っているので何が危険なのか実感が湧きにくいと思います。
この章では、住所への理解を深め、その危険性を明らかにしていきます。

なお、住所には、「住んでいるところ」という意味と「土地の登録番号(のようなもの)」という複数の意味で使われます。
後者の意味では地番や住居表示とも言われるようです。
適宜どちらの意味で使われているか推測しながら読んでください。

## 住所とはなにか

住所とは、地球上のある地点(範囲)に対して、**文字列** で **名前** を付けたものです。
おそらく世界中のほぼすべての国が、この名前を付けて土地を認識する行為を行っています。
地点に対しての別の表現方法として、緯度経度の **数値** で表す **測地系** があります。
また、2次元/3次元の **画像** で表す地図も、地点を表す表現方法の1つと言えるかもしれません。
重要なのは、これらは精度の差こそあれ **相互変換可能** だということです。
もちろん、現実空間の **自分が立っている場所** や、 **100m先で右に曲がって50m進んだところ** も相互変換可能です。

## 住所の構造

土地は、歴史的な経緯により **分割** され、それぞれ名前が付けられています。
分割されたそれぞれの内側も更に同じように分割され、その層がいくつも積み重なり、
広い範囲からだんだん狭い範囲をあらわす **木構造** をしています。
日本の場合、 都道府県 → 市区町村 → 大字 → ... といったような層になっています。

住所の文字列は、この木構造をエンコードしたものです。
日本の住所は木構造をそのままルートから辿っていくようにエンコードしますが、
世の中には複雑怪奇なエンコードをする国もあります。
その場合でも、住所の概念的構造が木構造になっているのは変わりません。

住所の概念的構造と変換の親和性が高いのは **地図** です。
一部に例外(**飛び地**)はあるものの、土地は基本的にひとかたまりになるように分割されます。
木構造を辿ることと、地図をズームインしていくことがほぼ等価になるので、
住所から地図上の一点に到達することは非常に簡単です。

ちなみに、[テクテクライフ](https://www.tekutekulife.com/)という地図を利用しためちゃくちゃ面白いゲームがあるので今すぐインストールしましょう。

## 人間から見た住所の特性

住所は文字列なので、人間にとっては **非常に覚えやすい** ものです。
特に住所の前半部分は **意味のある識別子** なので、曖昧な記憶でもリストから正しい答えを選択することが可能です。
曖昧な住所でも、住んでいる大まかな場所やその土地柄、**最寄り駅**、生活行動範囲、通っている学校などが推測できます。

住所は文字列なので、他人に簡単に伝えることができます。
これは、住所を教えた人が、見ず知らずの他人に **許可なく伝えることが可能** だということを意味します。
個人情報の意味をまだ理解していない子供の口を塞ぐことも難しいことが容易に想像できます。

住所は表記ゆれが非常に多くありますが、1つの土地に複数の全く違う住所表現が存在することは基本的にありません。
つまり、住所は本質的に1つの表現しかなく、二人の人物に教えた住所から、 **名寄せが可能** ということです[^1]。

[^1]: ECサイトAとECサイトBが結託したら購入情報を補完できる

住所は個人ではなく土地に付くので、同居する人間は同じ住所を共有します。
住所が一致する複数個人の情報を得た場合、同居している可能性が高いことから、**家族関係を推察** することができます。[^2]
また、子供が漏らしてしまった住所は、すなわち親の住所そのものです。

[^2]: 同じ地番に何件も戸建てが建っている場合もあるので不正解なこともある

通常、住所の表記が変更されることはほとんどありませんが、住所そのものを変更することは可能です。
これはいわゆる **引っ越し** と呼ばれ、50万円程度の費用と、住み慣れた部屋を失い、子供がいれば転校を余儀なくされ、見ず知らずの土地でまたゼロから生活を構築しなければならない羽目になります。

## 住所を知ると何ができるか

住所は場所を表すものなので、これを知るだけで場所に関する様々なサービスが利用可能です。
配送や出前などの輸送サービスは想像しやすいものですが、例えばリフォームの発注や、水道が出なくなったという通報や、救急車を呼ぶ、なども場所に関するサービスです。
これらの事業者は、例えば **クレジットカードが当人のもの** とか、 **声が本物** などの判定する手段を持たず、 さらに多くの場合は **その住所に住んでいる人の名前リスト** すら持っていないので、 **住所を不正利用した攻撃** が簡単にできてしまいます。
大量の出前を送りつける嫌がらせ[^3]や、救急車を不正に呼んで社会的な信用を失墜させることもできます。
着払いでゴミを送りつけることで単純に金銭面で被害を与えることもできます。
最近法改正で防がれたカニを送りつける詐欺も、本質的には住所の脆弱性を利用した攻撃です。

[^3]: 食べ物を処分せざるを得ない状況はかなりのストレスを与えるのでおそらく金銭的にペイする

住所は、電話口での個人認証など、簡易的な認証[^4]によく使われています。
銀行レベルは無理かもしれませんが、**なりすまし** が可能なサービスは無限にあると思われます。
インターネットネイティブではないサービスはこのような脆弱な認証経路が必ず存在し、
住所は電話番号などより秘匿されることが多いという認識があるので、特に強い認証要素になります。
何かを契約することは難しそうですが、重要なサービスを不正に解約することは可能なのではないかと予想します。

[^4]: 電話番号、生年月日などもよく使われる

## 住所の何が本質的に問題なのか

住所は個人ではなく場所に紐付いていて、使い分けができず、変更もできず、公開情報であることが問題です。
これは住所が住所という古臭い現実の存在であり続ける限り解決不能です。
システムで解決して、現実から住所の存在を消しましょう。
