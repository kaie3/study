# networkクラシック系

>**シリアル通信**について前知識を入れようと思ったら、調べていくうちに想像以上にシリアル通信の単語には紛らわしいものが沢山ありましたので要約してちょっとだけ載せておきます（間違っていたらごめんなさい）。
>RS-232C は正確には、後に改定され EIA-232-D となり、現在では運営組織が変わり、 TIA-232-F となっています。RS-232C では D-Sub 25 ピンと 26 ピンのピン配置しかしておらず、D-Sub 9 ピンのものは EIA/TIA-574 、RJ45 のものは EIA/TIA-561 が正式な規格です。ただし、（日本においては？）これらをすべて含めて広義な意味で RS-232C と呼ばれることがあります。
>また、シリアルポートを通じて接続されるシリアル通信デバイスは、CPU もしくは PCH には UART というデバイスを通じて接続されます。そのため、OS からは RS-232C デバイスとしてではなく、UART に接続されているデバイスとして見えます。その通信規格も異なるため、マザーボード上に RS-232C のシリアルポートがあったとしても、内部的で RS-232C と UART の変換を行っています。[ソース](https://hassiweb-programming.blogspot.com/2020/02/serial-comm-on-linux.html)

## [OSi参照モデル](https://stackoverflow.com/questions/38596488/in-which-layer-is-http-in-the-osi-model)

- TCP/IPモデルの中のアプリケーション層に所属
- HTTPはTCP/IP(インターネット基盤プロトコル)をベースにアプリレベルでデータ(メッセージ)のやり取りを行う

![OSi参照モデル](img\OSI参照モデル.jpg)
