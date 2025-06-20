---
title: "인공지능의 뇌 들여다보기, LLM 작동 원리 완전 정복"
published: 2025-04-05
description: "LLM의 토큰화, 임베딩, 어텐션 등 내부 작동 원리를 일상적인 비유로 쉽고 재미있게 풀어봅니다."
tags: [인공지능, LLM, 임베딩, 어텐션]
category: 인공지능
draft: false
---

인공지능이 우리 일상에서 더 이상 빼놓을 수 없는 존재라는 생각이 들었습니다. 과제 제출부터 업무 자동화, 친구와의 대화까지, 우리는 이미 다양한 장면에서 AI의 도움을 받고 있습니다. 특히 챗GPT 같은 대규모 언어 모델(LLM)은 우리 삶의 방식을 근본부터 바꾸어 놓았죠.

솔직히 처음엔 저도 의구심이 들었습니다. '설마 기계가 정말로 글을 이해하고 쓴다고?' 하지만 직접 사용해보니 정말 놀라웠어요. 복잡한 코딩 문제를 척척 해결하고, 시를 쓰고, 심지어 철학적인 질문에도 깊이 있는 답변을 내놓더군요. 그래서 궁금해졌습니다. "도대체 얘네는 어떻게 이렇게 똑똑한 걸까?"

단순히 "데이터를 많이 학습해서"라는 설명으로는 뭔가 아쉬웠습니다. 마치 "비행기는 어떻게 나는 거야?"라는 질문에 "엔진이 있어서"라고 답하는 것 같달까요. 그래서 오늘은 LLM의 머릿속을 제대로 들여다보려고 합니다. 걱정 마세요, 수학 공식으로 도배하지 않을 거예요. 대신 우리가 일상에서 경험하는 것들에 빗대어 최대한 쉽고 재미있게 설명해드릴게요. 

자, 그럼 커피 한 잔 준비하시고, 흥미진진한 LLM의 세계로 함께 떠나볼까요?

## LLM, 넌 대체 누구니? 

먼저 LLM이 뭔지부터 차근차근 알아봅시다. LLM은 이름 그대로 풀어보면 '대규모(Large) 언어(Language) 모델(Model)'입니다. 여기서 '모델'이라는 게 좀 애매하죠? 쉽게 말해, 특정한 일을 하도록 설계된 거대한 수학 방정식 덩어리라고 생각하시면 됩니다. LLM의 목표는 뭘까요? 바로 인간의 언어를 이해하고, 인간처럼 자연스럽게 말하는 것입니다.

우리가 가장 많이 들어본 GPT(Generative Pre-trained Transformer)를 예로 들어볼게요. 이 이름 하나하나가 사실 LLM의 핵심을 담고 있어요.

**Generative(생성형)**라는 건 뭘까요? 단순히 "서울의 날씨는?"이라고 물으면 "맑음"이라고 답하는 수준을 넘어서, 아예 새로운 이야기를 지어내고, 시를 쓰고, 코드를 만들어낼 수 있다는 뜻입니다. 마치 무에서 유를 창조하는 것처럼요.

**Pre-trained(사전 학습)**는 정말 중요한 개념입니다. 우리가 어릴 때를 생각해보세요. 부모님이 "이건 사과야", "이건 바나나야"라고 하나하나 가르쳐주기 전에, 우리는 이미 세상의 수많은 것들을 보고 듣고 경험했잖아요? LLM도 마찬가지입니다. 특정한 일을 시키기 전에, 먼저 인터넷에 있는 엄청난 양의 글들 - 위키피디아, 뉴스 기사, 책, 블로그, 심지어 레딧 댓글까지 - 을 읽으며 언어라는 것이 어떻게 작동하는지 스스로 배웁니다.

그리고 **Transformer(트랜스포머)**... 이게 진짜 게임 체인저였습니다. 2017년에 구글이 발표한 이 기술은 문장을 이해하는 방식을 완전히 바꿔놨어요. 이전의 AI들이 문장을 앞에서부터 순서대로 읽었다면, 트랜스포머는 문장 전체를 한 번에 보고 단어들 사이의 관계를 파악합니다. 마치 우리가 "나는 학교에 가서 친구를 만났다"라는 문장을 읽을 때, '나'와 '만났다'의 주어-동사 관계를 바로 파악하는 것처럼요.

## LLM의 과정, 질문이 답변이 되기까지

