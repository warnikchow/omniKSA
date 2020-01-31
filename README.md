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

화행은 아직도 정의하기 어려운 개념이지만, 논의의 역사는 생각보다 오래되었습니다. 화용론(pragmatics)의 발전과 거의 맞닿아 있다고 볼 수 있을 것 같아요. 학교에서 배울 수 있는 화용론은 크게 함축(implication), 적합성 이론(relevance theory), 전제(presupposition), 화행(speech act), 지시(reference) 및 직시(deixis), 정보구조(information structure)로 이루어져 있고, 각 부분에서는 다음과 같은 내용들을 다루게 됩니다. 내용에 대한 부분은 제가 들었던 화용론 수업의 content를 참고했습니다. **박유경 선생님 최고 +_+**

- **함축** - 대화 함축과 상례 함축(Conversational/Conventional implicature), 그라이스/신-그라이스 함축(Gricean/neo-Gricean implicature), 대화 격률(Maxims of conversation), 어휘 화용론(Lexical pragmatics)

- **적합성 이론** - 인지/의사소통의 적합성 원리(Cognitive/Communicative principle of relevance)

- **전제** - 의미/화용론적 전제(Semantic/Pragmatic presupposition), 전제 유발 표현(Triggers), 취소가능성(Defeasibility), 전제 투사(Projection)

- **화행** - 수행문/진술문(Performatives/cconstatives), 수행문 가설(Performative hypothesis), 적정 조건(Felicity condition), 언표/언표내적/언향적 화행(Locutionary/Illocutionary/Perlocutionary speech acts), 화행 분류(Typology), 직/간접 화행(Direct/Indirect speech acts), 공손성(Politeness)

- **지시 및 직시** - 지시/직시표현(Referring/Deictic expressions), 인물/시간/장소/사회/담화 직시(Person/Time/Space/Social/Discourse deixis)

- **정보구조** - 통사구조와 비-진리조건적 의미(Syntactic structure and non-truth conditional semantics), 화제성/대하여-성(Topic/About-hood), 문법/정보구조(Grammatical/Information structure)

중간에 화행이 꽤나 크게 들어가 있는 것을 확인할 수 있겠습니다. 다른 부분들도 물론 중요하지만, 모두 다루기에는 제가 화용론에 대한 내공이 부족하여... 자연어처리를 시작하는 시점부터 다뤄왔던 화행을 위주로 다뤄 보고자 합니다. 물론 다른 부분들과 화행에 관해서는 중간중간 짚어보고 넘어가야겠지요.

일단 전반적인 화용론의 기조를 살펴볼 때, 통사론/의미론처럼 어떤 이상적인 해석의 세계를 가정하는 경우와 다르게, 화용론은 연구 그 자체로 사람과 사람이 부대끼는 그 자체를 탐구하는 느낌이 없잖아 있습니다. 이론이란 것은 그것을 언어화한 것이고, 그나마 가장 기존 이론들과 양상이 유사한 부분을 형식화용론(formal pragmatics) 분야가 담당해주고 있지요.

그런 의미에서 화행도, 그 정의부터 놓고 봤을 때, 사람과 사람의 interaction으로부터 자유롭기 어렵습니다. Speech act라는 단어를 곱씹어 보면, Speech는 내가 혼자 하는 말일 수도 있고 남한테 하는 말일 수도 있지만 어떤 경우이든 화자와 청자를 가정하게 되겠지요. 비록 어떤 의미를 전달하려는 목적이 아니라고 해도요. Act라는 것은 비슷한 맥락에서, 그 발화(utterance)를 행하는 사람이 기대하는, 혹은 듣는 사람이 생각하는 행위라고 할 수 있습니다. 또 그 행위를 하는 주체는 화자/청자/둘 다가 될 수 있지요. 물론 **아무 의미 없다**고 하는 말, **그냥 해 본 말** 등등 다양한 반례들을 생각해볼 수 있겠지만, 어찌되었든 그래도 발화하는(utter) 것은 변하지 않고, 목적이 없다면 그것이 특징이 되겠지요. 발화의 형태도, 음성 발화가 주된 매체였던 예전에 비해, 요즘은 텍스트 형태 그 자체의 발화(채팅), 텍스트화된 음성(speech-to-text), 영상이 포함된 음성 발화(video) 등 여러 가지 경우를 생각해볼 수 있습니다.

### Austin - 수행문 가설과 적정 조건

<p align="center">
    <image src="https://github.com/warnikchow/omniKSA/blob/master/images/1962%20austin.PNG" width="500"><br/>
    <i>Austin (1962). 화행 이론의 시작점.<i>

다시 화행 자체의 얘기로 돌아와서, 수행문/진술문과 수행문 가설은 J. L. Austin의 다음의 내용을 포괄하게 됩니다.

- 참/거짓을 가릴 수 없는 발화가 수없이 많다는 것 (질문과 명령 등)

- (이어서) 진리조건으로 해석할 수 없는 평서문들, 즉 수행문이 존재하며, 말하는 것 이상의 행위로 해석되고, 기술하는 것 이상의 실효성이 있음

이 배경에는 암시적 수행문을 설명하기 위한 수행문 가설(performative hypothesis)이 자리잡고 있습니다. 

- **I (hereby) Vp you (that) S**

