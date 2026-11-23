# 마지막 운행의 10초 — 감동 / 60초 / 실사 (v2.1 최종본)

> v2 변경점: ① 컷 14 FPV 드론 제거 → 잔잔한 항공샷 ② 한국 버스·정류장 명시 + 레퍼런스 고정 ③ 키링을 컷 3·9에서 크게 ④ 컷 12 측면 투샷 + 대사는 보이스오버로 ⑤ 회상 속 기사를 현재 기사 레퍼런스로 일관성 확보 ⑥ 한글 간판 깨짐 대응 ⑦ 목소리 2개(내레이터/여자)로 분리하고 컷 길이에 맞게 대사 압축 ⑧ TTS·BGM·효과음 세트 추가 ⑨ (v2.1) Suno Instrumental·가사 칸 충돌 수정, 볼륨 밸런스 추가

## 0. 기획 요약
- 제목 후보: ① 30년 버스 기사가 매일 10초를 기다린 이유 ② 마지막 운행 날, 그 정류장에 그녀가 서 있었다 ③ 기사님, 저 한 번도 안 늦었어요
- 타깃: 20~60대 / 톤: 잔잔 → 뭉클 / 60초 / 14컷 (컷 1~10은 4초, 컷 11~14는 5초)
- 훅: "30년 같은 노선. 오늘이 마지막 운행이다."
- 연결 장치: **노란 곰 키링** (8살 → 17살 → 28살)
- 수미상관: 컷 5(어린 시절 인사) ↔ 컷 11(어른이 되어 인사), **같은 구도**

---

## 1. 레퍼런스 시트 (먼저 만들어 고정)

모든 컷 프롬프트에 아래 영어 문장을 **그대로** 복붙합니다.

| 이름 | 영어 묘사 |
|---|---|
| **DRIVER (현재)** | a Korean man in his late 60s, short salt-and-pepper hair, kind tired eyes with deep smile lines, light blue short-sleeve bus driver uniform shirt with a navy tie and a navy driver cap |
| **DRIVER_PAST (회상)** | the same Korean bus driver about 20 years younger, in his late 40s, short black hair with a few gray strands, the same kind eyes, light blue short-sleeve bus driver uniform shirt with a navy tie and a navy driver cap |
| **GIRL (8살)** | a Korean girl about 8 years old, black hair in two short pigtails, round cheeks, yellow raincoat, red backpack with a small yellow teddy bear keychain |
| **STUDENT (17살)** | a Korean high school girl about 17 years old, black hair in a high ponytail, navy school blazer uniform, red backpack with a small worn yellow teddy bear keychain |
| **WOMAN (28살)** | a Korean woman in her late 20s, shoulder-length black hair in a low ponytail, cream blouse with a beige cardigan, beige tote bag with a small worn yellow teddy bear keychain |
| **BUS** | a modern South Korean green city bus, low-floor Seoul-style |
| **STOP** | a Korean neighborhood bus stop with a small glass shelter and a metal bench, signs blurred in the background |

- 회상 스타일: `warm faded film look, early 2000s nostalgic color grade, soft grain`
- 현재 스타일: `cinematic, natural light, shot on 35mm, shallow depth of field, photorealistic`

### 생성 순서 (일관성 핵심)
1. **컷 1** 먼저 생성 → 마음에 드는 이미지에서 **DRIVER 얼굴**과 **BUS**를 레퍼런스로 저장
2. **DRIVER_PAST**는 DRIVER 이미지를 레퍼런스로 넣고 "20 years younger"로 생성 (따로 만들면 다른 사람이 됨)
3. **컷 5** 생성 → 이 구도를 **컷 11의 레퍼런스**로 사용 (인물만 WOMAN으로 교체)
4. **GIRL → STUDENT → WOMAN**은 같은 얼굴형이 이어지도록 앞 단계 이미지를 레퍼런스로 넣기
5. 이미지가 확정되면 영상 프롬프트로 움직임 생성

---

## 2. 컷 표 + 목소리

목소리: 🎙 **내레이터**(차분한 3인칭) / 👩 **여자**(WOMAN 본인)

