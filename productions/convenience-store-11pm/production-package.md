# K-드라마 쇼츠 Production Package (v2 — 캐릭터 일관성 강화판)
## 주제: 편의점 11시, 첫사랑이 돌아왔다

> **v2 변경 요약**
> - **0. Identity Lock Rules** 신설: 업로드한 인물 사진을 정체성 레퍼런스로 쓰는 7개 규칙을 모든 생성 단계에 적용
> - Consistency Anchor를 **인물별로 분리**(지우 / 현우). 한 씬에 안 나오는 인물의 묘사를 넣지 않아 얼굴이 섞이는 문제 차단
> - 얼굴 고정 항목 11개(윤곽·눈·쌍꺼풀·눈썹·코·입술·턱·피부톤·점/주근깨·나이·헤어라인)를 인물별로 구체화
> - "모든 컷 매크로" 표현 제거 → 컷마다 실제 렌즈(35/50/85/100mm macro) 지정. 얼굴 왜곡 방지, 실제 카메라 원근감
> - 뷰티 보정 금지 네거티브 추가(얼굴 축소·눈 키우기·V라인·미백·에어브러시 금지)
> - 점·흉터 위치를 **인물 기준 좌/우 + 화면 기준**으로 동시 표기해 좌우반전 오류 방지
> - 씬 3 프롬프트의 "wet modern Korean casual clothes"처럼 고정 의상과 충돌하던 표현 수정
> - 이미지(첫 프레임) 프롬프트와 영상(모션) 프롬프트 분리, 얼굴 검수 체크리스트(규칙 6) 추가
> - 화면 속 한글 자막·간판은 생성 대신 편집에서 넣도록 정리(글자 깨짐 방지)
> - 훅을 0~2초로 당긴 콜드오픈 옵션 추가

---

## 0. Identity Lock Rules — 사진 기반 인물 일관성 규칙 (모든 단계 최우선 적용)

사용자가 인물 사진을 올리고 새 이미지나 수정을 요청하면 아래 규칙을 따른다.

1. **업로드한 사진 = 정체성 레퍼런스.** 결과물 속 인물은 사진 속 인물과 같은 사람으로 확실히 알아볼 수 있어야 한다.
2. **아래 항목은 사용자가 직접 언급하지 않는 한 고정한다:** 얼굴 윤곽, 눈 모양·크기·간격, 쌍꺼풀 라인, 눈썹, 코 길이와 코끝, 입술 모양, 턱과 턱끝, 피부톤, 점과 주근깨, 겉보기 나이, 헤어라인.
3. **요청한 것만 바꾼다** (의상, 장소, 조명, 포즈, 카메라). 언급하지 않은 것은 사진 그대로 둔다.
4. **뷰티 보정 금지:** 얼굴 축소, 눈 확대, 턱 깎기, 피부 미백, 에어브러시 금지. 실제 피부 질감을 유지한다.
5. **실제 카메라 사진처럼:** 자연스러운 렌즈 원근감, 실제 빛과 그림자, 자연스러운 손.
6. **결과를 보여주기 전에 얼굴 비교:** 생성 결과의 얼굴을 원본 사진과 비교하고, 얼굴이 달라졌으면 얼굴을 고쳐 **한 번 재생성**한다.
7. **사진이 판독 불가면 추측하지 말고 알린다:** 너무 흐리거나, 필터가 심하거나, 각도가 심해 얼굴을 읽을 수 없으면 생성하지 않고 그 사실을 먼저 말한다.

### 0.1 이 프로젝트에서의 적용 방식

| 상황 | 처리 |
| --- | --- |
| 지우/현우 역 인물 사진을 업로드한 경우 | 사진이 정체성의 **유일한 기준**. 2.1/2.2의 얼굴 묘사는 사진과 다르면 **사진이 우선**하고, 텍스트 묘사는 사진에 맞춰 고쳐 쓴다. 의상·헤어스타일·장소만 이 문서대로 바꾼다. |
| 사진 없이 텍스트로만 생성하는 경우 | 2.3 레퍼런스 시트를 먼저 만들고, 승인된 시트 이미지를 이후 모든 씬의 레퍼런스 이미지로 첨부한다(텍스트 앵커 + 이미지 레퍼런스 동시 사용). |
| 씬마다 | 항상 **같은 승인 레퍼런스 이미지**를 첨부한다. 앞 씬 결과물을 다음 씬 레퍼런스로 쓰지 않는다(드리프트 누적 방지). |

