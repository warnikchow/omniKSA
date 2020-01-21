# OmniKSA
### Speech Act and its Analysis for the (spoken) Korean Language: An Omnibus Description

본 레포지토리에서는, 다른 곳에서 잘 다루어지지 않는 한국어의 화행/의도 파악 및 분석에 관한 자연어처리 데이터셋들을 소개하고자 합니다. 언어철학적으로도 오래 연구된 주제인 동시에 산업적으로도 활용성이 높은 내용이지요. 저의 박사과정 research topic이기도 하구요 :D 어느 정도 스토리의 유기성을 위해 옴니버스 형식으로 서술할 예정입니다. 

본격적으로 이야기에 들어가기에 앞서, 제가 주로 다루고 구축에 참여했던 한국어 화행/의도 관련 데이터셋들을 한눈에 볼 수 있도록 리스팅해 보도록 하겠습니다.

### At a Glance: Speech Act/Intention-Related Datasets of WarnikChow

- **한국어 비정형 텍스트 화행 분류 데이터셋: [3i4K](https://github.com/warnikchow/3i4k)**  (7 Classes, 61K Utterances)

- **한국어 중의성 구문 음성 화행 분류 데이터셋: [ProSem](https://github.com/warnikchow/prosem)** (7 Classes, 7K Speech Utterances)

- **한국어 질문 및 요구 문장의 의도 및 토픽 유사도 데이터셋: ParaKQC** (550K Pairs, To be added)

- **한국어 질문 및 요구 문장의 원활한 시맨틱 파싱을 위한 논항 추출 데이터셋: [SAE4K](https://github.com/warnikchow/sae4k)** (50K Pairs)

## Speech Act

화행은 아직도 정의하기 어려운 개념이지만, 논의의 역사는 생각보다 오래되었습니다. 화용론(pragmatics)의 발전과 거의 맞닿아 있다고 볼 수 있을 것 같아요. 학교에서 배울 수 있는 화용론은 크게 함축(implication), 적합성 이론(relevance theory), 전제(presupposition), 화행(speech act), 지시(reference) 및 직시(deixis), 정보구조(information structure)로 이루어져 있고, 각 부분에서는 다음과 같은 내용들을 다루게 됩니다. 내용에 대한 부분은 제가 들었던 화용론 수업의 content를 참고했습니다. 박유경 선생님 최고 +_+

- **함축** - 대화 함축과 상례 함축(Conversational/Conventional implicature), 그라이스/신-그라이스 함축(Gricean/neo-Gricean implicature), 대화 격률(Maxims of conversation), 어휘 화용론(Lexical pragmatics)

- **적합성 이론** - 인지/의사소통의 적합성 원리(Cognitive/Communicative principle of relevance)

- **전제** - 의미/화용론적 전제(Semantic/Pragmatic presupposition), 전제 유발 표현(Triggers), 취소가능성(Defeasibility), 전제 투사(Projection)

- **화행** - 수행문/진술문(Performatives/cconstatives), 수행문 가설(Performative hypothesis), 적정 조건(Felicity condition), 언표/언표내적/언향적 화행(Locutionary/Illocutionary/Perlocutionary speech acts), 화행 분류(Typology), 직/간접 화행(Direct/Indirect speech acts), 공손성(Politeness)

- **지시 및 직시** - 지시/직시표현(Referring/Deictic expressions), 인물/시간/장소/사회/담화 직시(Person/Time/Space/Social/Discourse deixis)

- **정보구조** - 통사구조와 비-진리조건적 의미(Syntactic structure and non-truth conditional semantics), 화제성/대하여-성(Topic/About-hood), 문법/정보구조(Grammatical/Information structure)

중간에 화행이 꽤나 크게 들어가 있는 것을 확인할 수 있겠습니다. 다른 부분들도 물론 중요하지만, 모두 다루기에는 제가 화용론에 대한 내공이 부족하여... 자연어처리를 시작하는 시점부터 다뤄왔던 화행을 위주로 다뤄 보고자 합니다. 물론 다른 부분들과 화행에 관해서는 중간중간 짚어보고 넘어가야겠지요.

일단 전반적인 화용론의 기조를 살펴볼 때, 통사론/의미론처럼 어떤 이상적인 해석의 세계를 가정하는 경우와 다르게, 화용론은 연구 그 자체로 사람과 사람이 부대끼는 그 자체를 탐구하는 느낌이 없잖아 있습니다. 이론이란 것은 그것을 언어화한 것이고, 그나마 가장 기존 이론들과 양상이 유사한 부분을 형식화용론(formal pragmatics) 분야가 담당해주고 있지요.

그런 의미에서 화행도, 그 정의부터 놓고 봤을 때, 사람과 사람의 interaction으로부터 자유롭기 어렵습니다. Speech act라는 단어를 곱씹어 보면, Speech는 내가 혼자 하는 말일 수도 있고 남한테 하는 말일 수도 있지만 어떤 경우이든 화자와 청자를 가정하게 되겠지요. 비록 어떤 의미를 전달하려는 목적이 아니라고 해도요. Act라는 것은 비슷한 맥락에서, 그 발화(utterance)를 행하는 사람이 기대하는, 혹은 듣는 사람이 생각하는 행위라고 할 수 있습니다. 또 그 행위를 하는 주체는 화자/청자/둘 다가 될 수 있지요. 물론 **아무 의미 없다**고 하는 말, **그냥 해 본 말** 등등 다양한 반례들을 생각해볼 수 있겠지만, 어찌되었든 그래도 발화하는(utter) 것은 변하지 않고, 목적이 없다면 그것이 특징이 되겠지요. 발화의 형태도, 음성 발화가 주된 매체였던 예전에 비해, 요즘은 텍스트 형태 그 자체의 발화(채팅), 텍스트화된 음성(speech-to-text), 영상이 포함된 음성 발화(video) 등 여러 가지 경우를 생각해볼 수 있습니다.

다시 화행 자체의 얘기로 돌아와서, 수행문/진술문과 수행문 가설은 J. L. Austin의 다음의 내용을 포괄하게 됩니다.

## Syntactic Ambiguity Resolution

## Sentence Similarity

## Argument Extraction