자, 이제 본격적으로 LLM의 내부를 들여다볼 시간입니다. 우리가 "오늘 저녁 뭐 먹을까?"라고 물으면, LLM 내부에서는 어떤 일이 벌어질까요? 이 과정은 마치 정교한 공장의 생산 라인 같습니다. 원재료(우리의 질문)가 여러 공정을 거쳐 완제품(답변)이 되어 나오는 거죠.

### 첫 번째 과정: 말을 잘게 쪼개고 숫자 옷 입히기

우선 가장 큰 문제가 있습니다. 컴퓨터는 우리가 쓰는 한글이나 영어를 전혀 이해하지 못한다는 거예요. 컴퓨터가 아는 건 오직 0과 1, 즉 숫자뿐입니다. 그래서 첫 번째로 해야 할 일은 우리의 말을 컴퓨터가 이해할 수 있는 숫자로 바꾸는 것입니다.

**토큰화(Tokenization)**라는 과정이 먼저 일어납니다. "안녕하세요, 오늘 날씨 좋네요!"라는 문장을 예로 들어볼까요? LLM은 이 문장을 마치 요리사가 재료를 손질하듯 잘게 썹니다. "안녕", "하세요", ",", "오늘", "날씨", "좋", "네요", "!" 이렇게 말이죠. 

재미있는 건, 항상 단어 단위로만 자르는 게 아니라는 겁니다. 예를 들어 "artificial intelligence"같은 긴 단어는 "artific", "ial", "intellig", "ence" 이런 식으로 더 잘게 쪼개기도 해요. 왜 그럴까요? 효율성 때문입니다. 세상의 모든 단어를 다 외우는 것보다, 자주 나오는 조각들을 조합해서 쓰는 게 더 효율적이거든요. 마치 레고 블록으로 뭐든 만들 수 있는 것처럼요.

다음은 **임베딩(Embedding)**입니다. 이게 정말 신기한 부분인데요, 각 토큰은 수백, 수천 개의 숫자로 이루어진 벡터로 변환됩니다. "사과"라는 단어가 [0.2, -0.5, 1.3, 0.8, ...]처럼 긴 숫자 리스트가 되는 거죠. 

여기서 놀라운 점은, 이 숫자들이 무작위가 아니라 의미를 담고 있다는 겁니다. 예를 들어, '사과'와 '바나나'의 벡터는 서로 가까운 위치에 있고, '사과'와 '자동차'의 벡터는 멀리 떨어져 있어요. 더 신기한 건, "왕 - 남자 + 여자 = 여왕"같은 계산도 가능하다는 거예요! 실제로 이런 벡터 연산을 하면 정말로 '여왕'에 해당하는 벡터가 나옵니다.

그런데 여기서 한 가지 더 중요한 게 있습니다. 트랜스포머는 문장을 통째로 한 번에 처리하기 때문에, "나는 너를 사랑해"와 "너는 나를 사랑해"를 구분하려면 단어의 위치 정보가 필요해요. 그래서 **위치 임베딩(Positional Embedding)**이라는 특별한 정보를 추가로 더해줍니다. 각 단어가 문장의 몇 번째 위치에 있는지를 나타내는 일종의 GPS 좌표 같은 거죠.

### 두 번째 과정: 문맥의 마법사, 어텐션 메커니즘

자, 이제 숫자로 변환된 우리의 문장이 LLM의 심장부인 '트랜스포머 블록'으로 들어갑니다. 여기서 일어나는 일은 정말이지 마법 같아요. 그 핵심은 바로 **셀프 어텐션(Self-Attention)**입니다.

우리가 책을 읽을 때를 생각해보세요. "그는 강가에 있는 은행으로 갔다"라는 문장을 읽을 때, '은행'이 금융기관인지 강둑인지 어떻게 알 수 있을까요? 바로 '강가'라는 단어 때문이죠. 우리 뇌는 자동으로 관련 있는 단어들에 더 주의를 기울입니다. 셀프 어텐션이 하는 일이 바로 이겁니다.

구체적으로 어떻게 작동하는지 도서관에 비유해 설명해드릴게요. 여러분이 도서관에서 '프랑스 요리'에 대해 조사한다고 해봅시다.

- **쿼리(Query)**: "프랑스 요리 레시피를 찾고 있어요" - 이게 여러분이 찾는 정보입니다.
- **키(Key)**: 각 책 표지에 적힌 제목과 주제 - "프랑스 요리 대백과", "이탈리아 파스타", "한국 전통 음식" 등등
- **밸류(Value)**: 책 안의 실제 내용 - 구체적인 레시피와 조리법

