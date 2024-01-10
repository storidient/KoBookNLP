# KoBookNLP : A Natural Language Processing Library for Korean Literary Text
KoBookNLP는 한국어 소설 텍스트을 위한 자연어처리 라이브러리로 다음과 같이 구성되어 있습니다.
* 등장인물 개체인식(Name Entity Recognition, NER)
* 상호참조해결(Coreference Resolution, Coref)
* 대사-발화자 찾기(Direct Quotation Assignment, Speaker Identification)
* [KoCoNovel 데이터셋](##KoCoNovel-Dataset)

**Note** : temporary repository for '2023 학부생연구지원프로그램 발표' in SNU

![Example for KoBookNLP](header.png "Example of KoBookNLP")

## KoCoNovel-Dataset
위키문헌에 있는 50편의 한국 근현대 소설 중단편 작품에 대해 등장인물 개체 인식(NER), 상호참조해결(Coref), 대사-발화자 찾기를 주석한 데이터셋입니다.
소설 목록은 `ListOfNovels.csv`에서 확인할 수 있습니다.

`data` 아래 각 소설 폴더에는 `.jsonl`과 `.conll` 파일이 들어가 있음
* `reader`: 독자 시점을 기준으로 상호참조관계가 주석된 데이터셋. (주석자가 읽으면서 주석작업을 진행. 장면 단위로 정보가 제한되어, 뒤늦게 같은 인물이라는 것이 밝혀지는 경우에는 따로 주석되어 있음)
* `omniscient`: 전지적 작가 시점을 기준으로 상호참조관계가 주석된 데이터셋.

`.jsonl`과 달리, `.conll`은 coref cluster와 speaker-id를 파악할 수 없지만, [OntoNotes](https://paperswithcode.com/sota/coreference-resolution-on-ontonotes)와 같은 format으로 되어 있어, e2e-coref, s2e-coref, LingMess 등의 모델에 바로 적용할 수 있습니다.

### Statistics