| 컷 | 시간 | 화면 | 목소리 | 대사 | 자막 |
|---|---|---|---|---|---|
| 1 | 0:00–0:04 | 새벽 차고지, 기사가 모자를 쓴다 | 🎙 | 30년 같은 노선. 오늘이 마지막 운행이다. | 오늘이 마지막 운행 |
| 2 | 0:04–0:08 | 닳은 핸들을 쓰다듬는 손 | 🎙 | 그에겐 지켜온 습관이 하나 있었다. | 30년의 습관 |
| 3 | 0:08–0:12 | (회상) 뛰는 아이의 빨간 가방과 노란 곰 키링 | 🎙 | 매일 아침, 늘 늦게 뛰어오던 아이. | 늘 늦던 아이 |
| 4 | 0:12–0:16 | (회상) 기사가 사이드미러를 보며 기다림 | 🎙 | 그는 늘, 10초를 더 기다렸다. | 10초 |
| 5 | 0:16–0:20 | (회상) 아이가 버스 계단에서 꾸벅 인사 | 🎙 | 아이는 늘 숨을 헐떡이며 인사했다. | |
| 6 | 0:20–0:24 | (회상) 교복 입은 학생이 창가 자리에 | 🎙 | 그렇게 10년, 아이는 교복을 입었고— | 10년 |
| 7 | 0:24–0:28 | (회상) 텅 빈 정류장, 은행잎 | 🎙 | 어느 날부터, 더는 오지 않았다. | 더는 오지 않았다 |
| 8 | 0:28–0:32 | 현재. 운전석에서 그 정류장을 바라봄 | 🎙 | 그리고 오늘, 마지막 운행. | 마지막 정류장 |
| 9 | 0:32–0:36 | 뛰는 토트백과 낡은 노란 곰 키링 (얼굴은 아직 안 보임) | 🎙 | 그 정류장에, 누군가 뛰어오고 있었다. | |
| 10 | 0:36–0:40 | 기사의 눈이 커졌다가 미소 | 🎙 | 그는 습관처럼, 10초를 기다렸다. | 습관처럼 10초 |
| 11 | 0:40–0:45 | 여자가 버스 계단에서 그때처럼 꾸벅 (컷 5와 같은 구도) | 🎙 | 숨을 헐떡이며, 그때처럼 고개를 숙이는 사람. | |
| 12 | 0:45–0:50 | 측면 투샷, 꽃다발과 편지를 건넴 | 👩 | 기사님 덕분에… 한 번도 안 늦었어요. | 한 번도 안 늦었어요 |
| 13 | 0:50–0:55 | 기사의 젖은 눈 클로즈업 | 👩 | 저, 오늘부터 선생님이에요. | 저, 선생님 됐어요 |
| 14 | 0:55–1:00 | 노을 속으로 떠나는 버스, 항공샷 | 🎙 | 그 10초가, 한 아이의 인생을 기다려주고 있었다. | 당신의 10초 |

> 대사 길이는 1초당 4~5글자 기준으로 맞췄습니다. 컷 12·13의 여자 대사는 **보이스오버**로 깔고, 화면에서 입을 맞추지 않습니다(립싱크 없음).

---

## 3. 힉스필드 프롬프트

**모든 컷 Negative:**
`text, subtitles, Korean text, garbled letters, readable signs, watermark, logo, extra fingers, deformed hands, deformed face, blurry, duplicate person, western-style bus`

**Cut 1 (0:00–0:04)** ⭐ 레퍼런스 컷
- Image: medium shot, a Korean man in his late 60s, short salt-and-pepper hair, kind tired eyes with deep smile lines, light blue short-sleeve bus driver uniform shirt with a navy tie, putting on a navy driver cap in front of a parked modern South Korean green city bus, low-floor Seoul-style, quiet Korean bus depot at dawn, soft blue morning haze with warm sodium lights, calm and nostalgic mood, cinematic, natural light, shot on 35mm, shallow depth of field, photorealistic, vertical 9:16
- Video: slow dolly in as he adjusts the cap with both hands and takes a deep breath, light morning mist drifting, calm pace.

**Cut 2 (0:04–0:08)**
- Image: extreme close-up, weathered elderly hands of a Korean bus driver in a light blue short-sleeve uniform shirt gently resting on a worn black steering wheel with faded grip marks, dashboard of a modern South Korean city bus softly lit by sunrise through the windshield, warm golden tones, shallow depth of field, photorealistic, vertical 9:16
- Video: static locked-off shot, the thumb slowly rubs the worn spot on the steering wheel, sunlight slowly brightening across the dashboard.