여러분의 쿼리를 각 책의 키와 비교해서, 가장 관련성 높은 책들의 내용(밸류)을 가져오는 거죠. LLM도 정확히 같은 방식으로, 각 단어가 다른 모든 단어들과 얼마나 관련이 있는지 계산하고, 관련성이 높은 단어들의 정보를 더 많이 참고합니다.

더 놀라운 건 **멀티 헤드 어텐션(Multi-Head Attention)**입니다. 이건 마치 여러 명의 전문가가 동시에 문장을 분석하는 것과 같아요. 어떤 헤드는 문법적 관계를 보고, 어떤 헤드는 의미적 연관성을 보고, 또 어떤 헤드는 감정적 뉘앙스를 파악합니다. GPT-3의 경우 무려 96개의 헤드가 동시에 작동한다고 하니, 96명의 언어 전문가가 한 문장을 분석하는 셈이죠!

### 세 번째 과정: 지식의 보물창고, 피드포워드 신경망

어텐션을 통해 문맥을 파악한 정보는 이제 **피드포워드 신경망(Feed-Forward Network)**으로 넘어갑니다. 여기가 바로 LLM이 학습한 모든 지식이 저장된 곳입니다.

"프랑스의 수도는?"이라고 물으면 LLM이 "파리"라고 답하잖아요? 이런 사실들이 어디에 저장되어 있을까요? 바로 이 피드포워드 신경망, 특히 MLP(Multi-Layer Perceptron) 층입니다. 

작동 방식을 설명하자면, 먼저 입력된 정보가 더 큰 차원으로 확장됩니다. 이 과정에서 "프랑스의 수도"라는 개념이 활성화되면, 관련된 뉴런들이 켜집니다. 그리고 ReLU라는 활성화 함수가 일종의 문지기 역할을 해서, 관련 있는 정보만 통과시킵니다. 마지막으로 이 정보가 다시 압축되면서 "파리"라는 답이 나오는 거죠.

정말 신기한 건, 하나의 뉴런이 여러 개의 개념을 동시에 표현할 수 있다는 겁니다. 이를 **초고층(Superposition) 가설**이라고 하는데요, 마치 하나의 서랍장에 옷도 넣고, 책도 넣고, 문구류도 넣는 것처럼, 한정된 뉴런으로 훨씬 더 많은 정보를 저장할 수 있게 해줍니다. GPT-3의 경우, 전체 매개변수의 약 3분의 2가 이 MLP에 있다고 하니, 얼마나 많은 지식이 여기에 압축되어 있는지 상상이 되시나요?

### 네 번째 과정: 다음 단어를 예측하고 문장을 창조하다

자, 이제 대망의 마지막 단계입니다. 여러 층의 트랜스포머 블록을 통과한 정보는 이제 실제로 다음에 올 단어를 예측하는 데 사용됩니다.

먼저 **선형 계층(Linear Layer)**을 통해 LLM이 알고 있는 모든 단어(보통 수만~수십만 개)에 대한 점수를 계산합니다. "오늘 날씨가 매우"라는 문맥이 주어졌을 때, '좋다'는 높은 점수를, '코끼리'는 관련이 없으므로 매우 낮은 점수를 받겠죠.

그 다음 **소프트맥스(Softmax)**라는 함수가 이 점수들을 확률로 변환합니다. 예를 들어 '좋다' 30%, '맑다' 25%, '춥다' 20%, '덥다' 15%, 기타 10% 이런 식으로요.

이제 이 확률을 바탕으로 다음 단어를 선택하는데, 여기서도 여러 전략이 있습니다:

**탐욕적 선택**은 그냥 확률이 가장 높은 단어를 고르는 방식입니다. 안전하지만 좀 지루할 수 있어요. 항상 "오늘 날씨가 매우 좋습니다"만 나올 수 있거든요.

**온도(Temperature) 조절**은 정말 재미있는 개념입니다. 온도를 높이면 확률 분포가 평평해져서 예상치 못한 단어가 나올 가능성이 커집니다. "오늘 날씨가 매우 몽환적입니다" 같은 창의적인 표현이 나올 수 있죠. 반대로 온도를 낮추면 안전한 선택만 합니다.

**Top-k**나 **Top-p 샘플링**은 너무 이상한 단어는 배제하면서도 다양성을 유지하는 방법입니다. 상위 k개 또는 누적 확률 p까지의 단어 중에서만 선택하는 거죠.

