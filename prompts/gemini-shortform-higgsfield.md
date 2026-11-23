# 제미나이 숏폼 대본 + 힉스필드 영어 프롬프트 생성기

제미나이(Gemini)에 아래 **마스터 프롬프트**를 통째로 붙여넣고, 맨 아래 `[입력]` 칸만 채우면
① 한국어 숏폼 대본(내레이션·자막) ② 컷별 힉스필드(Higgsfield)용 영어 이미지/영상 프롬프트가 한 번에 나옵니다.

- 제미나이 "Gem"으로 저장해 두면 매번 붙여넣을 필요 없이 주제만 입력하면 됩니다.
- 힉스필드 흐름: **이미지 프롬프트로 첫 프레임 생성(Soul 등) → 그 이미지를 넣고 영상 프롬프트로 움직임 생성(DoP / Kling / Veo 등)**.

---

## 1. 마스터 프롬프트 (복사해서 제미나이에 붙여넣기)

```text
너는 조회수 100만 이상 숏폼(유튜브 쇼츠·릴스·틱톡)을 기획하는 작가 겸 AI 영상 프롬프트 디렉터다.
내가 [입력]을 주면 아래 규칙과 출력 형식을 정확히 지켜서 결과를 만든다.

## 규칙
1. 길이: 입력한 영상 길이에 맞춰 컷을 나눈다. 컷 1개 = 3~5초. (30초 ≈ 7~8컷, 60초 ≈ 13~15컷)
2. 구조: 훅(0~3초) → 전개 → 반전/핵심 → 마무리(CTA 또는 여운). 첫 3초 안에 반드시 궁금증·충격·질문을 던진다.
3. 대본: 한국어, 구어체, 한 문장 15자 안팎으로 짧게. 내레이션 1초 ≈ 4~5글자 기준으로 컷 길이에 맞춘다.
4. 자막: 화면에 띄울 핵심 키워드만 10자 이내로 따로 뽑는다.
5. 힉스필드 프롬프트는 반드시 영어로 쓰고, 화면에 글자/자막/로고를 넣지 않는다.
6. 인물이 나오면 [캐릭터 시트]를 먼저 영어로 고정하고, 모든 컷의 이미지 프롬프트에 같은 외모 묘사를 그대로 반복해 일관성을 유지한다.
7. 이미지 프롬프트 공식 (한 문단, 쉼표로 연결):
   [shot type], [subject + appearance], [action/pose], [setting], [lighting], [mood/color], [style/camera·lens], vertical 9:16
   예) medium close-up, a Korean woman in her 30s with a short black bob wearing a beige trench coat, looking back over her shoulder in surprise, rainy Seoul alley at night, neon reflections on wet pavement, cinematic teal and orange, shot on 35mm, shallow depth of field, photorealistic, vertical 9:16
8. 영상 프롬프트 공식 (첫 프레임 이미지가 있다는 전제, 움직임만 서술, 1~2문장):
   [camera movement] + [subject motion] + [environment motion] + [speed/feel]
   카메라 무브먼트는 힉스필드에서 잘 먹히는 표현을 쓴다:
   slow dolly in, dolly out, crash zoom in, push in, pull back, orbit around subject, 360 orbit, FPV drone fly-through, crane up, crane down, tilt up, tilt down, pan left/right, handheld shaky cam, whip pan, bullet time, static locked-off shot, snorricam, dolly zoom (vertigo effect)
9. 한 컷에 동작은 하나만. 복잡한 동작·여러 인물의 상호작용은 피한다(AI 영상이 깨진다).
10. 저작권 캐릭터·실존 유명인·브랜드 로고는 쓰지 않는다.

## 출력 형식 (반드시 이 순서)
### 0. 기획 요약
- 제목 후보 3개 (궁금증 유발형)
- 타깃 / 톤 / 총 길이 / 컷 수
- 훅 한 줄

### 1. 캐릭터 시트 (영어, 인물 있을 때만)
- Character A: (나이, 성별, 국적/인상, 헤어, 의상, 특징을 한 줄로)

### 2. 컷 표
| 컷 | 시간 | 화면 설명(한글) | 내레이션/대사 | 자막 |
|---|---|---|---|---|

### 3. 힉스필드 프롬프트 (컷별)
**Cut 1 (0:00–0:03)**
- Image prompt: ...
- Video prompt: ...
- Negative: text, subtitles, watermark, logo, extra fingers, deformed face, blurry
(모든 컷 반복)

### 4. 업로드 세트
- 제목 1개 확정 / 설명 2줄 / 해시태그 8개
- BGM·효과음 추천 (분위기 키워드로)
- 썸네일용 이미지 프롬프트 (영어, 9:16, 글자 없이)

## [입력]
- 주제:
- 영상 길이: (예: 30초 / 45초 / 60초)
- 장르/톤: (예: 정보형, 감동 드라마, 공포, 코미디, 반전, 동기부여)
- 타깃 시청자:
- 영상 스타일: (예: 실사 시네마틱, 3D 애니메이션, 지브리풍 일러스트, 다큐)
- 꼭 넣을 내용/금지 내용:
```

