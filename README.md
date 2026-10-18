# 🕸️ 스파이더멘 웹스윙 3D

**🔗 바로 실행해 보기:** https://spider-bci2b8yun47s4nhgkexcds.streamlit.app

스파이더맨처럼 거미줄을 쏘면서 도시를 날아다니는 게임을 직접 만들어 보고 싶어서 시작한 브라우저 3D 게임입니다.
HTML 파일 하나에 Three.js로 도시·물리·전투를 모두 넣었고, 설치 없이 링크만 누르면 바로 플레이할 수 있게 했습니다.
웹스윙의 손맛을 내는 게 생각보다 훨씬 어려워서, 직접 플레이해 보며 고친 문제들을 9장에 전부 남겼습니다.

▶ **[여기를 눌러서 바로 플레이하기](https://skn35shimsungwook.github.io/spider/)**

---

## 1. 이 게임이 뭐예요? 🕷️

밤이 된 네온사인 도시에서, 여러분은 스파이더맨이 되어서:

- **손목에서 거미줄을 쏴서** 건물과 건물 사이를 그네 타듯이 날아다니고 (이걸 "웹스윙"이라고 불러요)
- **건물 벽에 부딪히면** 그대로 벽을 타고 올라가고
- **가끔 땅에 내려오면** 나쁜 사람(총잡이나 검객)이 나타나서 **싸움**이 벌어져요

싸울 때는 게임 속 스파이더맨이 원작처럼 **"위험을 미리 느끼는 감각"(스파이더 센스)** 도 가지고 있어요.
적이 공격하기 직전에 화면이 빨갛게 번쩍이는데, 그때 재빨리 피하면(회피) 안 맞아요!

## 2. 어떻게 플레이해요? 🎮

| 키 | 뭘 하나요? |
|---|---|
| **W** | 걷기 (건물 옥상 위에서) |
| **A / D** | 고개 돌려서 거미줄 쏠 방향 조준하기 |
| **스페이스바 또는 마우스 클릭** | 거미줄 발사! (조준한 곳에 아무것도 없으면 그냥 뛰어내려요) |
| **스윙 중 A / D** | 그네처럼 흔들릴 때 커브 그리기 |
| **Shift** | "웹지퍼" — 가까운 곳으로 순간 휙 날아가기 |
| **싸움이 시작됐을 때 WASD** | 자유롭게 이리저리 움직이기 |
| **F** | 주먹으로 펀치! |
| **싸움 중 클릭/스페이스** | 거미줄로 원거리 공격 |
| **적이 빨갛게 번쩍일 때 Shift** | 회피하기 (스파이더 센스!) |

목표는 딱 하나예요: **최대한 멀리, 안 죽고 날아가기.** 거리가 늘어날수록 점수가 올라가고, 250m마다 "체크포인트!"가 뜨고, 1000m를 넘으면 "미션 클리어!"가 나와요.

## 3. 이 게임은 어떻게 만들어졌을까요? 🛠️ (기술 스택, 쉽게 설명)

이 게임은 **딱 파일 하나(`index.html`)** 로 되어 있어요. 마치 레고 블록 하나에 게임 전체가 다 들어있는 것과 비슷해요! 설치 프로그램도 필요 없고, 그냥 인터넷 브라우저만 있으면 돌아가요.

그 안에 어떤 "재료"들이 들어갔는지 하나씩 설명해드릴게요:

- **HTML / JavaScript** — 이 게임이 사는 "집"이에요. HTML은 집의 뼈대(화면에 뭘 보여줄지)를 만들고, JavaScript는 그 안에서 실제로 게임이 움직이게 만드는 "심장"이에요. 캐릭터가 움직이고, 점수가 올라가고, 적이 공격하는 것 전부 JavaScript가 계산해요.

- **Three.js** — 컴퓨터한테 "이 자리에 건물을 세워줘", "여기엔 사람 모양을 그려줘" 라고 3D 그림을 쉽게 그리도록 도와주는 도구예요. 화가한테 붓을 쥐여주는 것과 비슷해요. 이게 없으면 3D 그래픽을 훨씬 더 어렵게, 직접 다 만들어야 해요.

- **WebGL** — Three.js가 그림을 그릴 때, 실제로 그 그림을 컴퓨터의 그래픽카드로 아주 빠르게(1초에 60번씩!) 그려주는 기술이에요. 이 덕분에 게임 화면이 뚝뚝 끊기지 않고 부드럽게 움직여요.

- **물리 계산 (직접 만든 "진자 운동" 공식)** — 거미줄을 쏘면 왜 진짜 그네처럼 흔들릴까요? 이건 실제 그네가 움직이는 물리 법칙(진자 운동)을 코드로 직접 계산해서 만든 거예요. 매 순간마다 "지금 얼마나 빠르게, 어느 방향으로 움직여야 하는지"를 다시 계산해서 진짜처럼 보이게 만들었어요.

- **3D 캐릭터 모델 + 뼈대 애니메이션 (GLTF)** — 주인공과 악당이 진짜 사람처럼 걷고 뛰는 건, 사람 뼈대 모양의 3D 모델 파일(GLTF)을 불러와서 쓰기 때문이에요. 종이 인형에 관절을 만들어서 움직이는 것처럼, 이 모델도 어깨·팔꿈치·무릎 같은 "뼈"가 있어서 자연스럽게 움직여요.

- **후처리 효과 - 블룸(Bloom)** — 창문 불빛이나 표적이 네온사인처럼 몽글몽글 빛나 보이는 효과예요. 그림을 다 그린 다음에 "여기 밝은 부분은 좀 더 은은하게 번지게 해줘"라고 한 번 더 손보는 기술이에요.

- **실시간 그림자** — 캐릭터가 서 있는 자리에 그림자가 생기는 것도 계산으로 만든 거예요. 태양(이 게임에서는 달빛)이 어느 방향에서 비추는지 계산해서, 그 반대쪽에 그림자를 그려줘요.

- **Web Audio API** — 효과음(웹 쏘는 소리, 타격 소리 등)을 미리 녹음된 파일 없이, 코드로 그 자리에서 즉석으로 "만들어서" 재생하는 기술이에요.

정리하면: **Three.js + WebGL로 3D 그림을 그리고, 직접 짠 물리 공식으로 움직임을 계산하고, 사람 모양 3D 모델로 캐릭터를 표현한 다음, 블룸·그림자 같은 효과로 예쁘게 꾸민** 브라우저 게임이에요.

## 4. 다른 방법으로도 플레이할 수 있어요

이 게임은 **Streamlit**(파이썬으로 웹앱을 쉽게 만드는 도구)에도 그대로 넣어서 배포할 수 있게 만들어 놨어요. 게임 자체는 여전히 브라우저 안의 JavaScript로 돌아가고, Streamlit은 그 게임을 감싸는 "액자" 역할만 해요. 코드는 이 저장소의 [`streamlit/`](./streamlit) 폴더에 있어요.

```bash
cd streamlit
pip install -r requirements.txt
streamlit run main.py
```

## 5. 어디서 실행돼요?

- 그냥 `index.html` 파일을 더블클릭해도 돼요 (인터넷 없어도 됨!).
- 아니면 위에 있는 [플레이 링크](https://skn35shimsungwook.github.io/spider/)를 눌러도 돼요.
- 파이썬/Streamlit으로 실행하고 싶으면 [`streamlit/`](./streamlit) 폴더를 보세요.

---

## 6. 파일 구조

```
spider/
├── index.html            # 게임 전체 (HTML+CSS+JS 한 파일, GitHub Pages가 이걸 그대로 서빙함)
├── streamlit/
│   ├── main.py            # Streamlit 페이지 (게임을 iframe으로 감싸기만 함)
│   ├── game.html          # index.html과 100% 동일한 게임 본체 (복사본)
│   └── requirements.txt   # streamlit 패키지 하나
└── README.md               # 지금 읽고 있는 이 파일
```

게임 로직이 있는 파일은 사실상 `index.html` 딱 하나예요. `streamlit/game.html`은 그걸 그대로 복사해 둔 것뿐이라, **실제 게임 코드를 고치고 싶으면 `index.html`만 보면 돼요.**

## 7. `index.html` 내부는 어떻게 짜여 있나요?

한 파일이지만 아무렇게나 섞여있지 않고, 위에서 아래로 이런 순서로 정리돼 있어요:

```
<head>
  <style>  ...HUD·시작화면·일시정지·격투 UI·체크포인트 토스트 CSS...  </style>
</head>
<body>
  <div id="stage"> ... 점수판, 크로스헤어, 체력바 같은 DOM 오버레이 요소들 ... </div>
  <canvas id="game"></canvas>          ← Three.js가 실제로 3D를 그리는 캔버스

  <script src="three.min.js"></script>          ← 3D 엔진 본체
  <script src="GLTFLoader.js"></script>          ← 3D 캐릭터 모델 불러오는 도구
  <script src="SkeletonUtils.js"></script>       ← 캐릭터 모델을 복제하는 도구(빌런용)
  <script src="EffectComposer / RenderPass / ShaderPass / UnrealBloomPass"></script>  ← 블룸 효과 도구 4종

  <script>
    (function(){
      // 실제 게임 코드 전체가 여기, 하나의 즉시실행함수(IIFE) 안에 들어있어요.
      // (바깥으로 변수가 새어나가지 않게 감싸는 상자라고 생각하면 돼요)
    })();
  </script>
</body>
```

`<script>` 안의 코드는 다시 아래처럼 역할별 구역으로 나뉘어 있어요 (괄호 안은 실제 줄 번호):

| 구역 | 줄 번호 | 뭘 하는 곳인가요? |
|---|---|---|
| DOM 참조 모으기 | 223–255 | HTML에 있는 점수판·체력바 같은 요소들을 JS 변수로 붙잡아 둠 |
| 렌더러 / 씬 / 카메라 / 후처리 | 265–335 | 3D 세계를 그릴 준비 (렌더러, 조명, 블룸, 그림자 설정) |
| 배경 꾸미기 | 341–413 | 달, 노을빛 지평선, 도로 텍스처, 바닥 |
| 오브젝트 풀 (건물·앵커·픽업) | 446–520 | 건물/앵커/아이템 3D 모델을 미리 만들어두는 곳 |
| 자동차 · 보행자 | 521–560 | 길거리 배경 장식 |
| 플레이어 캐릭터 | 561–658 | 주인공 몸(관절 인형) 만들기 |
| 빌런(적) 캐릭터 | 659–795 | 적 몸 만들기 + 등장/퇴장/데미지 처리 |
| 3D 사람 모델 불러오기 | 796–879 | 진짜 사람 모델(GLTF)을 인터넷에서 받아와서 주인공/빌런에 입히기 |
| 게임 상태값 · 상수 | 880–902 | 중력, 속도, 점수 같은 게임 전체 설정값들 |
| `resetGame()` | 903–957 | "새 게임 시작" 버튼을 누르면 모든 걸 처음 상태로 되돌리는 함수 |
| 도시 생성 | 958–1138 | 건물이 계속 새로 생기고, 지나간 건물은 치워지는 로직 (무한 도시) |
| 입력 처리 | 1139–1308 | 조준, 거미줄 발사, 마우스/키보드 입력 |
| 오디오 | 1309–1372 | 효과음/바람소리를 코드로 즉석 생성 |
| 거미줄 그리기 | 1373–1421 | 거미줄이 살짝 처지게(중력에 눌린 것처럼) 그리는 곡선 계산 |
| 충돌 처리 | 1422–1541 | 건물에 부딪혔을 때 무슨 일이 일어날지 결정 |
| **`update(dt)`** | 1542–1846 | **게임의 심장 — 매 프레임마다 물리·상태를 계산하는 가장 중요한 함수** |
| **`updateVisuals(dt)`** | 1847–2121 | **카메라, 캐릭터 자세, HUD를 화면에 실제로 반영하는 함수** |
| 메인 루프 | 2122–끝 | `update` → `updateVisuals` → 화면 그리기를 무한 반복 |

## 8. 핵심 시스템 하나하나 상세 설명

### 8-1. 오브젝트 풀링 (건물·앵커·자동차 등)

건물이 필요할 때마다 새로 만들고, 안 보이면 완전히 삭제하면 컴퓨터가 버벅여요. 그래서 이 게임은
**"미리 60개 정도 만들어두고, 화면에 안 보이면 숨겼다가, 다시 필요할 때 재활용"** 하는 방식을 써요.
장난감 상자에서 안 쓰는 블록을 꺼내 재배치하는 것과 비슷해요. `buildingPool`, `anchorPool`, `carPool`,
`pedestrianPool` 이 전부 이 방식이에요.

### 8-2. 무한 도시 생성 (`spawnRow`, `seedCity`, `pruneAndGrow`)

이 게임은 끝이 없는 도시를 달리는 게임이라, 도시를 통째로 미리 만들어둘 수 없어요. 그래서:

- 플레이어 앞쪽으로 420유닛 정도까지는 항상 건물이 채워져 있도록 계속 새로 만들고 (`seedCity`, `pruneAndGrow`)
- 플레이어가 지나쳐서 뒤로 멀어진 건물은 다시 풀(pool)로 돌려보내요

즉 "카메라가 보는 범위만 실제로 존재하는 것처럼" 착각하게 만드는 트릭이에요.

### 8-3. 웹스윙 물리 (`update(dt)` 안의 `swinging` 상태)

거미줄에 매달려 흔들리는 움직임은 **진자 운동**을 직접 코드로 계산해서 만들었어요. 매 프레임을
다시 4번 잘게 쪼개서(서브스텝) 이렇게 계산해요:

1. 중력과 조작(A/D 커브)만큼 속도를 살짝 바꾼다
2. 그 속도로 위치를 이동시킨다
3. "어? 거미줄 길이보다 앵커에서 더 멀어졌네?" → 위치를 거미줄 길이에 딱 맞게 다시 당겨온다
4. 거미줄이 당기는 방향(반지름 방향)의 속도 성분만 제거한다 (거미줄과 나란한 속도는 유지)

이걸 한 프레임에 4번 반복하면, 실제 그네처럼 자연스럽게 흔들리는 움직임이 나와요.

### 8-4. 플레이어 상태 머신

주인공은 항상 다음 중 딱 하나의 "모드"예요. `update(dt)` 함수가 매 프레임마다 지금 모드에 맞는
로직만 실행해요:

- **`grounded`** (건물 옥상 위, 또는 거리) — 서서 조준하거나 달리기
- **`falling`** — 공중에 떠서 자유낙하 중 (이때 거미줄을 쏠 수 있음)
- **`swinging`** — 거미줄에 매달려 흔들리는 중
- **`wallrun`** — 건물 옆면에 부딪혀서 그대로 벽을 타고 오르는 중
- **`combat`** — 거리에 착지해서 빌런과 싸우는 중

### 8-5. 건물 충돌 처리 (`resolveBuildingHit`)

건물에 부딪히면 딱 하나의 결과만 나오는 게 아니라, 상황에 따라 갈려요:

- 건물 **꼭대기보다 높이** 있으면서 떨어지는 중이었다면 → 옥상에 **착지**
- 옆면에 부딪혔는데 **위쪽으로 벽이 충분히 남아있으면** → **벽타기** 시작
- 스윙 중에 살짝 스치기만 했다면 → 거미줄은 유지한 채 살짝 튕겨내기만 함 (스윙이 끊기지 않게)

### 8-6. 빌런(적) 시스템

거리에 착지하면 **항상** 싸움이 걸리는 게 아니라, 마지막 전투 이후 **일정 거리 이상 이동했고 +
확률적으로**(대략 4번 착지에 1번꼴) 빌런이 나타나요. 빌런은 두 종류(총잡이/검객)이고, 셋 중 하나의
상태를 오가요:

- **`approach`** — 플레이어에게 다가오기 (또는 총잡이는 일정 거리를 유지)
- **`telegraph`** — 공격 직전 예고 (화면에 빨간 경고선이 뜨고, 이 타이밍에 회피 가능 = 스파이더 센스)
- **`recover`** — 공격 후 잠깐의 딜레이

### 8-7. 3D 캐릭터 (프로시저럴 리그 → GLTF 업그레이드)

처음엔 원기둥·구슬 같은 간단한 도형을 이어붙인 **관절 인형**으로 주인공을 만들어요(인터넷이 느려도
게임이 안 멈추게 하기 위한 기본값). 그 다음 인터넷에서 진짜 사람 3D 모델(`Xbot.glb`)을 백그라운드로
받아오는데, **7초 안에 도착하면** 그 모델로 몰래 갈아끼우고, **너무 오래 걸리면** 그냥 관절 인형으로
계속 진행해요. 빌런도 이 사람 모델을 "복제"(`SkeletonUtils.clone`)해서 보라색으로 색만 바꿔 써요 —
그래서 둘 다 사람처럼 자연스럽게 걷고 뛰어요.

### 8-8. 카메라

카메라는 그냥 플레이어 뒤를 졸졸 따라다니는 게 아니라, 여러 가지를 계산해요:

- 스윙 중엔 흔들리는 방향 바깥쪽으로 살짝 기울어져서(원심력 느낌) 박진감을 더함
- 건물이 시야를 가로막을 것 같으면 카메라를 플레이어 쪽으로 미리 당겨서 벽 뚫림을 방지
- 격투 중엔 카메라를 옆으로 살짝 빼서(어깨너머 시점) 주인공 몸이 적을 가리지 않게 함

### 8-9. 오디오

효과음 파일을 따로 두지 않고, **Web Audio API로 그 자리에서 소리를 직접 합성**해요. 예를 들어
거미줄 쏘는 소리는 주파수가 빠르게 떨어지는 파형을 코드로 만들어서 재생하는 식이에요.

---

## 9. 만들면서 겪은 문제 (전부)

직접 플레이하면서 부딪힌 문제를, **어떤 코드가 왜 잘못됐고 어떻게 고쳤는지** 코드 위주로 하나도 빼지 않고 적어 둡니다.

### 9-1. 실행 환경 관련

**① `file://`로 열면 3D 엔진이 아예 로드 안 됨**

원인: ES 모듈(`import`) 방식으로 Three.js를 불러왔는데, 브라우저가 `file://`에서 여는 페이지의
모듈 스크립트를 CORS 정책으로 막아 버렸습니다.

```html
<!-- Before: 모듈 방식 — file://에서 CORS 에러로 막힘 -->
<script type="module">
  import * as THREE from 'https://unpkg.com/three@0.160.0/build/three.module.js';
</script>

<!-- After: 클래식 스크립트 — 대신 클래식 빌드가 있는 r140으로 버전 고정 -->
<script src="https://cdn.jsdelivr.net/npm/three@0.140.0/build/three.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/three@0.140.0/examples/js/loaders/GLTFLoader.js"></script>
```

**② 재시작할 때 카메라가 한두 프레임 벽 속에 파묻힌 것처럼 보임**

원인: 카메라는 매 프레임 `lerp`(목표 위치로 서서히 다가가기)로만 움직이는데, `resetGame()`은
카메라 위치를 건드리지 않아서 지난 판이 끝난 자리(주로 벽 안)에서부터 다시 서서히 다가왔습니다.

```js
// resetGame() 안, Before: 카메라 위치를 아예 안 건드림
camYaw = 0; camPitchLerp = 0;
// (카메라는 다음 updateVisuals()의 lerp가 알아서 따라잡겠거니 방치)

// After: 새 판 시작 위치로 즉시 스냅
camYaw = 0; camPitchLerp = 0;
camera.position.set(player.x, player.y + 5.4, player.z + 13.5);
camera.lookAt(player.x, player.y + 1.6, player.z - 6);
```

**③ 미리보기 창 크기가 순간적으로 0이 되면 화면이 깨짐 (`Framebuffer is incomplete` 콘솔 에러)**

원인: 블룸 후처리(`EffectComposer`)가 화면 크기에 맞춰 렌더 타겟을 만드는데, 크기 조절 함수가
가로/세로 값을 검증 없이 그대로 넘겨서, 순간적으로 0이 들어오면 크기 0짜리 렌더 타겟이
만들어지고 그 뒤로 계속 깨진 채 남았습니다.

```js
// Before
function resize(){
  const w = stage.clientWidth, h = stage.clientHeight;
  renderer.setSize(w,h,false);
  composer.setSize(w,h);
  ...
}

// After: 0 이하 크기는 그냥 무시
function resize(){
  const w = stage.clientWidth, h = stage.clientHeight;
  if (w < 1 || h < 1) return;
  renderer.setSize(w,h,false);
  composer.setSize(w,h);
  ...
}
```

### 9-2. 조작/입력 관련

**④ 시작하자마자 실수로 더블클릭하면 바로 다이빙해버림**

원인: 마우스 down 이벤트 하나로 "게임 시작"과 "거미줄 발사"를 둘 다 처리해서, 시작 클릭 직후
손이 안 떨어져 생기는 추가 클릭까지 "발사" 시도로 인식했습니다.

```js
// Before
function onDown(){
  if (paused) return;
  if (state !== 'playing'){ startOrRestart(); return; }
  attachHeld = true;
  tryAttach();
}

// After: 시작 후 0.5초는 무시
let gameStartAt = 0; // startOrRestart()에서 performance.now()로 기록됨
function onDown(){
  if (paused) return;
  if (state !== 'playing'){ startOrRestart(); return; }
  if (performance.now() - gameStartAt < 500) return;
  attachHeld = true;
  tryAttach();
}
```

**⑤ 걷기가 W를 계속 누르고 있어야만 됨 → 너무 불편함**

원인: `keydown`에서 `keys.forward = true`만 켜고, 실제 이동 로직은 그 값이 `true`인 매 프레임에만
전진시켜서 손을 떼는 순간 멈춰버렸습니다.

```js
// keydown 핸들러, Before
else if (e.code === 'KeyW'){ keys.forward = true; }

// After: 서 있는 상태에서 한 번 누르면 "계속 걷기" 상태를 따로 켜둠
else if (e.code === 'KeyW'){
  keys.forward = true;
  if (player && player.mode === 'grounded' && !player.hasLaunched) player.autoWalk = true;
}

// 이동 로직도 keys.forward뿐 아니라 autoWalk도 같이 확인
if (keys.forward || player.autoWalk){ /* 전진 */ }
```

### 9-3. 웹스윙 물리 버그

**⑥ 스윙을 오래 붙잡고 있으면 앵커 바로 밑에서 완전히 멈춰버리고 다시는 안 움직임**

원인: 진자 물리를 "위치를 구속 조건에 맞게 강제로 당겨오는" 방식(포지션 기반 다이내믹스)으로
계산하는데, 이 방식은 매 프레임 아주 조금씩 에너지를 깎아먹는 특성이 있어서 오래 매달려 있으면
속도가 0으로 수렴했습니다.

```js
// 1차 해결(과했음): 속도가 낮으면 즉시 릴리즈
const swingSpd = Math.hypot(player.vx, player.vy, player.vz);
if (swingSpd < 9) releaseWeb();
// → 정상적인 스윙도 호(arc) 꼭대기에서 잠깐 느려지는 순간마다 놓여버림

// 최종 해결: "매달린 지 0.4초 이후" + "느린 상태가 0.5초 지속"일 때만 릴리즈
if (player.swingT > 0.4 && swingSpd < 4){
  player.swingLowT += dt;
} else {
  player.swingLowT = 0;
}
player.swingT += dt;
if (player.swingLowT > 0.5){
  releaseWeb();
  player.vz = Math.min(player.vz, -14);
}
```

**⑦ 스윙 도중 건물을 살짝 스치기만 해도 무조건 추락으로 바뀜**

원인: `resolveBuildingHit(b)`가 함수 맨 위에서 **무조건** `player.mode = 'falling'`부터 실행한
뒤에야 착지/벽타기 같은 세부 분기로 들어갔음. 건물 간격을 좁힌 뒤로 스윙 궤적이 모서리에
스치는 일이 잦아지면서, 사실상 스윙할 때마다 이 무조건 분기에 걸려버렸습니다.

```js
// Before
function resolveBuildingHit(b){
  player.mode = 'falling';   // 무조건 실행됨 — 스윙 중 살짝 스쳐도 예외 없음
  player.anchor = null;
  // ...이후 착지/벽타기 분기...
}

// After: 스윙 중 가벼운 접촉은 거미줄 유지한 채 튕겨내기만 함
function resolveBuildingHit(b){
  const wasSwinging = player.mode === 'swinging';
  // ...
  if (wasSwinging && !(speed > 24 && b.h - player.y > 4)){
    // 위치만 밀어내고 속도를 살짝 반사 — mode, anchor는 그대로 유지
    if (penX < penZ) player.x = b.x + Math.sign(dx||1) * (hx+0.05);
    else player.z = b.z + Math.sign(dz||1) * (hz+0.05);
    return;
  }
  player.mode = 'falling';   // 정면으로 빠르게 부딪힌 경우만 여기로
  player.anchor = null;
  // ...
}
```

### 9-4. 건물·도시 생성 버그

**⑧ 걸어가다가 갑자기 발밑 건물이 사라져서 그대로 추락**

원인: 지나간 건물을 치우는 `pruneAndGrow()`가 건물의 **중심 z좌표**만 보고 판단하는데, 시작
건물이 78×78로 커서 그 위를 걷는 도중에도 중심 기준으로는 이미 "지나간 것"으로 계산됐습니다.

```js
// Before
function pruneAndGrow(){
  const behindZ = player.z + 30;
  for (const b of buildingPool){
    if (b.active && b.z > behindZ){ b.active = false; /* ... */ }
  }
}

// After: 지금 서 있는 건물은 절대 치우지 않음
function pruneAndGrow(){
  const behindZ = player.z + 30;
  for (const b of buildingPool){
    if (b.active && b !== player.groundB && b.z > behindZ){ b.active = false; /* ... */ }
  }
}
```

**⑨ 건물이 너무 뜸하게 배치되거나, 반대로 너무 빽빽해서 부딪히기만 함**

원인: 건물 간격을 좁힌 뒤 충돌이 잦아져서 빈 칸 확률을 34% → 46%로 올렸는데(위 ⑦번이 아직
안 고쳐진 상태였습니다), 이번엔 "너무 휑하다"는 문제로 바뀌었습니다.

```js
// 1차 (충돌이 무서워서 건물을 줄임)
const skip = (i === forceOpenIdx) || Math.random() < 0.46;

// 최종 (⑦번을 먼저 고쳐서 그레이즈가 안전해졌으니 다시 촘촘하게)
const skip = (i === forceOpenIdx) || Math.random() < 0.28;
```

**⑩ 랜드마크(첨탑) 건물이 원래 모양으로 안 돌아옴**

원인: 건물 모양을 박스 + 8각 타워로 다양화했는데, 첨탑 건물 교체 로직이 "첨탑이 아니면
무조건 박스로" 하드코딩되어 있어서 8각 타워였던 건물도 박스로 바뀌어버렸습니다.

```js
// Before
slot.cap.geometry = landmark ? SPIRE_GEO : BOX_GEO;

// After: 그 건물 풀 슬롯이 원래 갖고 있던 모양(baseGeo)으로 되돌림
slot.cap.geometry = landmark ? SPIRE_GEO : slot.baseGeo;
```

### 9-5. 벽타기 / 거리 착지 버그

**⑪ 거리에 착지한 뒤엔 건물에 부딪혀도 벽타기가 전혀 안 됨**

원인: 건물 충돌 검사 자체가 `player.mode !== 'grounded'`일 때만 실행되도록 되어 있었는데,
전투가 끝나고 거리를 달릴 때도 모드가 정확히 `grounded`라서 검사 자체가 스킵됐습니다.

```js
// Before
if (player.invulnT <= 0 && player.mode !== 'wallrun' && player.mode !== 'grounded'){
  const hitB = findBuildingHit(player.x, player.y, player.z, PLAYER_R*0.55);
  if (hitB) resolveBuildingHit(hitB);
}

// After: "옥상 위(자기 건물)"일 때만 스킵, 거리를 달릴 때는 검사함
const onOwnRoof = player.mode === 'grounded' && !!player.groundB;
if (player.invulnT <= 0 && player.mode !== 'wallrun' && player.mode !== 'combat' && !onOwnRoof){
  const hitB = findBuildingHit(player.x, player.y, player.z, PLAYER_R*0.55);
  if (hitB) resolveBuildingHit(hitB);
}
```

### 9-6. 전투 시스템 버그 · 밸런스

**⑫ 전투 카메라가 플레이어 뒤에서 적을 향해 일직선으로 봐서, 화면에서 둘이 완전히 겹쳐 보임**

원인: 전투 중 카메라의 목표 위치가 "플레이어 정후방"으로만 계산되어서, 카메라가 적을 향해
회전할 때 플레이어 캐릭터 자체가 적 앞을 가리는 구도가 나왔습니다.

```js
// After: 전투 중엔 카메라를 옆으로(어깨너머 시점) 밀어냄
if (inCombat){
  const rightX = Math.cos(camYaw), rightZ = Math.sin(camYaw);
  desired.x += rightX * 5.5;
  desired.z += rightZ * 5.5;
  desired.y += 1.6;
}
```

**⑬ 전투 중 WASD 이동 방향이 화면과 안 맞음**

원인: 카메라는 계속 적을 향해 자동 회전하는데, 이동 계산은 회전과 무관한 고정 월드축을
그대로 썼습니다(D키 = 항상 +X 방향).

```js
// Before: 월드 고정 축
if (keys.left) mx -= 1;
if (keys.right) mx += 1;
if (keys.forward) mz -= 1;
if (keys.back) mz += 1;
player.vx = (mx/mlen)*moveSpeed;
player.vz = (mz/mlen)*moveSpeed;

// After: 지금 카메라가 보는 방향(camYaw) 기준으로 회전시켜서 적용
const fwdInput = -mz, rightInput = mx;
const wx = rightInput*Math.cos(camYaw) + fwdInput*Math.sin(camYaw);
const wz = rightInput*Math.sin(camYaw) - fwdInput*Math.cos(camYaw);
player.vx = (wx/wl)*moveSpeed;
player.vz = (wz/wl)*moveSpeed;
```

**⑭ 첫 전투에서 반응할 틈도 없이 바로 맞고 순식간에 죽음**

```js
// Before
villain.stateT = villain.type === 'gun' ? 0.55 : 0.42;   // 예고 시간
player.hp -= villain.type === 'gun' ? 18 : 26;            // 데미지
player.invulnT = 0.3;                                      // 착지 직후 무적

// After
villain.stateT = villain.type === 'gun' ? 0.7 : 0.58;
player.hp -= villain.type === 'gun' ? 13 : 19;
player.invulnT = 0.8;
```

**⑮ 거리에 착지할 때마다 무조건 전투가 걸려서 웹스윙의 흐름이 계속 끊김**

```js
// Before: 착지하면 100% 전투
if (player.y <= PLAYER_R){
  player.mode = 'combat';
  spawnVillain();
}

// After: 마지막 전투 이후 55유닛 이상 이동 + 45% 확률일 때만
if (player.y <= PLAYER_R){
  player.mode = 'grounded';   // 기본은 그냥 안전하게 착지
  const progressedSince = lastVillainZ - player.z;
  if (progressedSince > 55 && Math.random() < 0.45){
    player.mode = 'combat';
    lastVillainZ = player.z;
    spawnVillain();
  }
}
```

**⑯ 적이 도형 몇 개를 이어붙인 것처럼 너무 단순하게 생김**

```js
// Before: 원기둥+구+캡슐 조립
function makeVillainMesh(){
  const torso = new THREE.Mesh(new THREE.CylinderGeometry(0.46,0.38,1.05,10), mat);
  const head  = new THREE.Mesh(new THREE.SphereGeometry(0.4,16,16), skinMat);
  // ...팔다리도 캡슐...
}

// After: 주인공과 같은 GLTF 사람 모델을 스켈레톤째로 복제
const villainModel = THREE.SkeletonUtils.clone(gltf.scene);
villainModel.traverse(o => {
  if (o.isMesh && o.material){
    o.material = o.material.clone();
    o.material.color.set(0x5a1fb0);   // 보라색으로만 구분
  }
});
villainGltfMixer = new THREE.AnimationMixer(villainModel);
for (const clip of gltf.animations) villainGltfActions[clip.name] = villainGltfMixer.clipAction(clip);
```

### 9-7. 그래픽 회귀

**⑰ 블룸(빛 번짐) 효과를 넣었더니 지붕 같은 큰 밝은 면에서 화면 전체가 하얗게 날아가 버림**

```js
// Before: 작은 광원 기준으로 맞춘 값이 큰 밝은 면(옥상)에도 그대로 적용되어 과다 노출
const bloomPass = new THREE.UnrealBloomPass(
  new THREE.Vector2(w, h), 0.85, 0.55, 0.72   // strength, radius, threshold
);

// After: 임계값(threshold)을 올리고 세기/범위를 낮춰서 작은 광원만 반응
const bloomPass = new THREE.UnrealBloomPass(
  new THREE.Vector2(w, h), 0.45, 0.35, 0.92
);
```

### 9-8. 테스트 과정에서 발견한 "게임 버그는 아니지만" 특이사항

이건 실제 게임의 결함이 아니라, **개발 중 사용한 자동화 브라우저 테스트 도구 자체의 특성**입니다.
혹시 비슷한 걸로 헷갈리실까봐 구분해서 남겨둡니다.

- 이 프로젝트를 검증할 때 쓴 샌드박스 브라우저 도구는, 화면 캡처를 하지 않으면 애니메이션
  프레임이 잘 안 넘어가는 특성이 있었습니다. (실제 사용자 브라우저에서는 해당 없음)
- 같은 도구의 "클릭" 명령이 두 번째 클릭부터 간헐적으로 씹히는 현상이 있었는데, 직접 브라우저
  이벤트를 발생시켜보면 항상 정상 동작해서 **게임 코드의 문제가 아니라 테스트 도구의 특성**으로
  결론지었습니다.
- 미리보기 창을 열면 오디오 활성화용으로 추정되는 클릭이 자동으로 한 번 발생하는데, 이게
  마우스를 누르기만 하고 떼지 않는 것처럼 동작해서 의도치 않게 게임이 자동으로 진행되는 것처럼
  보인 적도 있었습니다.

---

🤖 제가 직접 플레이하며 방향을 정하고, 구현은 Claude Code와 같이 했습니다.