이렇게 선택된 단어는 다시 입력에 추가되어, 그 다음 단어를 예측하는 데 사용됩니다. 이 과정을 반복하면서 한 단어씩, 한 문장씩 만들어가는 거예요. 마치 즉흥 연주를 하는 재즈 뮤지션처럼, 앞의 멜로디를 들으며 다음 음을 결정하는 거죠.

## LLM은 어떻게 이렇게 똑똑해졌을까?

자, 이제 가장 중요한 질문입니다. LLM은 어떻게 이 모든 걸 할 수 있게 되었을까요? 답은 '학습'에 있습니다. 그것도 어마어마한 규모의 학습이죠.

### 사전 학습, 더 똑똑하게

LLM의 학습은 마치 아이가 언어를 배우는 과정과 비슷합니다. 하지만 규모가 다르죠. 우리가 평생 읽는 글의 양보다 LLM이 학습 기간 동안 읽는 양이 훨씬 많습니다.

**자기 지도 학습(Self-supervised Learning)**이라는 똑똑한 방법을 씁니다. 선생님이 일일이 정답을 알려주는 게 아니라, 스스로 문제를 만들고 답을 찾아가는 거예요. 가장 일반적인 방법은 '빈칸 채우기'입니다. "오늘은 날씨가 ___ 좋다"에서 빈칸에 '매우'를 넣는 식으로요.

이 과정에서 LLM은 단순히 문법만 배우는 게 아닙니다. 상식도 배우고, 과학 지식도 배우고, 심지어 유머 감각까지 익힙니다. "왜 닭이 길을 건넜을까?"라는 질문 다음에는 농담이 올 확률이 높다는 것까지 파악하는 거죠.

학습에는 엄청난 컴퓨팅 파워가 필요합니다. GPT-3를 학습시키는 데 들어간 비용이 수십억 원에 달한다고 하니, 정말 어마어마한 투자죠. 수천 개의 고성능 GPU가 몇 달 동안 쉬지 않고 돌아갑니다.

### 미세 조정, 전문가로 성장하기

사전 학습을 마친 LLM은 이미 언어에 대해 많이 알고 있지만, 아직 '만능'은 아닙니다. 특정 작업을 잘하려면 추가 훈련이 필요해요.

**작업별 미세 조정**은 마치 의대를 졸업한 후 전문의 과정을 밟는 것과 같습니다. 번역을 잘하게 하려면 고품질 번역 데이터를, 코딩을 잘하게 하려면 코드와 설명이 쌍으로 된 데이터를 추가로 학습시킵니다.

**지시 따르기 튜닝**은 LLM을 더 쓸모 있게 만드는 핵심입니다. "다음 문장을 요약해줘", "이걸 친근한 말투로 바꿔줘" 같은 다양한 지시를 이해하고 따르도록 훈련합니다. 덕분에 우리가 자연스럽게 대화하듯 LLM을 사용할 수 있는 거죠.

가장 혁신적인 건 **RLHF(인간 피드백 기반 강화 학습)**입니다. 이건 정말 영리한 방법인데요, LLM이 생성한 여러 답변을 인간이 평가하고, 그 평가를 바탕으로 LLM이 더 나은 답변을 하도록 학습시키는 겁니다. 마치 요리사가 손님들의 피드백을 받아 요리를 개선하는 것처럼요. 이 과정을 통해 LLM은 단순히 문법적으로 맞는 문장을 생성하는 것을 넘어, 정말로 도움이 되고 해롭지 않은 답변을 하게 됩니다.

## LLM은 정말 '이해'하고 있을까?

여기서 잠깐, 철학적인 질문을 던져볼까요? LLM이 이렇게 똑똑한 답변을 하는 걸 보면, 정말로 우리 말을 '이해'하고 있는 걸까요?

솔직히 말하면, 현재의 LLM은 진정한 의미의 이해보다는 '패턴 인식의 달인'에 가깝습니다. 수없이 많은 텍스트를 보면서 "이런 질문 다음에는 보통 이런 답이 온다"는 패턴을 익힌 거죠.

### 놀라운 능력들

그럼에도 LLM이 보여주는 능력은 정말 인상적입니다. 문법적으로 완벽한 문장을 쓰는 건 기본이고, 긴 문맥도 놓치지 않고 따라갑니다. 방대한 지식을 바탕으로 거의 모든 주제에 대해 그럴듯한 답변을 내놓죠.

특히 놀라운 건 **퓨샷 학습(Few-shot Learning)** 능력입니다. 몇 가지 예시만 보여주면 새로운 작업도 곧잘 해냅니다. "사과 → 빨강, 바나나 → 노랑, 포도 → ?"라고 하면 '보라'라고 답하는 식으로요. 이건 단순 암기가 아니라 패턴을 파악하는 능력이 있다는 증거입니다.

