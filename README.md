# KBN-Dataset-V2

**KBN-Dataset-V2**은  Knowledge Base Population (KBP)모델을 통해 만든 데이터셋이며,  \
영어 데이터셋 `FB15k-Expantion v1.0`와 `WN18RR-Expantion v1.0`으로 구성되어 있다. \
[WN18RR](https://arxiv.org/abs/1811.04441), [FB15k](https://www.microsoft.com/en-us/download/details.aspx?id=52312) 코퍼스에 대해 **BERT + TransE** 기반 KBP을 사용하여 확장된 데이터셋이다.


## 목차
* [다운로드](#다운로드)
* [파일 형식](#파일-형식)
* [FB15k-Expantion v1.0](#KBN_KO-v1.0)
* [WN18RR-Expantion v1.0](#KBN_EN-v1.0)

## 다운로드
https://drive.google.com/drive/folders/14YU9hQQucUwpNGqVvH_Na8nLxEdaNNqL?usp=sharing

## 파일 형식
| 데이터명| 트리플 수 | 관계 수 | 엔터티 수 | 크기 |  포멧  | 
| :---: | :---: | :---: | :---: | :---: |   :---: |
| FB15k-Expantion-v1.0 |  471,374 | 237 | 14,951 | 78.2MB  | tsv
| WN18RR-Expantion-v1.0 |  133,920 | 11 | 40,943 |  13.3MB  | tsv


## FB15k-Expantion v1.0
FB15K는 FreeBase 데이터셋에서 역관계 트리플을 제거한 변형 데이터셋이다 \
본 작업에서는 FB15k 데이터셋(트리플 수 : 310115)의 숨겨진 엔터티간 관계를 예측하여 새로운 데이터셋(트리플 수 : 471374)으로 확장한다.\
BERT Encoder을 통해 FB15k의 엔터티 Content Feature를 추출 한 후 TransE를 통해 엔터티 간 관계를 예측하였다. 

`FB15k-Expantion v1.0` 데이터셋은 원본데이터셋, 확장된 데이터셋, 엔터티사전, 관계 사전으로 구성되어 있다. \
`all_triples.tsv`는 KBP 수행 전 엔터티명, 관계명으로 이루어진 트리플 데이터셋이다. \
`result_triples.tsv`는 KBP 수행 후 엔터티명, 관계명으로 이루어진 확장된 트리플 데이터셋이다  \
`entity2text.tsv`, `entity2textlong.txt`는 엔터티명에 대한 원본 엔터티 정보이다.  \
`relation2text.tsv` 는 관계명에 대한 원본 관계 정보이다.

#### 데이터 예시 
```py
#result_triples.tsv
/m/02swsm	/music/record_label/artist	/m/04d_mtq
/m/01kym3	/people/person/nationality	/m/03_3d
/m/02x4sn8	/award/award_category/nominees./award/award_nomination/nominated_for	/m/0170yd
....

#entity2text.tsv
/m/02swsm	Hollywood Records
/m/04d_mtq	Kevin Jonas
/m/01kym3	Megumi Hayashibara
/m/03_3d	Japan
...
```


## WN18RR-Expantion v1.0
WN18RR는 WN18 데이터셋에서 역관계 트리플을 제거한 변형 데이터셋이다 \
본 작업에서는 WN18RR 데이터셋(트리플 수 : 93000)의 숨겨진 엔터티간 관계를 예측하여 새로운 데이터셋(트리플 수 : 133920)으로 확장한다.\
BERT Encoder을 통해 WN18RR의 엔터티 Content Feature를 추출 한 후 TransE를 통해 Entity 간 관계를 예측하였다.

`WN18RR-Expantion v1.0` 데이터셋은 원본데이터셋, 확장된 데이터셋, 엔터티사전, 관계 사전으로 구성되어 있다. \
`all_triples.tsv`는 KBP 수행 전 엔터티명, 관계명으로 이루어진 트리플 데이터셋이다. \
`result_triples.tsv`는 KBP 수행 후 엔터티명, 관계명으로 이루어진 확장된 트리플 데이터셋이다  \
`entity2text.tsv`는 엔터티명에 대한 원본 엔터티 정보이다.  \
`relation2text.tsv` 는 관계명에 대한 원본 관계 정보이다.


#### 데이터 예시 
```py
#result_triples.tsv
05034989    synset_domain_topic_of  06037666
09617161	derivationally_related_form    06694149
12319687    member_meronym  12321077
....

#entity2text.tsv
05034989	valency, (biology) a relative capacity to unite or react or interact as with antigens or a biological substrate
06037666	biology, the science that studies living organisms
09617161	panegyrist, an orator who delivers eulogies or panegyrics
06694149	pean, a formal expression of praise
...
```