**Cut 3 (0:08–0:12)** — 회상 / 키링 강조
- Image: medium close-up from behind at child height, a red backpack with a small yellow teddy bear keychain bouncing on the back of a Korean girl about 8 years old, black hair in two short pigtails, yellow raincoat, running toward a Korean neighborhood bus stop with a small glass shelter on a drizzly morning, a modern South Korean green city bus waiting softly out of focus ahead, wet pavement, warm faded film look, early 2000s nostalgic color grade, soft grain, photorealistic, vertical 9:16
- Video: handheld tracking shot following the running girl from behind, the yellow teddy bear keychain swinging clearly in the foreground, pigtails bouncing, light rain falling.

**Cut 4 (0:12–0:16)** — 회상 / DRIVER 레퍼런스 사용
- Image: close-up, the same Korean bus driver about 20 years younger, in his late 40s, short black hair with a few gray strands, the same kind eyes, light blue short-sleeve bus driver uniform shirt with a navy tie and a navy driver cap, glancing at the side mirror while waiting with the bus door open, rainy morning, warm faded film look, early 2000s nostalgic color grade, soft grain, photorealistic, vertical 9:16
- Video: slow push in on his face as he keeps watching the mirror and gives a small patient smile, raindrops sliding down the window.

**Cut 5 (0:16–0:20)** — 회상 ⭐ 컷 11 레퍼런스
- Image: medium shot from inside the bus looking at the front door steps, a Korean girl about 8 years old, black hair in two short pigtails, yellow raincoat, red backpack with a small yellow teddy bear keychain, standing on the bus steps out of breath and bowing politely, rainy Korean street behind her, warm faded film look, early 2000s nostalgic color grade, soft grain, photorealistic, vertical 9:16
- Video: static shot, the girl catches her breath and bows deeply, then looks up with a shy smile.

**Cut 6 (0:20–0:24)** — 회상
- Image: medium close-up, a Korean high school girl about 17 years old, black hair in a high ponytail, navy school blazer uniform, red backpack with a small worn yellow teddy bear keychain on her lap, sitting by the window of a South Korean city bus looking outside, rain streaks on the glass, soft gray daylight, warm faded film look, early 2000s nostalgic color grade, soft grain, photorealistic, vertical 9:16
- Video: slow pan left along the rainy window to her reflective face, city lights blurring past outside.

**Cut 7 (0:24–0:28)** — 회상
- Image: wide shot, an empty Korean neighborhood bus stop with a small glass shelter and a metal bench in autumn, fallen yellow ginkgo leaves on the bench and pavement, nobody waiting, signs blurred, overcast light, lonely and quiet mood, warm faded film look, soft grain, photorealistic, vertical 9:16
- Video: static locked-off shot, a gentle wind blows ginkgo leaves across the empty bench, slow and still.

**Cut 8 (0:28–0:32)**
- Image: over-the-shoulder shot from the driver's seat, a Korean man in his late 60s, short salt-and-pepper hair, light blue short-sleeve bus driver uniform shirt and navy driver cap, looking through the windshield of a South Korean city bus at a Korean neighborhood bus stop with a small glass shelter ahead, warm late-afternoon sunlight, cinematic, natural light, shot on 35mm, shallow depth of field, photorealistic, vertical 9:16
- Video: slow push in through the windshield toward the bus stop as the bus gently slows down, sunlight flaring softly.

**Cut 9 (0:32–0:36)** — 키링 강조 / 얼굴 숨김
- Image: medium close-up, a beige tote bag with a small worn yellow teddy bear keychain swinging at the hip of a running Korean woman in a cream blouse and beige cardigan, holding a small bouquet of white and yellow flowers, face out of frame, Korean neighborhood street in warm late-afternoon golden light, cinematic, natural light, shot on 35mm, shallow depth of field, photorealistic, vertical 9:16
- Video: tracking shot at hip level as she runs, the worn yellow teddy bear keychain swinging clearly in the center of the frame, slight slow motion, golden light flickering through trees.