> 사진은 본인 또는 사용 동의를 받은 인물의 사진만 사용한다.

### 0.2 레퍼런스 사진 판독 기준 (규칙 7)

다음 중 하나라도 해당하면 생성하지 않고 사용자에게 재업로드를 요청한다.
- 얼굴이 정면 기준 좌우 45° 이상 돌아가 있음 / 위아래로 심하게 숙이거나 듦
- 얼굴 폭이 약 300px 미만이거나 초점이 나가 눈·코·입 윤곽이 흐림
- 뷰티 필터·보정 앱·AR 효과가 강하게 들어감(피부 결이 안 보이거나 눈/턱이 변형됨)
- 선글라스, 마스크, 손, 머리카락이 눈·코·입 중 하나 이상을 가림
- 강한 컬러 조명이나 역광으로 피부톤 판단 불가

**권장 레퍼런스:** 정면 1장 + 3/4 측면 1장, 자연광, 무보정, 무표정 또는 옅은 미소, 헤어라인과 귀가 보이는 사진.

### 0.3 얼굴 검수 체크리스트 (규칙 6 — 매 이미지 생성 후)

원본 레퍼런스와 나란히 놓고 확인한다. **2개 이상 불일치 → 얼굴만 수정해 1회 재생성.** 재생성 후에도 불일치하면 결과를 보여주되 어떤 항목이 다른지 명시한다.

| # | 항목 | 확인 포인트 |
| --- | --- | --- |
| 1 | 얼굴 윤곽 | 갸름해지거나 넓어지지 않았는가 |
| 2 | 눈 모양·크기·간격 | 눈이 커지거나 간격이 바뀌지 않았는가 |
| 3 | 쌍꺼풀 | 라인 유무·두께가 같은가 |
| 4 | 눈썹 | 두께·각도·길이 |
| 5 | 코 | 콧대 길이, 코끝 모양 |
| 6 | 입술 | 두께, 윗입술/아랫입술 비율 |
| 7 | 턱·턱끝 | V라인으로 깎이지 않았는가 |
| 8 | 피부톤 | 밝아지거나 창백해지지 않았는가 |
| 9 | 점·주근깨·흉터 | 위치와 **좌우**가 맞는가 |
| 10 | 겉보기 나이 | 어려지거나 늙지 않았는가 |
| 11 | 헤어라인 | 이마 넓이, 가르마 위치 |
| + | 의상 | 2.1/2.2 고정 의상과 동일한가(색, 명찰, 시계 위치) |
| + | 손 | 손가락 5개, 관절 자연스러운가 |

---

## 1. Project Plan

**Concept:** 서울 밤 11시 편의점. 5년 전 헤어진 첫사랑이 비를 맞고 다시 들어온다. 삼각김밥 하나로 시작되는 40초 로맨스.
**핵심 훅:** "너, 아직도 참치마요 먹어?"
**Target Audience:** 20-30대 K-드라마 / 숏폼 로맨스 팬, 첫사랑·재회·편의점 감성 좋아하는 시청자
**Duration:** 40초
**Aspect Ratio:** 9:16 Vertical (1080x1920), 30fps
**Tone:** 따뜻하고 아련함 + 현실적인 한국 편의점 감성
**Ending:** 다음 편 유도형 클리프행어 (우산)

> **훅 보강 (권장):** 쇼츠는 첫 2초에 이탈이 결정된다. 0~2초에 씬 4의 대사 "너, 아직도 참치마요 먹어?"를 자막 + 남자 목소리로 먼저 깔고(화면은 비 내리는 간판), 이후 본편을 시작하는 콜드오픈을 권장. 총 길이는 그대로 40초.

---

## 2. Character Identity Lock — 씬 생성 전 캐릭터 고정

