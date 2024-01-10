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

`data` 아래 각 소설 폴더는 다음과 같이 구성되어 있습니다.
* `text.txt` : 소설 텍스트
* `reader`: 독자 시점을 기준으로 상호참조관계 및 발화자가 주석된 데이터셋. (장면 단위로 정보가 제한. e.g. 범인 정체가 뒤늦게 밝혀지면 이전 장면에서는 반영X)
* `omniscient`: 전지적 작가 시점을 기준으로 상호참조관계 및 발화자가 주석된 데이터셋.

| |Number of Entities|Number of Mentions|
|---|---|---|
reader|0|0|
omniscient|0|0|

`reader`와 `omniscient` 폴더는 각각 `.jsonl`과 `.conll` 파일이 들어 있습니다.
파일의 내용은 동일하나, 변환의 번거로움을 줄이고자 두 가지의 format을 모두 제공합니다.

* `.jsonl`: coref cluster와 speaker-id 간의 관계를 비교적 쉽게 파악 가능
* `.conll`: coref에서는 표준화된 format으로, [e2e-coref](https://github.com/kentonl/e2e-coref/), [s2e-coref](https://github.com/yuvalkirstain/s2e-coref), [LingMess](https://github.com/shon-otmazgin/lingmess-coref) 등 기존의 상호참조해결 모델에 바로 활용 가능

`.jsonl`을 활용한 data-exploration 파일과 `.conll`을 활용한 기존 모델 학습 및 테스트는 [Tutorial](##Tutorial)에서 확인할 수 있습니다.


### Statistics

## Tutorial