즉, 모든 문장 S에는 보이지 않는 기저의 주절에 어떤 수행동사 구조가 있다는 것입니다. 해당 이론은 '수행 동사 구조로 환원되지 않는 수행문이 있다'는 사실들로부터, 큰 지지를 얻지 못하게 됩니다. 다만 Austin (1962) 이 주장한 내용들 중 또다시 눈여겨볼 부분은, 수행문의 적정 조건(felicity condition)에 관한 것입니다. 이는 단어, 혹은 문장의 발화가 행위를 *적절하게* 수행하기 위해 필요한 조건을 의미하는 것으로, 다음과 같은 내용으로 구성되어 있습니다.

- 대화 참가자들은 상황에 따라 관례적 절차를 정확하고, 완전하게 수행해야 한다.

- 참가자들은 절차에 필요한 생각, 감정, 의도를 갖고 있어야 한다.

- 만일 후속 행동/조치가 명시되어 있으면, 그대로 따라야 한다.

이는 우리의 대화에서 항상 지켜지는 부분은 아니라는 점에서, Gricean maxim과 통하는 바가 있죠. 실제로 모두가 성심성의껏 대화에 참가하고 있다는 것은 굉장히 강력한 조건이고, 일상의 발화에뿐 아니라 공식적인 토론에서마저 지켜지지 않는 경우도 많으며, utter하는 내용과 intend하는 바가 차이가 생기는 경우는 아주 빈번합니다 (잘 가/가지마?). 그렇지만 저런 조건들을 이상적으로 가정하는 것은 마치 음성인식에서 clean condition을 가정하는 것과 비슷하다고 생각합니다. 일단 해석할 수 있는 경우에 대한 이론을 정립해 두고 나면, 그렇지 않은 경우에 대해 대응할 방안도 생각해 볼 수 있는 거니까요. 너무 pipeline적인 생각인지는 모르겠지만, 어쨌든, 수행문 가설과 적정 조건을 골자로 하는 초기 Austin의 연구는 다음과 같은 내용을 포함하여 발전하게 됩니다.

- **수행문 개념의 확대**: 수행문은 통사 의미적으로 특수한 부류의 문장/발화이며, 명시적 수행문 뿐만 아니라 암시적 수행문도 포함

- **화행에 관한 일반 이론**: 초기의 수행문/진술문의 이분법을 버리고 다양한 수행문들과 진술문들을 포괄하는 일반화행이론으로 확대

### Searle - 언표내적행위

Austin이 처음에 수행문과 진술문로 분류해 두었던 발화의 체계는, 화자와 청자를 고려하여 보다 복합적으로 변화하게 됩니다. 어떤 사람이 발화를 하게 된다는 것은, 발화 행위 자체도 있지만, 그것으로 화자가 의도하는 세상의 변화가 있고, 또 그것을 듣는 청자에게 실제로 나타날 만한 현상들을 동반하게 됩니다. Austin은 이를 각각 다음과 같이 설명합니다.

- **언표적 행위(locutionary act)**: 발화하는 행위 그 자체

- **언표내적 행위(illocutionary act)**: 발화를 통해 화자가 의도하는 것

- **언향적 행위(perlocutionary act)**: 발화 행위로 인해 청자에게 결과로써 나타날 만한 행위

<p align="center">
    <image src="https://github.com/warnikchow/omniKSA/blob/master/images/1962%20austic%20illo.png" width="500"><br/>
    <i>언표적 행위, 언표내적 행위, 언향적 행위<i>

언표적 행위는 사실 매우 명확합니다. 우리가 일상 생활에서 발화(여기서는 speak)를 하면 그것이 언표적 행위이고, 그 과정을 지칭하는 데에는 다른 행위들이 개입할 필요가 없습니다. 좀 더 자세히는 언표적 행위가 phonic act(음성 발화 시에는 물리적인 sound를 내고, 글을 쓸 때에는 text를 작성하는 것), phatic act(소리나 텍스트를 조합하여 말로써 성립하는 시퀀스로 만드는 것), 그리고 rhetic act(발화가 어떠한 의미를 갖게 하는 작업)으로 나눠진다고 하지만, 여기서는 그것을 따로 구별하지 않을 예정입니다. 좀 더 제가 주목하고 싶었던 것은 언표내적 행위와 언향적 행위의 개념입니다.

<p align="center">
    <image src="https://github.com/warnikchow/omniKSA/blob/master/images/1976%20searle.png" width="500"><br/>
    <i>언표내적 행위의 다양한 해석.<i>

언표내적 행위는 발화를 통해 화자가 의도하는 것으로, 언표내적 힘(illocutionary act)에 의해 결정됩니다. 발화 하나의 존재로써 행위가 결정되는 언표적 행위와 달리, 한 발화에서는 여러 가지 언표내적 행위가 수반될 수 있습니다. 다음과 같은 예문을 들어 보겠습니다.

*왜 이렇게 늦게 오셨어요*

