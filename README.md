# JMedWiC

## 概要
マスク言語モデルを用いて擬似的な同義・非同義ペアを自動抽出し，人手による同義性アノテーションを通じてラベルを決定することで，日本語の医療分野における語義同一性判定データセットを構築しました．
本データセットは，医療ドメインを対象とする **medical** と，一般ドメインを対象とする **general** の2つのサブセットから構成され，それぞれが1,000件となっています．

## データセット構成

| サブセット | 件数 | 対象語彙 | テキストコーパス |
|----------|------|---------|---------|
| medical  | 1,000 | [JMED-DICT](https://sip3-d2.naist.jp/jmed-dict.html) | [Wikipedia](https://huggingface.co/datasets/range3/wiki40b-ja) + [MSDマニュアル](https://www.msdmanuals.com)※ |
| general  | 1,000 | [BCCWJ語彙表](https://repository.ninjal.ac.jp/records/3234) | Wikipedia |

※ MSDマニュアルからスクレイピングしたテキストは，医療特化LLMによりパラフレーズしています．

## データ形式

- `term`: 対象単語
- `context1`: 文脈1
- `context2`: 文脈2
- `label`: 語義同一性ラベル（true=同義, false=非同義）
- `span1`: 文脈1における対象単語の文字位置 [開始位置, 終了位置]
- `span2`: 文脈2における対象単語の文字位置 [開始位置, 終了位置]

## データ例
```
{"term": "隆起",  
 "context1": "当時の窟は海に面していたが、関東大震災による土地の隆起で現在の高さとなった。",  
 "context2": "大半の患者は、隆起が視認可能で漠然とした不快感を感じたり、無症状である。",  
 "label": false,  
 "span1": [25, 27],  
 "span2": [7, 9]  
}
```

## 文献情報
* 堀口 航輝, 杉山 誠治, 梶原 智之, 若宮 翔子, 荒牧 英治.  
  JMedWiC：日本語医療分野の語義同一性判定データセット.  
  言語処理学会第32回年次大会, pp.3009-3013, March 2026. \[[PDF](https://www.anlp.jp/proceedings/annual_meeting/2026/pdf_dir/Q6-23.pdf)\]  
