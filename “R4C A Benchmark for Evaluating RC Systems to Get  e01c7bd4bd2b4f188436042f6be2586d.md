# “R4C: A Benchmark for Evaluating RC Systems to Get the Right Answer for the Right Reason”, ACL2020

Created: 2022年4月9日 午前 2:09
Keywords: Dataset, Question Answering, XQA
Last Edited Time: 2022年4月18日 午後 10:23
Status: Read

*Naoya Inoue et al.*

# HotpotQAベースの文書読解用データセット

[2020.acl-main.602.pdf](https://aclanthology.org/2020.acl-main.602.pdf)

[R4C: A Benchmark for Evaluating RC Systems to Get the Right Answer for the Right Reason](https://slideslive.com/38928927/r4c-a-benchmark-for-evaluating-rc-systems-to-get-the-right-answer-for-the-right-reason)

[Right for Right Reasons RC (R4C)](https://naoya-i.github.io/r4c/)

## Backgrounds

NLP文書読解タスクにおいて，モデルが"ズル”をする場面が散見される．具体的には*"Who”*で始まる質問に対してはとりあえず見つかった固有名を解答として返す，など．

この解決のため，**Multi-hop；中継**(参照関係にある文書を辿って読解する方法)を用いたQAが提案されるなどしたが，必ずしも解答が見つけられない点など懸念は残る．

## HotpotQA

[HotpotQA](https://hotpotqa.github.io/index.html)は質問とその解答，対応する文書が付与されたデータセット．特徴は，与えられた文書の中で，**Supporting Facts (SFs)**と呼ばれる，いわゆる根拠となる文が示されている点．このデータセットにおいて，読解システムは解答に加えてSFsに当たる箇所を抜き出す必要があり，それには適切な**Reasoning**；”理由付け”や因果推論がなされた読解が求められる．根拠となる文はそれ単体ではなく，その周辺や関連性のない文がくっついてるので，適切な読解には文書要約等での根拠の抽出が必要．

## R4C

> R4C is short for “Right for the Right Reasons RC.”
> 

![Untitled](%E2%80%9CR4C%20A%20Benchmark%20for%20Evaluating%20RC%20Systems%20to%20Get%20%20e01c7bd4bd2b4f188436042f6be2586d/Untitled.png)

HotpotQAのSFsは文単位で与えられるため，一文の中に複数の事実が含まれることがある．

HotpotQAをベースに，解答に加えてその"由来"を付与．必要最低限の事実についての短文(**Derivation**)を各SFsに関連付けさせている．(上図参照)

Derivationの作成・評価については論文を参照．ざっくりいうとGoldを作ってそれらとのAlignmentを評価(レーベンシュタイン距離による類似度)．Goldの作成はクラウドソーシング．