많은 문장들이 그렇겠지만, 의문사를 필두로 하는 문장은 컨텍스트와 뉘앙스에 따라 천차만별의 해석이 가능해지게 됩니다. 상사가 아침에 지각한 사원에게 하는 말이라면 질책이 될 것이고, 평소에 늦지 않던 상사가 늦게 왔다면 의외라는 감정의 표현, 그리고 동시에 실제 늦은 이유를 묻는 것일 수도 있을 것입니다. 또한 뉘앙스에 따라, 많은 상황에서는 질책과 동시에 다시 늦지 말라는 경고, 금지의 표현이 될 수도 있겠죠. 또한 극단적인 경우로, 망자를 뒤늦게 접했을 때 슬픔을 표현하는 발화일 수도 있습니다. 물론 여러 가지의 발화가 동시에 한 가지 언표내적 행위를 의도할 수도 있구요. 언향적 행위는, 저 말을 들은 청자가 수행할 만한 행위들을 의미합니다. 이는 언표내적 행위와 연관될 수 있지만, 같은 개념은 아닙니다. 만약 언표내적 행위가 '질책'이었다면 언향적 행위는 '반성'이 될 수 있겠으며, '놀람'이라면 '진정, 해명' 등이 될 수 있겠지요. 물론 화자가 여럿이라거나(성명문), 청자가 없거나(독백; 청자=화자인 경우 포함), 여럿인 경우(대담) 등은 또 다른 양상으로 언표내적 행위 및 언향적 행위가 해석되어야 할 것입니다.

Searle은 이러한 speech act들 중 illocutionary act, 즉 언표내적 행위를 크게 다섯 가지로 유형화합니다.

- **대언 행위** Representatives: Austin의 진술문에 해당. 화자의 믿음을 전달하고 진리치를 갖는 명제를 표현. 결론, 보고, 진술 등을 포함.

- **지시 행위** Directives: 화자가 청자로 하여금 어떤 일을 하도록 의도하는 행위로, 충고, 명령, 질문, 금지 등을 포함

- **위임 행위** Commissives: 화자 스스로 어떤 일을 하겠다고 다짐하는 것으로, 제안, 맹세, 약속, 거부 등을 포함

- **표출 행위** Expressives: 화자의 심리적인 태도나 상태를 표현하는 것으로, 비난, 축하, 감사, 찬양 등을 포함

- **선언 행위** Declaration: 일종의 제도화된 수행문(institutionalized performatives)으로, 입찰, 선전포고, 제명, 임명 등을 포함

사실 이런 유형화의 문제에 정답은 없기 때문에, 여러 이론이 엎치락뒤치락하곤 합니다. 그래도 Searle의 이 다섯 가지 분류는, 지금 봐도 상당히 포괄적이라고 생각합니다. 물론 화행이란 것이 어느 정도 언어를 타기도 하고, '선언 행위'처럼 잘 와닿지 않는 부분도 있지만요. 사실 화행 분류에서 가장 어려운 부분은, 서로 겹치는 부분이 없게 잘 boundary를 만드는 것이 아닐까 생각합니다. 예컨대 한 가지 발화가 동시에 무언가를 지시하면서 화자의 심리적인 태도나 상태를 표현할 수도 있겠으며, 선언 행위와 대언 행위가 완전히 별개는 아닌 것으로 느껴지기도 합니다. 이런 문제는 대화 컨텍스트, 뉘앙스, 화자와 청자의 정체 및 사회적 위치, 문화적 맥락 등 영향을 끼칠 수 있을 만한 모든 것에 따라 다르게 해석될 수 있으니까요.

### Levinson - 직/간접화행과 공손성

그래도 확실히 해야 할 점이 있다면, 화행의 개념은 '문장 유형'이라는 통사적 개념과는 연관은 있으나 같은 개념은 아니라는 것입니다. 이 점은 의도파악 데이터셋을 구축할 때 종종 간과되는 점이기도 합니다. 예컨대, '내일 아침 여덟 시에 화자를 전화로 깨워주기'라는 부탁을 하는 방식에는 여러 가지가 있습니다.

<p align="center">
    <image src="https://github.com/warnikchow/omniKSA/blob/master/images/1982%20levinson.png" width="500"><br/>
    <i>전화를 깨워 달라고 하고 싶다면?<i>

*전화 좀 부탁해 내일 아침에 잊지마 여덟시야*

*나 내일 아침 여덟시쯤 모닝콜 해줄 수 있어?*

*내일 아침 여덟시에 나 좀 전화로 깨워주라*

각각 문장 유형은 평서문, 의문문, 명령문이지만, 궁극적으로 원하는 것은 청자가 화자를 내일 아침에 전화로 깨워 주는 것입니다. 이 경우 세번째는 '명령문'이라는 문장 유형이 화행인 '요청'에 부합하는 직접 화행(direct speech act)이지만, 다른 두 경우는 각각 평서문과 의문문의 형식을 빌려 요청하는 간접 화행(indirect speech act)에 해당합니다. 이를 좀 더 복잡하게 말하면, 직접 화행은 문장의 형식이 언표내적 힘을 결정하는 것이고, 간접 화행에서는 그러하지 못합니다. 

Levinson (1983)은 이러한 관찰들로부터 문자적 힘 가설(literal force hypothesis)을 주창했는데, 그 핵심 내용은 화행에 따라 특정 문장 형식이 결정된다는 것이고, 나아가서 한 가지 언표내적 행위(illocutionary act)는 한 가지 문장 유형(clause type)에 대응된다는 것입니다. 좀 너무 나간 것 같은 느낌이 없지 않아 있지요. 저 역시 여전히, 형식은 형식이고 화행은 화행이며, 하나가 다른 하나를 결정하지는 않는다고 생각합니다. 이런 생각들을 바탕으로, Gazdar은 '한 가지 발화는 여러 화행을 의도할 수 있다', 그리고 '화행의 결정은 청자의 해석에 영향을 받는다'는 두 가지 argument로 Levinson을 반박했습니다. 이후 clause type, dialog act, communicative function 등을 이용해서도 설명할 예정이지만, 이 문제는 Levinson이 주장한 것처럼 단순히 1-1 mapping을 구축한다고 해결되는 문제가 아닌 것 같습니다.