---

## 2. 입력 예시

```text
- 주제: 매일 같은 시간에 편의점에 오는 할머니의 비밀
- 영상 길이: 30초
- 장르/톤: 감동 반전 드라마
- 타깃 시청자: 20~50대
- 영상 스타일: 실사 시네마틱
- 꼭 넣을 내용/금지 내용: 마지막에 눈물 포인트, 자극적인 표현 금지
```

---

## 3. 출력 예시 (위 입력 기준 샘플)

### 0. 기획 요약
- 제목 후보: ① 매일 밤 11시, 할머니가 사 가는 단 하나 ② 알바생이 1년 만에 알게 된 할머니의 비밀 ③ 할머니는 왜 늘 우유 두 개를 샀을까
- 타깃 20~50대 / 잔잔→뭉클 / 30초 / 7컷
- 훅: "매일 밤 11시, 할머니는 꼭 우유 두 개를 사 가셨다."

### 1. 캐릭터 시트
- **Character A (Grandma):** a Korean woman in her late 70s, small and slightly hunched, short permed gray hair, kind wrinkled face, wearing a faded maroon knit cardigan over a floral blouse
- **Character B (Clerk):** a Korean man in his early 20s, messy black hair, tired eyes, wearing a green convenience store vest over a white t-shirt

### 2. 컷 표
| 컷 | 시간 | 화면 설명 | 내레이션 | 자막 |
|---|---|---|---|---|
| 1 | 0:00–0:04 | 밤 11시 편의점, 자동문 열리며 할머니 입장 | 매일 밤 11시, 할머니는 꼭 오셨다. | 매일 밤 11시 |
| 2 | 0:04–0:08 | 우유 두 개를 계산대에 올려놓는 손 | 사 가는 건 늘 우유 두 개. | 늘 우유 두 개 |
| 3 | 0:08–0:12 | 알바생이 고개를 갸웃 | 혼자 사신다던데… 왜 두 개일까. | 왜 두 개? |
| 4 | 0:12–0:16 | 어느 날 할머니가 오지 않은 빈 매장, 시계 11시 | 그런데 어느 날, 할머니가 오지 않았다. | 오지 않은 날 |
| 5 | 0:16–0:21 | 알바생이 퇴근길 골목에서 할머니 집 앞 발견 | 걱정돼 찾아간 할머니 집 앞엔— | |
| 6 | 0:21–0:26 | 문 앞 작은 그릇 두 개, 길고양이 두 마리가 기다림 | 할머니를 기다리던 고양이 두 마리가 있었다. | 고양이 두 마리 |
| 7 | 0:26–0:30 | 알바생이 우유를 따라주며 미소 | 그날부터, 우유는 내가 산다. | 이제 내 차례 |

### 3. 힉스필드 프롬프트

**Cut 1 (0:00–0:04)**
- Image prompt: wide shot, a Korean woman in her late 70s, small and slightly hunched, short permed gray hair, kind wrinkled face, wearing a faded maroon knit cardigan over a floral blouse, stepping through the sliding glass door of a brightly lit Korean convenience store at night, empty street outside, cool fluorescent light inside contrasting with dark blue night, quiet and lonely mood, cinematic, shot on 35mm, photorealistic, vertical 9:16
- Video prompt: slow dolly in toward the entrance as the automatic door slides open and the old woman slowly walks in, light breeze moving her cardigan, calm and gentle pace.