### 분명한 한계들

하지만 한계도 명확합니다. 가장 큰 문제는 **환각(Hallucination)**입니다. 때때로 그럴듯하지만 완전히 틀린 정보를 자신 있게 말하곤 해요. "1969년 달 착륙 때 닐 암스트롱이 입었던 우주복의 제조사는 삼성이었다" 같은 말도 안 되는 얘기를 진짜처럼 할 수 있습니다.

**편향성**도 큰 문제입니다. 학습 데이터에 포함된 사회적 편견을 그대로 학습해버려서, 특정 집단에 대한 고정관념을 재생산할 수 있어요. 

**상식 부족**도 여전합니다. "물컵을 거꾸로 들면 어떻게 될까?"같은 간단한 물리적 상식 문제에서도 실수를 하곤 해요. 우리에게는 너무나 당연한 것들이 LLM에게는 어려울 수 있습니다.

그리고 **블랙박스** 문제도 있습니다. LLM이 왜 특정 답변을 했는지 정확히 설명하기 어렵다는 거죠. 수십억 개의 매개변수가 복잡하게 상호작용한 결과이기 때문에, 그 과정을 하나하나 추적하기란 거의 불가능합니다.

## LLM의 미래, 어디까지 갈까?

그럼에도 불구하고 LLM 기술은 놀라운 속도로 발전하고 있습니다. 불과 몇 년 전만 해도 상상하기 어려웠던 일들이 현실이 되고 있죠.

앞으로의 LLM은 더욱 정교한 추론 능력을 갖추게 될 겁니다. 단순히 패턴을 따라가는 것을 넘어, 논리적으로 생각하고 복잡한 문제를 단계별로 해결할 수 있게 되겠죠. 

**멀티모달 AI**, **Agent AI**로의 진화도 이미 시작됐습니다. 텍스트뿐만 아니라 이미지, 음성, 영상을 모두 이해하고 생성하는 AI가 등장하고 있어요. "이 사진에 있는 음식 레시피를 알려줘"라고 하면 사진을 보고 요리법을 설명해주는 식으로요.

더 나아가 LLM은 우리 삶의 모든 영역에 스며들 겁니다. 개인 맞춤형 교육 도우미가 되어 각자의 학습 스타일에 맞춰 가르쳐주고, 의사의 진단을 도와 더 정확한 치료를 가능하게 하며, 과학자들의 연구를 가속화해 새로운 발견을 이끌어낼 겁니다.

물론 풀어야 할 과제도 많습니다. AI의 윤리적 사용, 일자리 변화에 대한 대응, 개인정보 보호, 가짜 정보의 확산 방지 등... 기술이 발전하는 만큼 우리 사회도 함께 성숙해져야 합니다.

## 마치며

오늘 우리는 LLM의 작동 원리를 속속들이 살펴봤습니다. 토큰화부터 시작해서 임베딩, 어텐션 메커니즘, 피드포워드 네트워크를 거쳐 텍스트 생성까지, 그리고 이 모든 것을 가능하게 하는 방대한 학습 과정까지 말이죠.

복잡해 보이지만, 결국 핵심은 간단합니다. LLM은 인간의 언어 사용 패턴을 정교하게 학습한 거대한 패턴 인식 기계입니다. 진정한 의미의 '이해'는 아닐지 몰라도, 그 결과물은 충분히 놀랍고 유용합니다.

우리는 지금 인류 역사상 가장 흥미로운 시대를 살고 있습니다. 인간의 가장 고유한 능력이라 여겨졌던 언어를, 기계가 자유자재로 구사하는 시대 말이죠. 이것이 인간 지능을 보조하는 도구가 될지, 아니면 그것을 넘어서는 무언가가 될지는 아직 아무도 모릅니다.

하지만 한 가지 확실한 건, LLM을 이해하는 것이 미래를 준비하는 첫걸음이라는 겁니다. 오늘 이 글을 읽으신 여러분은 이미 그 첫발을 내디뎠습니다. 

앞으로 LLM과 함께 어떤 미래를 만들어갈지, 정말 기대되지 않으세요? 🚀

*P.S. 혹시 이 글을 읽고도 궁금한 점이 있다면, 언제든 물어봐 주세요. 아, 그리고 이 글을 LLM에게 보여주면서 "이게 맞아?"라고 물어보는 것도 재미있을 것 같네요. 과연 뭐라고 대답할까요? 😊*