하지만 Levinson의 시도들이 의미가 없는 것은 아닙니다. 예컨대, 위에서 한국어의 예시로 설명했지만, 영어도 마찬가지로 어떤 것을 요청하는 데에는 다양한 수식어구들이 들어가곤 합니다. Searle의 경우 상례화(conventionalized) 경향으로 설명된 내용이지만, Levinson은 이를 체면 유지 전략(face-saving strategy) 및 체면 위협 행위(face-threatening act)의 개념을 도입하여 설명했습니다. 또한 그는 사회적 거리감(D; social distance), 청자가 화자에 대해 갖는 상대적 권위(P; relative power), 그리고 특정 문화에서의 지위의 절대적 순위(R; absolute ranking)라는 세 가지 요소를 도입하여 FTA-avoiding strategy 를 체계화했습니다. 즉, 체면을 심하게 위협하는 행위일수록 화자는 그 실효를 완화시키기 위해 공손한 책략을 써야 한다는 내용인데요, 생각해 보자면 밤 늦게 일을 부탁하는 경우 더 공손한 어투와 어미와 어휘를 써서 문서를 작성하는 것 등을 들 수 있겠습니다. 물론 그것을 수치화시키는 것은 계산화용론 등의 분야에서 더 잘 다룰 수 있는 것으로 보입니다. 

<p align="center">
    <image src="https://github.com/warnikchow/omniKSA/blob/master/images/1983%20levinson%20otsazuke.jpg" width="500"><br/>
    <i>Slide from https://slidesplayer.org/slide/11379678/. 오차즈케는 녹차에 만 밥을 의미하는 것으로, 일본어의 관점에서는 "이제 그만 가야겠습니다"라는 언향적 행위를 기대하게 된다<i>

나아가, 이로부터, 화행은 문화 변이가 상당하다는, 꽤나 당연한 결론을 얻을 수도 있습니다. 그런 것은 비슷한 syntax를 공유하지만 전혀 다른 공손성의 양상을 보이는 한국어와 일본어의 예시로부터도 알 수 있습니다. 일본에서 '괜찮습니다'는 강력한 거절의 의미라면서요...? 물론 언제까지고 이런 발화 양상이 유지된다는 보장도 없을 뿐더러 개인차도 심하고, 지역 편차도 있을 겁니다. 그게 화행 연구의 가장 어려운 점이지요. 좀 더 확실하게 접근할 방법이 있을까요?

### Portner - 형식 의미론적 접근

Portner의 형식 의미론을 기반으로 한 접근은 제가 제일 많이 이용한 방식이기도 하고, 사실 이러한 해석에서 벗어나기도 쉽지 않을 만큼 문제를 추상화시켜둔 방법입니다. 바로 clause type을 화행의 관점에서 형식적으로 정의하는 것입니다. 일단 그러기 위해서는 clause type이 어떻게 유형화될 수 있는지 먼저 알아봐야 하겠습니다. 문장 유형은 결국 한국어로 따지면 종결 어미를 보는 것이고, 영어로 따지면 어두에 의문사가 오는 의문문(interrogative)인지 그렇지 않은 평서문(declarative)인지, 혹은 covert subject로 시작하는 명령문(imperative)인지 보는 것으로, 문법적으로 결정할 수 있는 굉장히 straightforward한 절차입니다. Portner은 각각이 다음과 같이 형식의미론적으로 정의될 수 있다고 정리합니다.

- **평서문(declarative)**: Proposition (p)의 모음을 청자와 화자의 공통 지식(common ground, CG)에 더하는 과정. 이 경우 sentencial force는 assertion으로 정의

- **의문문(interrogative)**: 일반적으로 질문 '그에 상응하는 답변의 집합'으로 정의될 수 있기 때문에 proposition (p)의 모음, 즉 set of propositions (q)으로 표현되는데, 이 질문의 모음을 청자와 화자가 공통적으로 해답을 얻고자 하는 문제의 모음 (question set, QS)에 더하는 과정. 이 때 asking이라는 conventional force는 해당 interrogative를 QS에 더하는 과정이 됨

- **명령문(imperative)**: imperative로 표현할 수 있는 어떤 property (P)를 addressee의 to-do-list (TDL)에 더하는 과정. 좀 더 자세히, requiring이라는 conventional force가 addressee에게 부과되어야 한다는 것을 의미하며, 이것은 A를 require한다는 것(require_A)이, TDL function을 통해 imperative로 표현되는 P를 A에 관한 TDL에 더한다는 것이라고 표현할 수 있음. Imperative는 크게 세 가지의 subtype이 있는데, social authority에 기반한 order와 그렇지 않은(화자/청자가 benefit이 있는) request, 그리고 화자 자신의 TDL이 업데이트되는 permissions로 나눌 수 있음

각각을 람다 캘큘러스를 이용하여 설명하면 더 좋겠지만, 형식의미론을 깊게 들어가면 너무나 어렵더라구요. 일단 Portner가 해당 논문에서 제시한 가설들을 마저 알아보겠습니다. 제가 좋아하는 결론이기도 한데, 결과적으로 말하고자 하는 바는 

