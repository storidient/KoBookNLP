# KoBookNLP : Natural Language Processing Library for Korean Literary Text
KoBookNLP는 한국어 소설 텍스트을 위한 자연어처리 라이브러리로 다음과 같이 구성되어 있습니다.
* 등장인물 개체인식(Name Entity Recognition, NER)
* 상호참조해결(Coreference Resolution, Coref)
* 대사-발화자 찾기(Direct Quotation Assignment, Speaker Identification)
* [KoCoNovel 데이터셋](##KoCoNovel-Dataset)

**Note** : temporary repository for '2023 학부생연구지원프로그램 발표' in SNU

![Example for KoBookNLP](header.png "Example of KoBookNLP")

## KoCoNovel-Dataset
### Introduction
[위키문헌](https://ko.wikisource.org/wiki/%EC%9C%84%ED%82%A4%EB%AC%B8%ED%97%8C:%EB%8C%80%EB%AC%B8)에 있는 50편의 한국 근현대 소설 중단편 작품에 대해 등장인물 개체 인식, 상호참조해결, 대사-발화자 찾기를 주석한 데이터셋입니다.


<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" href="http://purl.org/dc/dcmitype/Dataset" property="dct:title" rel="dct:type">KoCoNovel Dataset은</span> <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>를 따르고 있습니다.

소설 목록은 `ListOfNovels.csv`에서 확인할 수 있습니다.

`data` 아래 각 소설 폴더는 다음과 같이 구성되어 있습니다.

* `_text.csv` : 20문장 내외의 장면으로 분할된 소설 텍스트
* `reader`: 장면 단위로 정보가 제한된 상태로, 독자 시점에서 상호참조관계 및 발화자가 주석된 데이터셋
* `omniscient`: 작품 세계를 기준으로 상호참조관계 및 발화자가 주석된 데이터셋

|episode|reader|omniscient|
|---|---|---|
|3|이 [**B 사감**]<sub>x</sub>이 감독하는 그 기숙사에 올해 가을 들어서 괴상한 일이 '생겼다'느니 보다 '발각되었다'는 것이 마땅할는지 모르리라.|이 [**B 사감**]<sub>x</sub>이 감독하는 그 기숙사에 올해 가을 들어서 괴상한 일이 '생겼다'느니 보다 '발각되었다'는 것이 마땅할는지 모르리라.|
|5|"나의 천사, 나의 하늘, 나의 여왕, 나의 목숨, 나의 사랑, 나를 살려 주어요, 나를 구해 주어요." [**사내**]<sub>y</sub>의 애를 졸리는 간청|"나의 천사, 나의 하늘, 나의 여왕, 나의 목숨, 나의 사랑, 나를 살려 주어요, 나를 구해 주어요." [**사내**]<sub>x</sub>의 애를 졸리는 간청|
|6|이 어쩐 기괴한 광경이냐! 전등불은 아직 끄지 않았는데 침대 위에는 기숙생에게 온 소위 '러브레터'의 봉투가 너저분하게 흩어졌고 그 알맹이도 여기저기 두서없이 펼쳐진 가운데 [**B 여사**]<sub>x</sub> 혼자 - 아무도 없이 제 혼자 일어나 앉았다.|이 어쩐 기괴한 광경이냐! 전등불은 아직 끄지 않았는데 침대 위에는 기숙생에게 온 소위 '러브레터'의 봉투가 너저분하게 흩어졌고 그 알맹이도 여기저기 두서없이 펼쳐진 가운데 [**B 여사**]<sub>x</sub> 혼자 - 아무도 없이 제 혼자 일어나 앉았다.|

위와 같이 작품에 정보의 비대칭성이 존재하는 경우에는 상호참조해결 주석이 다르게 되어 있습니다.(현진건, 'B사감과 러브레터')


`reader`와 `omniscient` 폴더에는 각각 `overlap_plural`, `default`가 존재합니다.
* `default` : plural entity(e.g. '우리')를 각 개인의 entity(e.g. '너', '나')와는 별개로 취급한 데이터셋
* `overlap_plural`: 등장인물의 합으로 표현 가능한 plural entity에 대해, 각 개인의 entity를 겹쳐서 표현한 데이터셋

| |default|overlap_plural|
|---|---|---|
text|[**첫째 처녀**]<sub>x</sub>는 호동그래진 눈에 무서워하는 빛을 띤다. … [**둘째 처녀**]<sub>y</sub>도 잠 오는 눈을 비비며 수상해한다.… 장난 잘 치고 짓궂은 짓 잘하기로 유명한 [**셋째 처녀**]<sub>z</sub>는 동무 말을 못 믿겠다는 듯이 이슥히 귀를 기울이다가, "딴은 수상한걸. 나는 언젠가 한 번 들어본 법도 하구먼. 무얼 잠 아니 오는 애들이 이야기하는 게지." 이때 그 괴상한 소리는 댁대굴 웃었다.[**세 처녀**]<sub>w</sub>는 귀를 소스라쳤다.|[**첫째 처녀**]<sub>x</sub>는 호동그래진 눈에 무서워하는 빛을 띤다. … [**둘째 처녀**]<sub>y</sub>도 잠 오는 눈을 비비며 수상해한다.… 장난 잘 치고 짓궂은 짓 잘하기로 유명한 [**셋째 처녀**]<sub>z</sub>는 동무 말을 못 믿겠다는 듯이 이슥히 귀를 기울이다가, "딴은 수상한걸. 나는 언젠가 한 번 들어본 법도 하구먼. 무얼 잠 아니 오는 애들이 이야기하는 게지." 이때 그 괴상한 소리는 댁대굴 웃었다.[**세 처녀**]<sub>x,y,z</sub>는 귀를 소스라쳤다.
clusters|[['첫째 처녀'], ['둘째 처녀'], ['셋째 처녀'], ['세 처녀']]|[['첫째 처녀', '세 처녀'], ['둘째 처녀', '세 처녀'], ['셋째 처녀', '세 처녀']]|

### Annotation-Guidelines
한국어 상호참조해결 주석 가이드라인은 [여기](KoCoNovel_Guidelines_kor.pdf)에서 확인할 수 있습니다.

### Format
`.jsonl`과 `.conll` 파일이 들어 있습니다. 파일의 내용은 동일하나, 변환의 번거로움을 줄이고자 두 가지의 format을 모두 제공합니다.

* `.jsonl`: coref cluster와 speaker-id 간의 관계를 비교적 쉽게 파악 가능
* `.conll`: 표준화된 format으로, [e2e-coref](https://github.com/kentonl/e2e-coref/), [s2e-coref](https://github.com/yuvalkirstain/s2e-coref), [LingMess](https://github.com/shon-otmazgin/lingmess-coref) 등 기존의 상호참조해결 모델에 바로 활용 가능

`.jsonl`을 활용한 data-exploration과 `.conll`을 활용한 기존 모델 학습 및 테스트는 [튜토리얼](##Tutorials)에서 확인할 수 있습니다.

## Tutorials
- KoCoNovel Dataset Exploration
- KoCoNovel e2e-coref model training

## Contact
데이터셋과 코드 사용에 궁금한 점이 있거나, 제안이 있을 경우에는 아래로 연락주시길 바랍니다.

- 김규희(서울대학교) salgu@snu.ac.kr
- 이수린(서울대학교) lsrwhite@snu.ac.kr

## Acknowledgments
이 연구는 2023 서울대학교 기초교육원의 학부생연구지원프로그램 지원을 받아 수행되었습니다. 
