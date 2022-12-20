# KBN-Dataset-V2

**KBN-Dataset-V2**은  Knowledge Base Population (KBP)모델을 통해 기존의 데이터셋을 확장하여 만든 데이터셋이다.  

사용된 알고리즘은 **BERT Encoder + TransE Scoring** 기반 KBP을 사용하였고, 확장된 데이터셋 목록은 아래와 같다. 

1. 해외 Wiki-KB Dataset 확장  
영어 데이터셋 `FB15k-Expantion v1.0`와 `WN18RR-Expantion v1.0`으로 구성되어 있다. \
[WN18RR](https://arxiv.org/abs/1811.04441), [FB15k](https://www.microsoft.com/en-us/download/details.aspx?id=52312) 코퍼스에 대해 확장되었다.

2. 이전 Wiki-KB Dataset 확장  
영어 데이터셋 `KBNE-Expantion v1.0`와 한국어 데이터셋`KBNK-Expantion v1.0`으로 구성되어 있다. \
[KBN-EN 1.0, KBN-KO 1.0](https://github.com/usgnob/KBN-Dataset) 코퍼스에 대해 확장되었다.


## 목차
* [다운로드](#다운로드)
* [파일 형식](#파일-형식)
* FB15k-Expantion v1.0
* WN18RR-Expantion v1.0
* KBN-EN-Extention v1.0
* KBN-KO-Extention v1.0


## 다운로드
https://drive.google.com/drive/folders/14YU9hQQucUwpNGqVvH_Na8nLxEdaNNqL?usp=sharing

## 파일 형식
| 데이터명| 트리플 수 | 관계 수 | 엔터티 수 | 크기 |  포멧  | 
| :---: | :---: | :---: | :---: | :---: |   :---: |
| FB15k-Expantion-v1.0 |  471,374 | 237 | 14,951 | 78.2MB  | tsv
| WN18RR-Expantion-v1.0 |  133,920 | 11 | 40,943 |  13.3MB  | tsv
| KBN-EN-Expantion v1.0 |  2,220,304 | 141,055 | 2,549,078 | 295MB  | tsv
| KBN-KO-Expantion v1.0 |  4,705,320 | 48 | 691,712 |  145MB  | tsv


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




## KBN-EN-Expantion v1.0
KBN-EN v1.0는 영어 위키베이스에서 상호참조해결 및 Open Information Extract 태스크를 사용하여 구축한 데이터셋이다. \
본 작업에서는 KBN-EN v1.0 데이터셋(트리플 수 : 2,031,694)의 숨겨진 엔터티간 관계를 예측하여 새로운 데이터셋(트리플 수 : 2,220,304)으로 확장한다. \
`KBN-EN-Expantion v1.0` 데이터셋은 확장된 데이터셋, 엔터티사전, 관계 사전으로 구성되어 있다. \
`ind_all.tsv`는 KBP 수행 후 엔터티명, 관계명으로 이루어진 확장된 트리플 데이터셋이다  \
`entity2text.tsv`는 엔터티명에 대한 원본 엔터티 정보이다.  \
`relation2text.tsv` 는 관계명에 대한 원본 관계 정보이다.


#### 데이터 예시 
```py
#ind_all.tsv
78860048	grew	47136311
37095393	to_finance	47177735
75266537	Limited	84187556
42327259	had_developed	42327259
89034854	combined	74063069
29941407	married	31824814
16660268	adopted	98437123
33986167	have	64169165
81962286	had	73773974
26819709	was	14462038
62782581	was	64323365
...
```

## KBN-KO-Expantion v1.0
KBN-KO v1.0은 한국어 위키베이스에서 Relation Extraction을 사용하여 구축한 KB 데이터셋이다. \
본 작업에서는 KBN-KO v1.0 데이터셋(트리플 수 : 4,098,370)의 숨겨진 엔터티간 관계를 예측하여 새로운 데이터셋(트리플 수 : 4,705,320)으로 확장한다. 

`KBN-KO-Expantion v1.0` 데이터셋은 확장된 데이터셋, 엔터티사전, 관계 사전으로 구성되어 있다. \
`ind_all.tsv`는 KBP 수행 후 엔터티명, 관계명으로 이루어진 확장된 트리플 데이터셋이다  \
`entity2text.tsv`는 엔터티명에 대한 원본 엔터티 정보이다.  \
`relation2text.tsv` 는 관계명에 대한 원본 관계 정보이다.


#### 데이터 예시 
```py
#ind_all.tsv
13480598	team	21154481
35878336	child	26629477
46162719	deathPlace	82957176
90512674	deathPlace	45415611
73715684	country	7405309
24632428	opponent	80704354
92359255	region	82689331
18204476	league	9525029
11071262	country	77732616
54298565	region	79964486
97252904	deathPlace	52514224
75152248	religion	15622128
...
```