# analogRead()

ここは`analogRead()` 関数のページです

# 説明

指定されたアナログピンから値を読み取ります。Arduinoボードには、マルチチャンネル、10ビットのA/Dコンバータが搭載されています。つまり、0から動作電圧（5Vまたは3.3V）までの入力電圧を、0から1023までの整数値にマッピングします。例えば、Arduino UNOの場合、以下のような分解能になります。5ボルト/1024、つまり1個あたり0.0049ボルト（4.9mV）/div. です。各種Arduinoボードで使用可能なピン、動作電圧、最大分解能については、以下の表を参照してください。

入力範囲は`analogReference()`で変更でき、分解能は`analogReadResolution()`で変更できます（Zero、Due、MKRボードの場合のみ）

ATmegaベースのボード（UNO、Nano、Mini、Mega）では、アナログ入力を読み取るのに約100マイクロ秒（0.0001秒）かかるので、最大で1秒間に約1万回読み取れることになります

| ボード |	駆動電圧 |	使用可能なピン |	最大分解能 |
|----|----|----|----|
| UNO | 5V | A0〜A5 | 10ビット |
| Mini, Nano | 5V | A0~A7 | 10ビット |
| Mega, Mega2560, MegaADK | 5V | A0~A14 | 10ビット |
| Micro | 5V | A0~A11\* | 10ビット |
| Leonardo | 5V | A0~A11\* | 10ビット |
| Zero | 3.3V | A0〜A5 | 12ビット\*\* |
| Due | 3.3V | A0~A11 | 12ビット\*\* |
| MKR Family boards | 3.3V | A0~A6 | 12ビット\*\* |

\*A0からA5は基板上の記載通りのピン、A6からA11はそれぞれ4、6、8、9、10、12番ピンで使用可能です
\*\*これらのボードのデフォルトの analogRead() の分解能は、互換性を確保するため10ビットとなっています。12ビットに変更するには、`analogReadResolution()`を使用する必要があります

# 構文

`analogRead(pin)`

# パラメータ

`pin`：読み出すアナログ入力ピンの名前（ほとんどのボードではA0からA5、MKRボードではA0からA6、MiniとNanoではA0からA7、MegaではA0からA15）です

# 返り値

ピンのアナログ読み出しの値です。A/Dコンバータの分解能によって返ってくる値の幅が異なります（10ビットなら0〜1023、12ビットなら0〜4095）  
データ型：`int`

# サンプルコード

`analogPin`の電圧を読み取り、それをシリアルモニタに表示します

```cpp
int analogPin = A3; // A3ピンに可変抵抗を接続
int val = 0;  // 読み取った値を格納する変数

void setup() {
  Serial.begin(9600);           // シリアル通信のセットアップ
}

void loop() {
  val = analogRead(analogPin);  // 入力ピンを読み取る
  Serial.println(val);          // 値をシリアルモニタに出力
}
```

# 注意点

アナログ入力ピンに何も接続されていない場合、`analogRead()`が返す値は、様々な要因（他のアナログ入力の値、ボードに手がどれだけ近いか、など）に応じて変動することになります。

# 出典

このページは[Arduino公式のページ](https://www.arduino.cc/reference/en/language/functions/analog-io/analogread/)を翻訳したものです（一部意訳を含みます）

[一覧に戻る](https://pages.nchlab.net/Arduino/ref/)  
[トップページに戻る](https://pages.nchlab.net/)