> **규칙:**
> 1. 사진 업로드 시 0장 규칙이 최우선. 아래 얼굴 묘사는 사진이 없을 때의 기본값이며, 사진이 있으면 사진에 맞게 고쳐 쓴다.
> 2. 모든 씬 프롬프트 맨 앞에 **그 씬에 등장하는 인물의 앵커만** 붙인다(2.4). 등장하지 않는 인물 앵커는 넣지 않는다.
> 3. 실제 이미지/영상 생성은 '진행해' 승인 후에만 시작한다.

### 2.1 Character Profile — Main: 지우 (Jiwoo)

**Age:** 24 (겉보기 나이 24, 더 어려 보이게 만들지 않음)
**Gender:** Female
**Role:** 편의점 야간 아르바이트생, 주인공

**Face Lock (11항목):**
| 항목 | 고정값 |
| --- | --- |
| 얼굴 윤곽 | soft oval face, natural cheek fullness, not slimmed |
| 눈 모양·크기·간격 | medium almond-shaped dark brown eyes, natural size, average spacing (about one eye-width apart) |
| 쌍꺼풀 | natural thin in-out double eyelid (tapered at inner corner) |
| 눈썹 | thin natural straight brows, slightly soft arch at outer third |
| 코 | straight soft nose bridge, medium length, small rounded tip |
| 입술 | natural medium-full lips, slightly fuller lower lip, muted rose tint |
| 턱·턱끝 | gentle rounded jawline, soft rounded chin (no V-line) |
| 피부톤 | light warm beige Korean skin tone |
| 점·주근깨 | small mole under her LEFT eye (viewer's right in front view), light freckles across nose bridge |
| 겉보기 나이 | 24 |
| 헤어라인 | natural rounded hairline, side part on her right, curtain bangs |

**Skin Micro-Texture:** visible natural pores, fine peach fuzz, slight under-eye shadow from night shift, minimal makeup, no porcelain / plastic filter look
**Hairstyle:** shoulder-length dark brown layered cut, soft curtain bangs, slightly wavy ends, right side tucked behind ear, a few loose strands on cheek, natural shine, no bright dye
**Exact Outfit (고정 — 씬마다 동일):**
- Cream ivory knit cardigan, loose fit, ribbed cuffs, top 2 buttons undone
- Plain white crew-neck T-shirt
- Dark green convenience store apron, small white Hangul name tag "지우" on her left chest, strings tied at back
- Light blue straight-fit jeans, slightly faded knees
- White low-top canvas sneakers, slightly worn sole
- Thin silver stud earrings, no necklace, no rings, clear phone case in apron pocket

### 2.2 Character Profile — Sub: 현우 (Hyunwoo)

**Age:** 26
**Gender:** Male
**Role:** 5년 만에 돌아온 첫사랑

**Face Lock (11항목):**
| 항목 | 고정값 |
| --- | --- |
| 얼굴 윤곽 | clean oval face, slightly longer lower third |
| 눈 모양·크기·간격 | medium-narrow dark brown eyes, slightly upturned outer corners, average spacing |
| 쌍꺼풀 | inner (in-fold) double eyelid, fold hidden at inner corner, visible only at outer half |
| 눈썹 | medium-thick straight dark brows |
| 코 | straight nose, medium-high bridge, slightly defined tip |
| 입술 | natural medium lips, defined cupid's bow |
| 턱·턱끝 | defined but soft jawline, straight chin |
| 피부톤 | medium warm beige Korean skin tone |
| 점·흉터 | faint acne scar on his RIGHT cheek (viewer's left in front view), light stubble shadow on chin |
| 겉보기 나이 | 26 |
| 헤어라인 | straight natural hairline, fringe covering upper forehead |

**Skin Micro-Texture:** visible pores, natural rain sheen, no heavy makeup
**Hairstyle:** short black Korean two-block cut, longer textured top, neatly faded sides, front fringe over forehead. **씬 3~5: 비에 젖은 상태**(젖은 정도 동일 유지)
**Exact Outfit (고정 — 씬마다 동일):**
- Charcoal gray oversized hooded windbreaker, zip half-up, rain-wet
- Black crew-neck T-shirt
- Dark navy straight-fit chinos, wet hems
- Black-and-white low-top sneakers, wet
- Black digital watch on his LEFT wrist, no other accessories
- Wet transparent umbrella (씬 3에서 들고 들어와 계산대 옆에 기대 둠 → 씬 5에서 두고 감)

### 2.3 Character Reference Sheet Prompt

**A. 사진을 업로드한 경우 (권장)**

`Use the uploaded photo as the strict identity reference. Create a hyper-realistic character reference sheet of THIS SAME PERSON, clearly recognizable as the person in the photo. Keep unchanged from the photo: face outline, eye shape, size and spacing, eyelid fold, eyebrows, nose length and tip, lip shape, jaw and chin, skin tone, every mole and freckle in the same position and side, apparent age, hairline. Change ONLY: outfit to [2.1 or 2.2 Exact Outfit], hairstyle to [2.1 or 2.2 Hairstyle], background to clean neutral light gray studio. Layout: FRONT full-body, SIDE profile, 3/4 view, head-and-shoulders close-up. Same face and same outfit in every view. Real camera photo, 50mm lens for full body and 85mm lens for close-up, soft even studio lighting with natural soft shadows, real skin texture with visible pores, believable hands.`

**B. 사진 없이 텍스트로만 생성하는 경우 — 지우**

`Hyper-realistic character reference sheet photo of ONE person: Jiwoo, 24-year-old modern South Korean woman. [2.1 Face Lock 전체를 영어로 나열]. Shoulder-length dark brown layered hair with curtain bangs, right side tucked behind ear. Outfit: cream ivory knit cardigan, white crew-neck T-shirt, dark green convenience store apron with small white Hangul name tag "지우" on her left chest, light blue straight jeans, white canvas sneakers, thin silver stud earrings. Layout on clean neutral light gray studio background: FRONT full-body, SIDE profile, 3/4 view, head-and-shoulders close-up. Identical face, identical mole position, identical outfit in every view. Real camera photo, 50mm and 85mm lens, soft even studio lighting with natural soft shadows, real skin texture with visible pores and fine peach fuzz, believable hands, accurate Hangul only.`

**C. 사진 없이 텍스트로만 생성하는 경우 — 현우** (지우와 **별도 생성**. 한 장에 두 사람을 넣지 않는다)

`Hyper-realistic character reference sheet photo of ONE person: Hyunwoo, 26-year-old modern South Korean man. [2.2 Face Lock 전체를 영어로 나열]. Short black two-block haircut with textured top and fringe over forehead. Outfit: charcoal gray oversized hooded windbreaker zipped halfway, black crew-neck T-shirt, dark navy straight chinos, black-and-white low-top sneakers, black digital watch on his left wrist. Layout on clean neutral light gray studio background: FRONT full-body, SIDE profile, 3/4 view, head-and-shoulders close-up. Identical face, identical scar position, identical outfit in every view. Real camera photo, 50mm and 85mm lens, soft even studio lighting with natural soft shadows, real skin texture with visible pores, believable hands.`

> 승인된 레퍼런스 시트(또는 업로드 사진)를 **이후 모든 씬에 레퍼런스 이미지로 첨부**한다. 텍스트 앵커만으로는 얼굴이 고정되지 않는다.

### 2.4 Consistency Anchor Prompts (인물별 분리)

**[ANCHOR-J] 지우 등장 씬 맨 앞에:**

`IDENTITY LOCK — Jiwoo: same person as the attached reference image, clearly recognizable. Keep unchanged: face outline, eye shape, size and spacing, eyelid fold, eyebrows, nose length and tip, lip shape, jaw and chin, light warm beige skin tone, small mole under her left eye, light freckles on nose bridge, apparent age 24, hairline. 24-year-old modern South Korean woman, shoulder-length dark brown layered hair with curtain bangs. Outfit unchanged: cream ivory knit cardigan, white T-shirt, dark green convenience store apron with Hangul name tag "지우" on her left chest, light blue straight jeans, white canvas sneakers, silver stud earrings. No beauty retouching, real skin texture.`

**[ANCHOR-H] 현우 등장 씬 맨 앞에:**

`IDENTITY LOCK — Hyunwoo: same person as the attached reference image, clearly recognizable. Keep unchanged: face outline, eye shape, size and spacing, inner eyelid fold, eyebrows, nose length and tip, lip shape, jaw and chin, medium warm beige skin tone, faint acne scar on his right cheek, apparent age 26, hairline. 26-year-old modern South Korean man, short black two-block haircut, rain-wet. Outfit unchanged: charcoal gray hooded windbreaker zipped halfway, black T-shirt, dark navy chinos, black-and-white sneakers, black digital watch on left wrist. No beauty retouching, real skin texture.`

**[TWO-SHOT RULE] 두 사람이 같이 나오는 씬:**
- 두 앵커를 모두 넣고, 각자의 레퍼런스 이미지를 **따로** 첨부한다.
- 화면 위치를 반드시 명시: 예) `Jiwoo on the LEFT behind the counter, Hyunwoo on the RIGHT at the counter.`
- 마지막에 `Do not blend or swap the two faces.` 추가.

---

## 3. Script & Storyboard Table

| Scene # | Timestamp | Dialogue / VO | Action | Camera | 등장 인물 / 앵커 |
| --- | --- | --- | --- | --- | --- |
| 0 (옵션 콜드오픈) | 00:00-00:02 | 남(V.O.): "너, 아직도 참치마요 먹어?" | 비 젖은 간판 불빛 | 고정, 빗방울 포커스 | 없음 |
| 1 | 00:00(02)-00:05 | VO (여): "밤 11시, 오늘도 마지막 손님만 기다리고 있어요." | 비 내리는 서울 밤거리, 편의점 간판 불빛, 창 너머 계산대의 지우 | 빗방울 클로즈업 → 간판으로 틸트업 → 창 안 지우로 슬로우 달리인 | J |
| 2 | 00:05-00:12 | (무음) 효과음만 | 지우의 손: 삼각김밥 정리, 컵라면, 따뜻한 캔커피 | 100mm 매크로 인서트, 얕은 심도, 손 따라 천천히 패닝 | J (손만) |
| 3 | 00:12-00:22 | 남: "어... 여기 아직 있어?" / 여: "오빠?" | 문 열리며 종소리, 비 맞은 현우 등장, 우산을 계산대 옆에 기대 둠, 두 사람 눈 마주침 | 문 쪽 → 투샷 휘핑팬, 지우 얼굴 85mm 클로즈업 컷인 | J + H |
| 4 | 00:22-00:32 | 남: "5년 만이네. 너, 아직도 참치마요 먹어?" / 여: "...오빠는 아직도 비 맞고 다녀?" | 현우가 참치마요 삼각김밥을 건넴, 지우 미소, 어색하고 설레는 공기 | 현우 어깨 너머 오버숄더(지우 얼굴), 주고받는 손 100mm 매크로 인서트 | J + H |
| 5 | 00:32-00:40 | VO (여): "그날 이후, 매일 11시가 기다려졌어요." | 현우 나간 뒤 계산대 옆 우산 발견, 지우가 우산을 들고 빗속으로 뛰어나감(뒷모습) | 뒷모습 팔로우샷 → 우산 클로즈업 엔딩 | J (+H 원경) |

> 엔딩 자막 "다음 편: 우산"은 **편집에서** 넣는다(생성 이미지 속 글자는 깨지기 쉬움).

---

## 4. Image & Video Generation Prompts

### 4.0 생성 순서 (워크플로)
1. 레퍼런스 확보: 업로드 사진 판독(0.2) → 또는 2.3 시트 생성 → **사용자 승인**
2. 씬별 **첫 프레임 이미지** 생성: [앵커] + [씬 이미지 프롬프트] + 레퍼런스 이미지 첨부
3. **얼굴 검수(0.3)** → 불일치 시 얼굴만 수정해 1회 재생성
4. 검수 통과한 첫 프레임으로 **이미지→영상** 생성: [씬 영상 프롬프트]
5. 영상에서도 얼굴 변형(모핑) 확인 → 변형된 구간은 잘라내거나 재생성

### 4.1 공통 스타일 (모든 씬, 앵커 뒤에 붙임)

`Real camera photo / cinema footage look, natural lens perspective, real light and shadows, believable hands with five fingers, natural skin texture with visible pores, authentic modern South Korean convenience store and Seoul street at night, Hangul signage only, no real brand logos, 9:16 vertical composition, 4K detail.`

> 기존의 "hyper-realistic macro photography"를 전 컷에 거는 방식은 얼굴 클로즈업에서 광각 왜곡·과샤픈을 일으켜 얼굴이 달라 보이게 만든다. 매크로는 손/소품 인서트에만 쓴다.

### Scene 1 — 비 오는 편의점 외관
**이미지:** `[ANCHOR-J] [4.1] Rainy night in Seoul, exterior of a small modern South Korean convenience store, warm interior light glowing through rain-streaked glass, wet asphalt reflections, Jiwoo visible inside behind the counter as a small mid-ground figure, cool blue night vs warm 3200K interior contrast, 35mm lens, shallow depth of field on raindrops on the glass.`
**영상:** `Slow tilt up from raindrops to the glowing store sign, then slow dolly-in toward the window. Rain falling steadily. Jiwoo stays still behind the counter. Keep her face and outfit identical to the first frame, no morphing.`

### Scene 2 — 손과 삼각김밥 인서트
**이미지:** `[ANCHOR-J] [4.1] Close-up insert of Jiwoo's hands (cream ivory knit cardigan ribbed cuffs visible, no rings, short natural nails) arranging triangle kimbap with Hangul packaging on a Korean convenience store shelf, warm shelf light, plastic wrapper texture, 100mm macro lens, shallow depth of field, five natural fingers per hand.`
**영상:** `Slow pan following her hands placing triangle kimbap, then touching a cup ramen and a warm canned coffee. Natural finger movement, no extra fingers, cardigan cuffs unchanged.`

### Scene 3 — 재회
**이미지:** `[ANCHOR-J] [ANCHOR-H] [4.1] Inside a Korean convenience store at night. Hyunwoo on the RIGHT just stepping through the glass door, rain-wet hair and charcoal windbreaker, holding a wet transparent umbrella. Jiwoo on the LEFT behind the counter, surprised, eyes meeting his. Hangul shelf signs softly blurred in background, natural fluorescent and warm light mix, 35mm lens medium two-shot, eye-level. Do not blend or swap the two faces.`
**클로즈업 컷인 이미지:** `[ANCHOR-J] [4.1] Close-up of Jiwoo's face reacting in surprise, lips slightly parted, 85mm lens, eye-level, soft store light, mole under her left eye visible, real skin texture.`
**영상:** `Door opens with rain behind him, Hyunwoo steps in and leans the umbrella against the counter, both freeze and look at each other. Subtle breathing, no exaggerated expressions. Keep both faces identical to the first frame, no morphing, no face swap.`

### Scene 4 — 삼각김밥 건네기
**이미지:** `[ANCHOR-J] [ANCHOR-H] [4.1] Over-the-shoulder shot from behind Hyunwoo's RIGHT shoulder (his wet charcoal windbreaker and back of his head in soft foreground blur), focus on Jiwoo's face on the LEFT behind the counter, warm small smile, natural slight blush, he holds out a tuna mayo triangle kimbap with Hangul label. 50mm lens, shallow depth of field. Do not blend or swap the two faces.`
**손 인서트 이미지:** `[4.1] Close-up insert of a man's hand (black digital watch on left wrist, wet windbreaker sleeve) handing a triangle kimbap to a woman's hand (cream knit cardigan cuff) across a convenience store counter, 100mm macro lens, five natural fingers per hand.`
**영상:** `He slowly slides the triangle kimbap across the counter, she hesitates then takes it, small shy smile. Gentle handheld micro-movement. Keep faces identical to the first frame, no morphing.`

### Scene 5 — 우산 엔딩
**이미지:** `[ANCHOR-J] [4.1] Back view of Jiwoo running out of the convenience store into the rain, holding Hyunwoo's transparent umbrella (closed, in her hand), apron strings visible at her back, cardigan getting wet, a blurred male figure in a charcoal hooded windbreaker far ahead on the wet street, warm store light behind her, wet reflections, 35mm lens follow shot.`
**영상:** `Camera follows behind Jiwoo as she runs into the rain, she opens the transparent umbrella, end on close-up of the umbrella canopy with rain drops. Keep outfit and hair identical to previous scenes.`

### 4.2 Negative Prompt (모든 씬 공통)

`different person, face drift, changed face shape, enlarged eyes, slimmed face, V-line chin, sharpened chin, skin whitening, pale porcelain skin, airbrushed skin, plastic skin, beauty filter, heavy makeup, younger-looking face, older-looking face, mirrored mole position, blended faces, face swap, extra fingers, missing fingers, fused fingers, distorted hands, wide-angle face distortion, different outfit, missing name tag, watch on wrong wrist, anime, cartoon, illustration, 3D render, Chinese or Japanese styling, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, low resolution, blurry face`

> 원본의 "No Chinese people, No Japanese people"는 생성 모델에서 효과가 약하고 얼굴을 불안정하게 만들 수 있어, **"modern South Korean" 긍정 묘사 + 레퍼런스 이미지 고정**으로 대체하고 네거티브에는 스타일·문자만 남겼다.

---

## 5. Video Editing Guide

**Cut Pacing:**
- 00:00-00:12: 빠른 컷 0.8-1.2초, 비·간판·손 인서트로 몰입
- 00:12-00:32: 2-3초 롱테이크로 감정 유지, 눈맞춤은 끊지 않기
- 00:32-00:40: 다시 빠르게, 우산 클로즈업에서 엔딩 자막으로 컷

**Transitions:**
- Scene 1 > 2: 빗방울에서 손으로 매치컷
- Scene 2 > 3: 종소리에 맞춰 화이트 플래시 / 휘핑팬
- Scene 3 > 4: 눈 클로즈업 → 손 인서트는 점프컷 대신 6프레임 디졸브
- Scene 5: 페이드 아웃 + 다음 편 예고 자막

**얼굴 연속성 편집 체크:**
- 컷이 바뀔 때 지우의 점(왼쪽 눈 아래)과 현우의 흉터(오른쪽 볼)가 같은 쪽에 있는지 확인. 화면 좌우반전(flip) 금지
- 영상 생성 결과에서 얼굴이 흐르거나 바뀌는 프레임은 잘라낸다
- 현우 머리 젖은 정도, 지우 머리 넘긴 방향(오른쪽 귀 뒤) 컷 간 일치

**Subtitle / Caption Styling:**
- 폰트: Pretendard Bold, 흰색 + 검은 그림자 80%
- 위치: 하단 안전영역, 9:16 기준 하단 15% 위 (유튜브 쇼츠 UI 가림 영역 피하기)
- 한 줄 최대 12자, 키워드는 노란색 `#FFD93D` 강조 (예: "5년 만", "참치마요")
- 모든 화면 글자(자막, "다음 편: 우산")는 편집 툴에서 삽입. Hangul만 사용, 이모지 최소

**BGM & SFX Cue Sheet:**
- 00:00-00:05: 빗소리 + 잔잔한 피아노 Lo-fi (BPM 70)
- 00:05-00:12: 편의점 냉장고 웅웅 소리, 비닐 소리
- 00:12: 문 열림 종소리 "딸랑" + BGM 멈춤 0.5초 (긴장)
- 00:22-00:32: BGM 다시 작게, 심장 박동 SFX 살짝
- 00:32-00:40: BGM 클라이맥스, 우산 펼치는 소리, 엔딩 후 1초 무음

**Color Grading Notes:**
- 전체: 따뜻한 편의점 내부 (3200K) vs 차가운 밤거리 (6500K) 대비 유지
- 피부톤: 레퍼런스 사진의 피부톤 기준으로 맞춘다. 미백·채도 과다·스킨 스무딩 금지
- 하이라이트: 간판 불빛 살짝 글로우, 그림자 딥블루
- LUT: Muted Teal & Orange, 채도 -10, 콘트라스트 +8, 필름 그레인 5%
- 자막 가독성 위해 하단 비네트 10%

---

## 다음 단계
- 이 구상안으로 이미지·영상을 만들려면 **'진행해'** 라고 승인해야 생성을 시작한다.
- 승인 시 순서: (1) 업로드 사진 판독 또는 레퍼런스 시트(2.3) 생성 → 확인받기 → (2) 씬별 첫 프레임 → 얼굴 검수 → (3) 영상.
- 지우/현우 역으로 쓸 인물 사진이 있다면 정면 1장 + 3/4 측면 1장을 함께 올려주면 일관성이 가장 높다.