- Discourse context는, universal하게, 최소한 common ground, question set, 그리고 to-do-list를 포함하고 있음

- Generalized update function인 F = "take a set of x's and another x, and add the new x to the set" (즉, x의 모음 X와 또다른 x에 대해, X에 x를 더하는 작업) 은 universal함

- F를 제외한 다른 update function은 universal하지 않고 F가 preferred되는데, 그 이유는 F가 sentence의 force를 결정하는 데 사용될 수 있다면, 반드시 사용된다는 점에서 그러함 (이 점은 각주에서 Portner가 widening이라는 다른 update function을 이용해 exclamation을 설명한다는 점에서, 아주 완벽한 claim은 아닌 듯하긴 합니다)

이러한 내용입니다. 깊게 들어가면 훨씬 어려운 내용이지만, 일단 저는 평서문, 의문문, 그리고 명령문이 가진 성질이 각각 statement, question, command라는 illocutionary act들을 설명하는 데에 유용하게 사용될 것이라고 기대하였고, 실제 한국어 의도파악 데이터셋 구축을 하는 데에 이를 활용해볼 수 있을 것이라는 생각을 하였습니다. 즉, 위에서 본 CG와 QS, 그리고 TDL을 화행을 결정하는 기준으로 사용하면 어떨까요? 그리고, 화행의 결정 과정에서 지금까지 주로 논의되었던 illocutionary act뿐 아니라 perlocutionary act까지 고려한다면 어떻게 될까요? 이렇게 생각해 본다면, 어떤 다른 factor들을 생각해볼 수 있을 것이며, 이것보다 훨씬 더 자세하게 화행을 분류하는 기준으로는 어떤 것이 있을까요? 또 한국어라면, 다른 언어들, 특히 영어와 다른 어떤 특징을 텍스트 분류 과정에서 생각해볼 수 있을까요?

### 그 외 -  Allwood, Stolckes et al., Bunt et al.

Portner과 비슷한 견지에서, Allwood는 communicative function이라는 개념을 고려하여 좀 더 정성적으로 상기의 개념을 설명합니다. 하지만 여기서 추가적으로 고려되는 내용이 있는데, 이 과정에서, 발화 과정에서 expressive factor와 evocative factor을 함께 고려합니다. Expressive라는 것은 화자 입장에서의 attitude, 그리고 evocative라는 것은 청자로부터의 reaction을 지칭하게 됩니다. Statement와 exclamation에서는 expressive가 대체로 중시되지만, question과 request에서는 그 반대의 현상이 나타납니다.

- **서술(Statement)** - *Expressive*: Belief / *Evocative*: (that listener shares) Belief judjment 

- **질문(Question)** - *Expressive*: Desire for information / *Evocative*: (that listener provides) the desired information

- **요청(Request)** - *Expressive*: Desire for X / *Evocative*: (that listener provides) X

- **감탄(Exclamation)** - *Expressive*: Any attitude / *Evocative*: (that listener attends to attitude)

물론 여기서도, 발화 하나에서 여러 개의 act에 대한 해석이 나올 수 있다는 점은 변함이 없습니다. 하지만, Portner의 접근에서도 그리고 Allwood의 접근에서도, 이러한 네 가지 유형의 발화를 통사-의미론적, 혹은 화용론적으로 나올 수 있는 발화의 유형들로 생각한다는 것은, 이에 대한 세분화된 speech act의 정의를 추가적으로 생각할 수는 있겠지만, 이 카테고리에 속하지 않는 verbal expression들이 그렇게 많을 것이라고는 생각되지 않네요. 이는 speaker-oriented impact와 addressee-oriented impact를 모두 고려하는 Beyssade and Mandarin (2006)에서도 확인할 수 있습니다. 거기서도 exclamation은 별도의 addressee-oriented impact가 없는 독특한 문장 유형으로 등장하구요.

이쯤 되면 우리는 다시 한번, 이보다 세분화된 speech act의 구별은 어떤 것인지 생각해볼 필요가 있습니다. 가장 대표적인 것은 Switchboard 전화음성 DB의 각 script에 DASML 기반의 42개의 dialog act를 태깅한 Stolcke et al.의 연구입니다. 이 act에는 가장 많은 비율을 차지하는(36%) statement부터 19%를 차지하는 backchannel/acknowledge(uh-huh 등의 동조), 13%를 차지하는 opinion(statement보다 조금 더 주관성이 개입되는 경우) 등이 포함되며, 의외로 질문/요구의 발화는 합쳐서 10퍼센트도 안 될 정도로 큰 비율을 차지하지 못합니다. 오히려 backchennel이나 yes/no answer 등이 훨씬 많은 비중을 차지하고 있지요. 이는 해당 코퍼스가 어떤 scripted되지 않은, 자연스러운 전화 코퍼스의 전사 자료인 것에 많이 기인합니다. 실제로 우리가 일상 생활에서 대화를 하면서, 질문이나 요구의 비율이 그렇게 높지는 않습니다. 오히려 인공지능 비서나 스마트 스피커 등을 사용하면 모르겠지만요. 