**Cut 10 (0:36–0:40)**
- Image: close-up, a Korean man in his late 60s, short salt-and-pepper hair, kind tired eyes with deep smile lines, navy driver cap, looking at the side mirror of a South Korean city bus with widening eyes, warm golden sunlight on his face, cinematic, shot on 35mm, shallow depth of field, photorealistic, vertical 9:16
- Video: slow push in as his eyes widen in recognition and soften into a quiet smile, he keeps the door open.

**Cut 11 (0:40–0:45)** — 컷 5 레퍼런스로 같은 구도
- Image: medium shot from inside the bus looking at the front door steps, a Korean woman in her late 20s, shoulder-length black hair in a low ponytail, cream blouse with a beige cardigan, beige tote bag with a small worn yellow teddy bear keychain, holding a small bouquet, standing on the bus steps out of breath and bowing politely, golden afternoon Korean street behind her, cinematic, natural light, shot on 35mm, photorealistic, vertical 9:16
- Video: static shot mirroring the childhood scene, she catches her breath and bows deeply, then looks up with a teary smile.

**Cut 12 (0:45–0:50)** — 측면 투샷, 입 움직임 없음
- Image: side profile two-shot, a Korean woman in her late 20s, shoulder-length black hair in a low ponytail, cream blouse with a beige cardigan, holding out a small bouquet of white and yellow flowers and a plain white envelope to a Korean man in his late 60s with short salt-and-pepper hair, light blue uniform shirt and navy driver cap, seated at the wheel of a South Korean city bus, both with lips closed, warm golden backlight through the bus windows, cinematic, shot on 35mm, shallow depth of field, photorealistic, vertical 9:16
- Video: static side shot, she gently holds out the flowers and envelope, the driver slowly reaches out and takes them with both hands, no talking, subtle golden light flicker.

**Cut 13 (0:50–0:55)**
- Image: extreme close-up, a Korean man in his late 60s, short salt-and-pepper hair, deep smile lines, navy driver cap, holding a small bouquet of white and yellow flowers near his chest, eyes glistening with tears while smiling, lips closed, golden backlight, cinematic, shot on 85mm, very shallow depth of field, photorealistic, vertical 9:16
- Video: very slow push in as a single tear rolls down his cheek and he nods softly, lips closed, static background.

**Cut 14 (0:55–1:00)**
- Image: aerial wide shot, a modern South Korean green city bus driving along a quiet tree-lined road in a small Korean town toward a glowing orange sunset, long shadows, low-rise rooftops, peaceful and emotional mood, cinematic, photorealistic, vertical 9:16
- Video: smooth cinematic aerial shot slowly rising and pulling back as the bus drives away into the sunset, warm light flaring, calm ending.

---

## 4. 목소리 (TTS) 세트

| 목소리 | 설정 | 컷 |
|---|---|---|
| 🎙 내레이터 | 40~50대 남성, 낮고 따뜻한 톤, 느린 속도(0.9배), 문장 사이 0.3초 쉼 | 1~11, 14 |
| 👩 여자 | 20대 후반 여성, 살짝 숨이 찬 톤, 떨리는 목소리, 말끝을 흐리게 | 12, 13 |

**녹음용 대본 (그대로 TTS에 넣기)**

```text
[내레이터]
30년 같은 노선. 오늘이 마지막 운행이다.
그에겐 지켜온 습관이 하나 있었다.
매일 아침, 늘 늦게 뛰어오던 아이.
그는 늘, 10초를 더 기다렸다.
아이는 늘 숨을 헐떡이며 인사했다.
그렇게 10년, 아이는 교복을 입었고—
어느 날부터, 더는 오지 않았다.
그리고 오늘, 마지막 운행.
그 정류장에, 누군가 뛰어오고 있었다.
그는 습관처럼, 10초를 기다렸다.
숨을 헐떡이며, 그때처럼 고개를 숙이는 사람.

[여자]
기사님 덕분에… 한 번도 안 늦었어요.
저, 오늘부터 선생님이에요.

[내레이터]
그 10초가, 한 아이의 인생을 기다려주고 있었다.
```

- 컷 10이 끝나면 **1초 정적**(BGM만)을 두고 컷 11 내레이션을 시작하세요.
- 컷 13 대사 직후 BGM을 가장 크게 올리세요.

