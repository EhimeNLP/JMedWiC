[English](README.md) | [日本語(Japanese)](README-ja.md)
# JMedWiC

## Overview

JMedWiC is a Japanese dataset for Word-in-Context (WiC) tasks specifically focused on the medical domain. The dataset was constructed by automatically extracting candidate synonym/non-synonym pairs using Masked Language Models (MLM) and assigning gold labels through human annotation.
The dataset consists of two subsets, medical and general, each containing 1,000 pairs.

## Dataset Composition

| Subset | Instances | Target Vocabulary | Text Corpus |
|----------|------|---------|---------|
| medical  | 1,000 | [JMED-DICT](https://sip3-d2.naist.jp/jmed-dict.html) | [Wikipedia](https://huggingface.co/datasets/range3/wiki40b-ja) + [MSDマニュアル](https://www.msdmanuals.com)※ |
| general  | 1,000 | [BCCWJ Vocabulary List](https://repository.ninjal.ac.jp/records/3234) | Wikipedia |

※ Text scraped from the MSD Manual has been paraphrased using a medical-domain specialized LLM.

## Data Format

- `term`: The target word
- `context1`: The first sentence containing the target word.
- `context2`: The second sentence containing the target word.
- `label`: A boolean indicating word sense identity (`true` = synonymous, `false` = non-synonymous).
- `span1`: The character indices for the target word in `context1` [`start`, `end`].
- `span2`: The character indices for the target word in `context2` [`start`, `end`].

## Example
```
{"term": "隆起",  
 "context1": "当時の窟は海に面していたが、関東大震災による土地の隆起で現在の高さとなった。",  
 "context2": "大半の患者は、隆起が視認可能で漠然とした不快感を感じたり、無症状である。",  
 "label": false,  
 "span1": [25, 27],  
 "span2": [7, 9]  
}
```

## Citation
* Koki Horiguchi, Seiji Sugiyama, Tomoyuki Kajiwara, Shoko Wakamiya, Eiji Aramaki.  
JMedWiC: A Japanese Word-in-Context Dataset in the Medical Domain.  
Clinical NLP Workshop 2026. Mallorca, Spain. May 2026. [to appear]

* 堀口 航輝, 杉山 誠治, 梶原 智之, 若宮 翔子, 荒牧 英治.  
  JMedWiC：日本語医療分野の語義同一性判定データセット.  
  言語処理学会第32回年次大会, pp.3009-3013, March 2026. \[[PDF](https://www.anlp.jp/proceedings/annual_meeting/2026/pdf_dir/Q6-23.pdf)\]  