이러한 불균형에도 불구하고, 각 발화의 개수는 그렇게 적지 않습니다. 이는 전체 발화가 약 20만 개이기 때문입니다. 그래도 태깅이 상당히 높은 정도의 Fleiss kappa = 0.8 이라는 주석자간 일치도를 얻었다는 사실은, guideline이 상당히 잘 만들어졌고 그만큼 정교한 typology라는 것을 의미합니다. 물론 저는 statement와 opinion의 관계, 혹은 conventional expressions를 question/command로 볼지의 여부, self-talk와 서술/감탄 등의 경계가 여전히 모호하다고 생각하지만, 그래도 적어도 영어에서는 그러한 boundary에 대해 어느정도 화자들 간의 agreement가 이루어졌다는 것을 알 수 있었습니다.

이보다 조금 더 세분화된 최근의 국제 공인(ISO) 주석 방식은 좀 더 세분화된 communicative funciton에 기반한 태깅을 제시합니다. Communicative function은 크게 4가지의 general-purpose functions와 8가지의 dimension-specific functions로 나뉘는데요, 각각은 다시 다음과 같이 세분화됩니다.

- **General-purpose functions**: 4 information-seeking functions / 6 information-providing functions / 4 commissive functions / 5 directive functions

- **Dimension-specific funcitons**: 2 auto-feedback functions / 3 allo-feedback functions / 2 time management functions / 6 turn management functions / 3 discourse structuring functions / 2 own communication management functions / 2 partner communication management functions / 10 social obligation management functions

각 세분화된 functions는 confirm, accept 등의 특정한 dialog act를 나타내고, 그 앞의 숫자는 해당하는 세분화된 act들의 수를 의미합니다. 굉장히 방대하죠. 이에 따른 taxonomy 역시 해당 논문에서 제시하고 있습니다. 이에 기반한 DIT++ 태깅 역시 제공됩니다. 다만, DASML이나 DIT++ 모두, 상세한 annotation scheme이 장점이나 실제로 그것을 행하는 것에 시간적/금전적 부담이 들어가고, 언어 전문가들이 필요하며, class가 많아 각 카테고리 당 발화의 수가 충분히 보장되지 않을 수 있다는 단점이 있습니다. 또한, 현재의 SLU 시스템들에서 그렇게 많고 자세한 발화 태깅을 필요로 하지 않을 수 있고, 영어 기반의 주석 방식이므로 한국어에 적합하지 않을 수 있으며, 더욱이 goal-oriented task에서 필요로 하는 intent와 slot-filling 문제는 좀 더 구체적인 경우들을 필요로 하게 됩니다. 

### 화행과 의도, 그리고 Intent

여태까지는 화행에 대해 설명했습니다. 화행은 speech act이고, 때로는 dialog act로 불립니다. speech act 이든 dialog act이든, 어떤 특정한 목적이 있는(goal-oriented) 것이라기보다는, 인간과 인간, 혹은 인간과 기계 사이의 대화에서, 혹은 일반적인 발화 상황에서까지 발생할 수 있는 경우들을 모두 모델링하기 위한 유형 체계로, 특정 토픽에 제한되지 않는다는 공통적인 특징이 있습니다. 하지만 헷갈리게도, 종종 Intention이라는 표현은 speech act와 혼용되곤 합니다. 좀 더 자세히는, Allen의 Analyzing Intention in Utterances에서 알 수 있듯 speech act보다는 조금 더 구체적인 어떤 의도된 결과물을 지칭하기도 하고, speech act 정도로 일반화된 개념을 지칭하는 경우도 있습니다.

이에 반해, intent라는 표현은 자연어 처리 분야, 특히 goal-oriented task에서 훨씬 많이 사용되는 표현입니다. 여기서의 '의도'는 좀 더 그 목적이 명확해요. 예컨대, '저기 있는 물건 좀 가져다 주세요'는 기본적으로 요청이지만, '심부름'이라는 intent를 가졌다고 할 수 있겠죠. 또, '내일 강변 cgv 세시 반에 겨울왕국 2 두자리 예약 부탁해요'는 비슷한 원리로 '예약'이라는 목적을 갖고 있다고 볼 수 있을 겁니다. 이러한 intent의 명명법은 물론 task에 따라 달라지게 됩니다. 이것이 스마트 비서가 아닌 검색 서비스라면, 그래서 사용자가 '지금 서울 비 오나?' 라고 묻는다면, 그 의도는 날씨에 대한 질문이 되겠지요.

이 intent의 표현은 종종 다른 term들로 대체되기도 합니다. 화행에 대한 분류 자체에도 항상 논란이 있어왔던 만큼, 엔지니어링에 좀 더 가까운 intent identification이 그 명확한 term에 대한 약속이 없는 것은 어쩌면 당연한 것 같습니다. 대기업과 빅 그룹이 사용하면 공식 term이 되는 세상이지요 ㅎㅎ 어쨌든, 일반적으로 사용되는 양상을 보자면, intent는 크게는 domain의 하위 분야이고, intent 아래에는 argument와 item이 자리잡고 있는 것으로 보입니다. 예컨대, Haghani et al. (2018)에서는 다음과 같은 구조를 보여줍니다.

- **“can you set an alarm for 2 p.m.”** : <DOMAIN><PRODUCTIVITY><INTENT><SET ALARM><DATETIME>2 p.m
  