---

## 5. BGM (Suno) 프롬프트

- **Title:** The Ten Seconds
- **Style:** `emotional cinematic instrumental, solo felt piano, slow tempo 68 bpm, nostalgic and warm, Korean drama OST mood, soft strings enter at the middle and swell to a gentle climax near the end, no drums, no vocals`
- **Exclude Styles:** `vocals, singing, choir, humming, drums`

> ⚠️ Suno에서 **Instrumental을 ON으로 켜면 가사 칸이 사라집니다.** 아래 두 방법 중 하나를 고르세요.

**방법 A: 구조 태그 사용 (추천, 클라이맥스 위치를 조절하기 쉬움)**
- **Instrumental: OFF**
- 가사 칸에 **태그만** 넣고 가사는 쓰지 않습니다:
```text
[Intro]
[soft solo piano, sparse]

[Verse]
[piano melody, gentle and nostalgic]

[Build]
[low strings slowly join]

[Climax]
[full warm strings and piano, emotional swell]

[Outro]
[single piano notes fading out]

[End]
```
- 보컬이 섞여 나오면 Exclude Styles를 확인하고 다시 생성하세요.

**방법 B: 간단하게**
- **Instrumental: ON**, Style만 입력 (구조는 Suno에 맡김)

- 편집할 때 **Climax가 컷 12~13(0:45~0:55)**에 걸리도록 음악의 시작 위치를 맞추세요.

---

## 6. 효과음

| 컷 | 효과음 |
|---|---|
| 1 | 새벽 새소리, 멀리서 시동 거는 소리 |
| 3~5 | 빗소리, 뛰는 발소리, 버스 문 열리는 "치익" |
| 6 | 창밖 빗소리, 버스 엔진의 낮은 소리 |
| 7 | 바람 소리, 낙엽 굴러가는 소리 |
| 9 | 뛰는 발소리, 키링이 짤랑이는 소리 |
| 11 | 버스 문 "치익" (컷 5와 같은 소리를 써서 수미상관) |
| 14 | 버스 엔진 소리가 멀어지며 페이드아웃 |

### 볼륨 밸런스 (캡컷 기준, 대략값)
| 트랙 | 볼륨 |
|---|---|
| 🎙 내레이터 / 👩 여자 | 0dB (기준) |
| BGM | -18dB → **컷 13 대사가 끝난 직후부터 -10dB로 올림** → 컷 14 끝에서 페이드아웃 |
| 빗소리·바람 등 환경음 | -28dB |
| 버스 문 "치익", 발소리 등 포인트 효과음 | -14dB 안팎 |

- 숫자보다 **귀로 확인하는 게 우선**이에요. 휴대폰 스피커로 한 번, 이어폰으로 한 번 들어 보고 대사가 묻히지 않는지 보세요.
- 대사가 나올 때 BGM을 자동으로 살짝 낮추는 캡컷 기능(오디오 더킹)이 있으면 함께 쓰세요.

## 7. 업로드 세트
- 제목: **30년 버스 기사가 매일 10초를 기다린 이유**
- 설명: 매일 늦던 아이를 위해 기다려준 10초. 마지막 운행 날, 그 10초가 돌아왔다.
- 해시태그: #쇼츠 #감동 #감동영상 #버스기사 #마지막운행 #뭉클 #눈물주의 #AI영화
- 썸네일: close-up, an elderly Korean bus driver in a navy cap smiling with teary eyes, holding a small bouquet of white and yellow flowers, warm golden sunlight through the bus window, emotional, cinematic, photorealistic, vertical 9:16

## 8. 체크리스트
- [ ] 버스와 정류장이 한국식으로 나왔는가 (서양식 스쿨버스나 이층버스가 아닌지)
- [ ] 회상 기사(컷 4)와 현재 기사가 같은 사람으로 보이는가
- [ ] 컷 3·9에서 노란 곰 키링이 9:16 화면에서 또렷이 보이는가
- [ ] 컷 5와 컷 11의 구도가 같은가
- [ ] 컷 12·13에서 입이 움직이지 않는가 (보이스오버와 충돌 방지)
- [ ] 간판이나 표지판에 깨진 한글이 보이면 흐리게 처리하거나 자르기