**Cut 2 (0:04–0:08)**
- Image prompt: extreme close-up, wrinkled elderly hands with a faded maroon knit cardigan sleeve placing two small cartons of white milk on a convenience store counter, barcode scanner nearby, warm fluorescent light, soft shallow depth of field, photorealistic, vertical 9:16
- Video prompt: static locked-off shot, the hands gently set down the second milk carton and slide both forward, subtle rack focus to the milk.

**Cut 3 (0:08–0:12)**
- Image prompt: medium close-up, a Korean man in his early 20s with messy black hair and tired eyes, wearing a green convenience store vest over a white t-shirt, tilting his head with a curious expression behind the counter, convenience store shelves blurred behind him, soft fluorescent light, photorealistic, vertical 9:16
- Video prompt: slow push in on his face as he tilts his head and narrows his eyes slightly, subtle handheld feel.

**Cut 4 (0:12–0:16)**
- Image prompt: wide shot, an empty Korean convenience store at night, wall clock showing 11 o'clock, glass door closed, no customers, cold blue-white lighting, melancholic mood, muted colors, photorealistic, vertical 9:16
- Video prompt: slow pan right from the clock to the closed glass door, nobody enters, a few flickers of the fluorescent light, still and lonely.

**Cut 5 (0:16–0:21)**
- Image prompt: medium shot from behind, a Korean man in his early 20s with messy black hair, wearing a green convenience store vest over a white t-shirt, walking up a narrow old residential alley in Seoul at night, single warm streetlight, worn brick walls, anxious mood, cinematic, photorealistic, vertical 9:16
- Video prompt: handheld tracking shot following him from behind as he walks quickly up the alley, streetlight flickering softly, tense pace.

**Cut 6 (0:21–0:26)**
- Image prompt: low angle close-up, two thin stray cats, one orange tabby and one black and white, sitting patiently beside two small empty ceramic bowls in front of an old wooden door, warm yellow light from a streetlamp, heartwarming and bittersweet mood, photorealistic, vertical 9:16
- Video prompt: slow crane down to cat eye level, the two cats look up toward the camera and softly meow, tails swaying gently.

**Cut 7 (0:26–0:30)**
- Image prompt: medium shot, a Korean man in his early 20s with messy black hair, wearing a green convenience store vest over a white t-shirt, crouching and pouring milk into two small ceramic bowls for an orange tabby cat and a black and white cat, warm golden streetlight, gentle smile, hopeful mood, cinematic, photorealistic, vertical 9:16
- Video prompt: slow orbit around him as he pours the milk and the cats begin to drink, he smiles softly, slow pull back to end the scene.

> 모든 컷 Negative: `text, subtitles, watermark, logo, extra fingers, deformed face, blurry, distorted animals`

### 4. 업로드 세트
- 제목: **할머니는 왜 매일 우유 두 개를 샀을까**
- 설명: 매일 밤 11시, 같은 손님. 1년 만에 알게 된 작은 비밀.
- 해시태그: #쇼츠 #감동 #감동실화 #편의점 #할머니 #길고양이 #반전 #뭉클
- BGM: 잔잔한 피아노 → 컷 6부터 스트링 추가 / 효과음: 편의점 도어벨, 바코드 삑, 고양이 울음
- 썸네일 프롬프트: close-up, wrinkled elderly hands holding two small cartons of milk, an orange tabby cat looking up in soft focus background, warm golden light, emotional, photorealistic, vertical 9:16

---

## 4. 힉스필드 사용 팁
- **이미지 먼저, 영상은 나중:** 텍스트→영상보다 이미지→영상이 인물·구도 일관성이 훨씬 좋습니다.
- **캐릭터 일관성:** 캐릭터 시트 문장을 매 컷 그대로 복붙하고, 가능하면 첫 컷 이미지를 레퍼런스(Soul ID/캐릭터 기능)로 재사용하세요.
- **영상 프롬프트는 짧게:** 이미 이미지에 있는 외모·배경은 다시 쓰지 말고 *움직임*만 쓰는 게 깨짐이 적습니다.
- **카메라 프리셋:** 힉스필드 카메라 무브먼트 프리셋(Dolly In, Crash Zoom, Orbit, FPV 등)을 고르면 영상 프롬프트의 카메라 문장과 겹치지 않게 피사체 동작만 남겨도 됩니다.
- **9:16 확인:** 생성 화면 비율을 세로(9:16)로 꼭 맞추세요.