이는, Productivity라는 domain의 발화로, Set alarm이라는 intent를 가지며, 그에 따른 item인 Datetime이 2 p.m인 문장이라는 것을 의미합니다. 여기서 intent는 Set alarm이라는 하나의 키워드로 결정되었지만, semantic role labeling에서의 argument 개념으로 본다면, set이라는 verb에 해당하는 argument로 alarm이 왔다고 볼 수 있을 것이고, set something이라는 intent로 별도로 분류할 수도 있겠지요. 이처럼 intent의 파악은 데이터셋이 구축된 방법 및 그 토픽/도메인/목적 등에 영향을 많이 받습니다. 따라서 지금까지 우리가 논의해 왔던 typology와는 좀 거리가 있습니다. 그럼에도 engineer의 관점에서는 speech act보다 훨씬 다양하게, 자세히, 그리고 산업적으로 다뤄지고 있는 분야이고, 현실에서의 활용성 또한 높습니다. 일단 당장 질문인지 요구인지 서술인지 구별하는 것도 중요하지만, 결국 하고 싶은 것은 그 발화를 통해 어떤 것을 하게 만드는가가 중요한 것 아니겠어요? 이 점이 기존의 화행 연구와 산업에서의 intent identification / slot-filling 간에 발생할 수 있는 간극이며, 화행 연구가 linguistic typology, formal semantics, context 등의 문제에서 자유롭지 못한 상황에서도 산업에서의 의도파악 연구가 활발하게 진행되고 있을 수 있는 이유이기도 합니다. 이 점은 한국어 연구에서도 마찬가지로, 한국어 화행 연구는 주로 식당/영화 예약 데이터베이스에서의 의도 파악을 기반으로 많이 진행되었고, intent 파악 연구는 현시각에도 각 기업에서 열정적으로 데이터셋을 만들고 slot-filling을 하고 있지만, 일반언어학적인 화행 논의와는 거리와 있는 것이 사실입니다. 이 과정에서, 일반언어학적인, 혹은 typological한 화행 연구가 한국어에서 철학적/화용론적인 연구를 넘어 어떤 식으로 유용될 수 있을까? 저는 이 점이 궁금했습니다.

### Revisiting perlocutionary act? 응대 혹은 비응대

앞부분의 speech act에 대한 논의를 기억하시나요? Searle은 illocutionary act를 기준으로 논의를 펼쳐갔고, perlocutionary act에 대한 연구가 활발하지 않았던 이유는 아무래도 어떤 발화에 대한 행동으로 나올 수 있는 상황이 너무 다양하기 때문이었겠지요. 하지만, 산업적인 관점에서 볼 때는, 역설적으로 청자가 취할 만한 행동들을 분석하는 것이 좀 더 인간과 기계 간의 언어 장벽을 낮춰 주는 길이 됩니다. 물론 최근에는 language model이 더욱 발전하여 문장에 대한 '이해' 없이도 대화를 물 흐르듯이 할 수 있는 (거의 튜링 테스트를 통과할 법한) open-domain dialog system들이 개발되었지만, 여전히 인간이 발화한 문장에 대한 이해 및 그에 상응하는 어떤 '행동'을 하는 것은 고전적이면서 중요한 요소이기 때문입니다.

이러한 본질적인 태스크, 즉 발화의 이해와 행동에 어려움을 미치는 부분은, 적어도 한국어에서는, 이른바 비정형 발화라 불리는 표현들입니다. 세상 모든 질문이 '~하니?'로 끝나고 모든 요청이 '~해줘'로 끝나면 얼마나 좋을까요? 하지만 일단 사람과 사람 사이의 대화만 봐도 그렇지 못하죠. 물론 인공지능이 인간이 그렇듯 context를 인지하고 사람처럼 대화하는 길은 아직도 요원하고, 대부분의 사람들이 인공지능이 청자라는 사실을 자각했을 때는 충분히 알아듣기 쉬운 언어로 발화하기는 합니다. 그럼에도 불구하고, 세상에는 인공지능을 대상으로 다양한 발화를 시도하고 싶어하는 사람들이 있고, 또한 인공지능을 위한 발화에 익숙하지 않은 사람들이 분명 있기 때문에, 범용성을 위해서라도 비정형 발화, 즉 non-canonical utterances에 대한 처리는 필수적입니다. 그렇지 않으면, 시리처럼 모르겠어요만 반복하게 될 수 있겠죠.

저는 이런 배경에서 open domain dialog에 있어, 음성이나 대화 히스토리 같은 컨텍스트가 주어지지 않는 경우에서 측 최소한의 조건만으로도, 문장의 역할을 분간해 줄 만한 가이드라인이 있으면 좋겠다는 생각이 들었습니다. 예컨대 '난 그 이번 수능 수학 6번 풀이과정이 궁금한데' 라는 발화는, 비록 문장이 충분히 끝나지 않은 fragment (혹은 full sentence의 앞 clause)이지만, 히스토리가 어떻게 되었든 무언가에 대한 질문으로 해석될 가능성이 큽니다. 물론 그렇게 해석되지 않게 대화 히스토리를 요상하게 잡을 수도 있겠지만, 굳이 그럴 필요는 없지요. 또, '야 음식물 쓰레기 갖다 버리고 오라고 몇 번을 말하냐'는 발화는, 형식상으론 평서문에 embed된 수사의문문이지만, 결론적으로는 음식물 쓰레기를 당장 갖다 버리고 오라는 의미를 가지고 있겠죠. 이처럼, 일단 중요한 것은 통사구조와 화행의 개념을 분리하는 것이고, 그 다음으로 그 문장이 청자에게 유발하는 행동을 고려하여, 최종적으로 앞의 문장은 '질문'에, 뒤의 문장은 '요구'에 가깝다고 판단하는 프로세스가 필요하다고 보았습니다.

