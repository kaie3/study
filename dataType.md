# データ型

Rustの基準型は一般的にいい選択肢になります。  
整数型の基準はi32型です。  
64ビットシステム上でも、 この型が普通最速になります。

Rustの浮動小数点型は、f32とf64で、それぞれ32ビットと64ビットサイズです。  
基準型はf64です。  
なぜなら、現代のCPUでは、f32とほぼ同スピードにもかかわらず、より精度が高くなるからです。

|言語|大きさ|符号付き|符号なし|
|:-:|:-:|:-|:-|
|rust|8-bit|i8(-128<=i8<=127)|u8(0<=u8<=255)|
|rust|16-bit|i16(-32_768<=i16<=32_767)|u16(0<=u16<=65_535)|
|rust|32-bit|i32(-2_147_483_648<=i16<=32_147_483_647_767)|u32(0<=i16<=4_294_967_295)|
|rust|64-bit|i64(-9_223_372_036_854_775_808<=i16<=9_223_372_036_854_775_807)|u64(0<=i16<=18_446_744_073_709_551_615)|
|rust|arch(アーキテクチャ(32bit or 64bit)依存)|isize(-9_223_372_036_854_775_808<=isze<=9_223_372_036_854_775_807)|usize(0<=usize<=18_446_744_073_709_551_615)|

## 命名規則

|アイテム|規則|
|-|-|
|クレート| [不明](https://github.com/rust-lang-nursery/api-guidelines/issues/29)|
|モジュール | `snake_case`|
|型| `CamelCase`|
|トレイト| `CamelCase`|
|Enumのバリアント  | `CamelCase`|
|関数 | `snake_case`  |
|メソッド| `snake_case`  |
|一般のコンストラクタ| `new` または `with_more_details`|
|変換を行うコンストラクタ| `from_some_other_type`|
|マクロ  | `snake_case!`|
|ローカル変数  | `snake_case`|
|スタティック変数 | `SCREAMING_SNAKE_CASE`|
|定数 | `SCREAMING_SNAKE_CASE`|
|型パラメータ  | 簡潔な`CamelCase`、大抵は大文字で1文字: `T`|
|ライフタイム  | 短い`lowercase`、大抵は1文字: `'a`, `'de`, `'src`|
|Feature | [不明](https://github.com/rust-lang-nursery/api-guidelines/issues/101)、ただし[C-FEATURE](naming.html#c-feature)を参照 |

## javascriptでfalsyとなる値

[MDN Falsy (偽値)](https://developer.mozilla.org/ja/docs/Glossary/Falsy)  
null および undefined はヌル値でもあります。

|値|型|説明|
|-|-|-|
|null|null|キーワードnull,値が存在しないことを示します。|
|undefined|undefined|undefined,プリミティブ値。|
|false|論理値型|キーワードfalse|
|NaN|数値型|NaN — 数値ではない|
|0|数値型|数値ゼロ（従って、 0.0 や 0x0 なども含みます）|
|-0| 数値型|数値マイナスゼロ（従って、 -0.0 や -0x0 等も含みます）|
|0n|長整数型|長整数型のゼロ（従って、 0x0n も含みます）。なお、長整数型にはマイナスゼロはありません。   0n の負の数は 0n です|
|""|文字列型|空文字列値。'' や `` も含みます|
|document.all|オブジェクト|JavaScript で唯一の偽値のオブジェクトは、組み込みの document.all です|