언뜻 보기에는 간단하게 결정할 수 있을 것 같지요. 물론 통사구조가 결정이 된다면 특정 lexicon의 존재에서 가능한 화행의 범위는 제한이 되게 됩니다. 그렇지만 이것을 rule로 만들기는 쉽지가 않습니다. 우리가 생각할 수 있는 술어들, 극어(polarity item), 명사 및 명사구, 호칭어 등등을 다 모아 두고 생각해 봐도 딱 명쾌하게 나눌 수 있는 규칙이 생각나지는 않을 뿐더러, 다음 chapter에서도 설명하겠지만 한국어는 agent 생략 / wh-intervention / underspecified particles / scrambling / agglutinative morphology까지 의미-통사-형태-음성학 전반에 걸쳐 걸출하게 분석의 난점들이 도사리고 있는 언어입니다. 이것은 설령 rule을 만든다고 해도 곧바로 그것을 반박할 수 있는 예문을 만들어올 수 있을 정도로 그 구성이 자유롭고 방탕한 고맥락 언어라는 것이지요. 물론 prosody의 존재가 어느 정도 이것을 compensate해 주며, 그 부분을 제가 main 연구분야로 삼고 있긴 하지만 말입니다.

그래서 일단, 앞서 설명했던 discourse component와 communicative function의 관점에서, 발화를 크게 statement / question / command로 나누되(이 과정에서 exclamation은 statement와 사실상 같은 역할을 하는 것으로 간주), statement와 같은 역할을 할 수 있는 발화로 rhetorical question과 rhetorical command를 추가하기로 하였습니다. 여기서 말하는 S, Q, C는 모두 의미적인 부분이고 문장 형태와는 상관이 없지만, 이렇게 되면 RQ와 RC는 S와의 경계가 모호한 것이 사실입니다. 그래서, 문장의 최종적인 property(예컨대 '난 너가 대체 뭘 어떻게 하고 싸돌아댕기는 건지 궁금하다 진짜'처럼 평서문이 의문문을 안고 있고 의문문이 실제로 무언가를 묻지만 rhetorical하면서 non-directive하다면, 최종적인 property가 rhetorical question)를 보고 판단을 하는 것이 좀 더 reliable하다고 생각했습니다. 이 기준에 따르면 앞서의 문장은 각각 최종적인 property가 question인 평서문, 그리고 최종적인 property가 command인 수사의문문이 되겠지요. 수사명령문은 좀 그 개념이 와닿지 않을 수도 있지만, '두고 봐'라든지 '쏠 테면 쏴봐' 같은 발화들, 그리고 '새해 복 많이 받으세요'같은, 청자가 어떻게 행할 수 없는 기원문들의 경우가 그 예가 될 것입니다. 이런 식으로 일차적으로 다섯 가지 정도로 분류를 하고, 이 중에 Q, C를 청자가 '대응해야 할' 발화, 그리고 S, RQ, RC를 청자가 '대응하지 않아도 될' 발화로 이해한다면, 어떤 비정형 발화의 텍스트가(일단은 음성인식된 text를 가정하겠습니다) 들어왔을 때, 청자(machine)이 그에 대응해야 할지, 아니면 할 필요가 없을지를 빠르게 판단하고 그에 상응하는 행동을 취할 수 있겠죠. 일종의, 필요할 때 반응하는 지니를 만드는 것이라 할 수 있겠습니다. illocutionary와 perlocutionary acr가 적절히 섞인, 산업에 적합한 화행 체계라고 봐 주시면 될 것 같습니다. 해당 코퍼스는 기 확보된 single utterance 데이터셋에 열심히 태깅을 하고 혹은 생성하여 약 6만 문장을 모아, [3i4K](https://github.com/warnikchow/3i4k) 레포지토리에 공개되어 있습니다. 이 부분이 제가 자연어처리 태스크에 처음 매닝되고 이년 동안 한 작업이라 생각하니 뿌듯하기도 하고 아직 부족하기도 하고 ... 그렇습니다.

그런데, 지금까지 열심히 화행 및 의도파악에 대해 얘기했지만, 사실 간과하고 있는 점이 하나 있습니다. 바로 우린 텍스트 데이터에 대한 태깅을 했지, 그에 포함된, 혹은 유발할 수 있는 음성학적 특징들에 대해서는 전혀 언급하지 않았다는 것입니다. 물론 앞에서 사용한 예문들은 모두, 말할 만한 억양이 대충 예상이 되고, 글로 읽어도 전혀 중의성이 없습니다. 하지만 다음의 발화는 어떨까요?

- **이번에 어디 갔다 왔어**

- **벌써 열두 신데 그만 좀 자라**

- **너랑 있을 때 만큼은 기분이 좋지 않았어**

의문사의 존재양화사화부터 억양 및 장단에 따른 통사중의성까지, prosody 없이 해결할 수 없는 의도 파악 문제는 세상에 너무나도 많습니다. NLP의 관점에서, 우린 이에 대해 어떤 해결책을 제시할 수 있을까요? 또 실제로 음성을 접할 수 있다면 어떤 추가적인 조치를 취할 수 있을까요?

## Syntactic Ambiguity Resolution

## Sentence Similarity

## Argument Extraction

