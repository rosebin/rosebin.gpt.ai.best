# 편의점 11시 — 통합 프롬프트 v3 (복사해서 바로 쓰는 버전)

## 사용법
> **네거티브 포함 버전:** 모든 프롬프트 끝에 `Avoid:` 네거티브가 이미 붙어 있다. 코드 블록 하나를 통째로 복사해서 붙여넣으면 끝. (툴에 Negative 칸이 따로 있으면 `Avoid:` 줄만 잘라서 그 칸에 넣어도 된다.)

1. **STEP 1**로 지우·현우 레퍼런스 시트를 **각각 따로** 만들고 마음에 드는 것 하나씩 고른다.
2. 씬 이미지를 만들 때 해당 인물의 레퍼런스 이미지를 **항상 첨부**한다. 둘 다 나오는 씬은 두 장 모두 첨부.
3. 첫 프레임 얼굴·체형이 레퍼런스와 다르면 1회 재생성.
4. 통과한 첫 프레임을 넣고 영상 프롬프트로 영상을 만든다.
5. 대사·자막·"다음 편: 우산"은 편집에서 넣는다.

## 씬별 의상 변화 (스토리상 이유가 있는 것만)

40초 전체가 **같은 날 밤, 같은 편의점**이라 기본 의상은 그대로 둔다. 옷이 바뀌면 시청자는 "다른 날"로 읽고, AI 생성에서도 얼굴 일관성이 떨어진다. 대신 이야기가 만드는 변화만 넣었다.

| 씬 | 지우 | 현우 | 이유 |
| --- | --- | --- | --- |
| 1 | 기본 의상 | — | |
| 2 | 기본 의상, **카디건 소매를 팔꿈치 아래까지 걷음** | — | 진열 작업 중 |
| 3 | 기본 의상, 소매 내림 | **후드 쓴 상태, 지퍼 가슴까지, 흠뻑 젖음, 우산 없음** | 우산 없이 비 맞고 옴 → "아직도 비 맞고 다녀?" 대사의 근거 |
| 4 | 기본 의상 | **후드 벗음, 젖은 앞머리가 이마에 붙음.** 계산대 위에 참치마요 + 편의점 투명 우산(새 상품) | 가게 안이라 후드를 벗음. 우산을 사서 일부러 두고 감 |
| 5 | 기본 의상 + **비에 젖기 시작한 머리와 카디건**, 투명 우산 들고 뛰어나감 | 멀리서 **다시 후드 쓰고** 빗속을 걸어감 | 우산을 두고 갔으니 다시 비를 맞음 |

---

## STEP 1-A. 지우 레퍼런스 시트 (참조 이미지 없이)

```
Hyper-realistic photo of ONE person: Jiwoo, 24-year-old beautiful modern South Korean woman, K-drama lead actress look.
Body: slim and slender, 167cm tall, long slender legs, small head, model-like proportions (about 1:8 head-to-body ratio), straight posture.
Face: small slim oval face with a soft tapered jawline and delicate chin, large clear dark brown eyes with natural double eyelids and long lashes, straight slim dark brown brows, slim straight nose with a small refined tip, full soft lips with a natural rose-pink tint, fair warm-ivory Korean skin tone, apparent age 24.
Skin: clear, smooth, even-toned glowing skin with subtle natural texture, no moles, no freckles, no blemishes, light natural makeup (dewy base, soft coral blush, tinted lips).
Hair: glossy dark brown hair just past the shoulders, soft loose waves at the ends, airy see-through bangs, natural center-right part.
Outfit: fitted cropped cream ivory knit cardigan with ribbed cuffs, white slim-fit crew-neck T-shirt, dark green convenience store apron tied snugly at the waist with a small white Hangul name tag "지우" on her left chest, high-waisted light blue slim straight jeans, clean white low-top sneakers, small silver stud earrings.
Layout: character reference sheet on a clean light gray studio background — FRONT full-body head to toe, SIDE profile full-body, 3/4 view, head-and-shoulders close-up. Full-body views shot with the camera at waist height so the legs look naturally long. Identical face, hair, body proportions and outfit in every view.
Real camera photo, 50mm lens for full body, 85mm lens for close-up, soft flattering studio lighting with gentle natural shadows, believable hands, accurate Hangul only.
Avoid: different person, face drift, moles, freckles, acne, blemishes, scars, uneven skin, oily skin, plastic skin, doll-like skin, cartoonish big eyes, short legs, stubby proportions, large head, chubby, baggy oversized clothes, extra fingers, missing fingers, fused fingers, distorted hands, wide-angle distortion, anime, cartoon, illustration, 3D render, Chinese or Japanese styling, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, subtitles, captions, watermark, low resolution, blurry face
```

## STEP 1-B. 현우 레퍼런스 시트 (참조 이미지 없이, 지우와 별도 생성)

```
Hyper-realistic photo of ONE person: Hyunwoo, 26-year-old handsome modern South Korean man, K-drama lead actor look.
Body: tall 184cm, slim athletic build, broad shoulders, long legs, small head, model-like proportions (about 1:8 head-to-body ratio), straight posture.
Face: small face with a sharp clean jawline and defined chin, deep-set dark brown eyes with inner (in-fold) double eyelids and a calm gaze, thick straight dark brows, high straight nose bridge, well-shaped lips, light warm beige Korean skin tone, clean-shaven, apparent age 26.
Skin: clear, smooth, even-toned skin with subtle natural texture, no moles, no blemishes, no scars, no stubble.
Hair: black Korean two-block cut, soft textured top with a comma-style fringe curving over the forehead, neat short sides.
Outfit: charcoal gray hooded windbreaker in a regular fit (not oversized) zipped halfway, black slim crew-neck T-shirt, black slim tapered trousers, clean white leather low-top sneakers, slim black analog watch on his LEFT wrist.
Layout: character reference sheet on a clean light gray studio background — FRONT full-body head to toe, SIDE profile full-body, 3/4 view, head-and-shoulders close-up. Full-body views shot with the camera at waist height so the legs look naturally long. Identical face, hair, body proportions and outfit in every view.
Real camera photo, 50mm lens for full body, 85mm lens for close-up, soft flattering studio lighting with gentle natural shadows, believable hands.
Avoid: different person, face drift, moles, acne, blemishes, scars, stubble, uneven skin, oily skin, plastic skin, doll-like skin, short legs, stubby proportions, large head, chubby, baggy oversized clothes, extra fingers, missing fingers, fused fingers, distorted hands, wide-angle distortion, anime, cartoon, illustration, 3D render, Chinese or Japanese styling, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, subtitles, captions, watermark, low resolution, blurry face
```

---

## SCENE 1 — 비 오는 편의점 외관 (00:00–00:05) · 첨부: 지우

**이미지**
```
IDENTITY LOCK — Jiwoo: same person as the attached reference image, clearly recognizable. Keep unchanged: face shape, eyes and eyelids, brows, nose, lips, jaw and chin, fair warm-ivory clear skin, apparent age 24, hairline, glossy dark brown hair past the shoulders with see-through bangs, slim body with long legs and model-like proportions. Outfit: fitted cropped cream ivory knit cardigan, white slim T-shirt, dark green convenience store apron with small white Hangul name tag "지우" on her left chest, high-waisted light blue slim straight jeans, white sneakers.
Scene: rainy night in Seoul, exterior of a small modern South Korean convenience store, warm interior light glowing through rain-streaked glass, wet asphalt reflections, Jiwoo visible inside standing behind the counter as a mid-ground figure, cool blue night outside vs warm 3200K light inside, raindrops on the glass sharp in the foreground.
Real camera photo, 35mm lens, natural lens perspective, real light and shadows, Hangul signage only, no real brand logos, 9:16 vertical, 4K.
Avoid: different person, face drift, changed face shape, moles, freckles, blemishes, uneven skin, plastic skin, short legs, stubby proportions, large head, baggy oversized clothes, different outfit, missing name tag, distorted hands, wide-angle distortion, anime, cartoon, illustration, 3D render, Chinese or Japanese styling, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, subtitles, captions, watermark, low resolution, blurry face
```

**영상**
```
Slow tilt up from raindrops on the glass to the glowing store sign, then a slow dolly-in toward the window where Jiwoo stands behind the counter. Steady rain, light reflections shimmering on the wet street. Jiwoo tucks a strand of hair behind her ear and looks toward the door. Keep her face, hair, body proportions and outfit identical to the first frame. No morphing, no face change, no on-screen text. 5 seconds, 9:16.
Avoid: face morphing, face change, different person, moles, blemishes, short legs, extra fingers, distorted hands, on-screen text, subtitles, watermark
```

---

## SCENE 2 — 손 인서트 (00:05–00:12) · 첨부: 지우

**이미지**
```
Same Jiwoo as the attached reference image — only her hands and forearms are visible: slim elegant hands with long slender fingers, fair warm-ivory clear skin, short neat nails with a sheer nude polish, no rings, cream ivory knit cardigan sleeves pushed up to just below the elbows.
Scene: close-up insert of her hands arranging triangle kimbap with Hangul packaging on a Korean convenience store shelf, a cup ramen and a warm canned coffee nearby, warm shelf light, crisp plastic wrapper texture, five natural fingers on each hand.
Real camera photo, 100mm macro lens, shallow depth of field, real light and shadows, Hangul labels only, no real brand logos, 9:16 vertical, 4K.
Avoid: extra fingers, missing fingers, fused fingers, distorted hands, chubby hands, moles, blemishes, rough skin, plastic skin, rings, sleeves rolled down, different cardigan, anime, cartoon, illustration, 3D render, Chinese or Japanese text, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, subtitles, watermark, low resolution
```

**영상**
```
Slow pan following Jiwoo's slim hands as she places triangle kimbap neatly on the shelf, then lightly touches a cup ramen and wraps her fingers around a warm canned coffee. Graceful, unhurried finger movement. Cardigan sleeves stay pushed up. Five fingers per hand at all times, no on-screen text. 7 seconds, 9:16.
Avoid: extra fingers, missing fingers, fused fingers, distorted hands, morphing hands, on-screen text, subtitles, watermark
```

---

## SCENE 3 — 재회 투샷 (00:12–00:22) · 첨부: 지우 + 현우

**이미지 (투샷)**
```
IDENTITY LOCK — Jiwoo: same person as the attached Jiwoo reference image, clearly recognizable. Keep unchanged: face shape, eyes and eyelids, brows, nose, lips, jaw and chin, fair warm-ivory clear skin, apparent age 24, hairline, glossy dark brown hair with see-through bangs, slim body. Outfit: fitted cropped cream ivory knit cardigan with sleeves down, white slim T-shirt, dark green convenience store apron with small white Hangul name tag "지우" on her left chest.
IDENTITY LOCK — Hyunwoo: same person as the attached Hyunwoo reference image, clearly recognizable. Keep unchanged: face shape, eyes and inner eyelids, brows, nose, lips, sharp jawline and chin, light warm beige clear skin, clean-shaven, apparent age 26, tall slim athletic build with broad shoulders and long legs. Outfit: charcoal gray hooded windbreaker with the HOOD UP, zipped up to the chest, soaked with rain, black slim tapered trousers, white sneakers, slim black analog watch on his left wrist. He carries NO umbrella. Wet comma-style fringe visible under the hood.
Scene: inside a Korean convenience store at night. Hyunwoo on the RIGHT, standing tall just inside the glass door, rain dripping from his hood and shoulders, rain falling outside behind him. Jiwoo on the LEFT behind the counter, surprised, their eyes meeting. Hangul shelf signs softly blurred in the background, clean fluorescent light mixed with warm light.
Real camera photo, 35mm lens medium-wide two-shot at chest height, natural lens perspective, real light and shadows, Hangul only, no real brand logos, 9:16 vertical, 4K. Do not blend or swap the two faces.
Avoid: different person, face drift, changed face shape, blended faces, face swap, moles, freckles, acne, blemishes, scars, stubble, uneven skin, plastic skin, short legs, stubby proportions, large head, baggy oversized clothes, hood down, umbrella in his hand, different outfit, missing name tag, extra fingers, distorted hands, wide-angle distortion, anime, cartoon, illustration, 3D render, Chinese or Japanese styling, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, subtitles, captions, watermark, low resolution, blurry face
```

**이미지 (지우 클로즈업 컷인)**
```
IDENTITY LOCK — Jiwoo: same person as the attached reference image, clearly recognizable. Keep unchanged: face shape, eyes and eyelids, brows, nose, lips, jaw and chin, fair warm-ivory clear glowing skin, light natural makeup, apparent age 24, hairline, glossy dark brown hair with see-through bangs. Cream ivory knit cardigan and dark green apron visible at the bottom of the frame.
Scene: close-up of Jiwoo's face behind a convenience store counter, surprised, lips slightly parted, eyes glistening slightly, soft warm store light from the side, beautiful soft catchlights in her eyes.
Real camera photo, 85mm lens at eye level, shallow depth of field, real light and shadows, 9:16 vertical, 4K.
Avoid: different person, face drift, changed face shape, moles, freckles, acne, blemishes, uneven skin, oily skin, plastic skin, doll-like skin, cartoonish big eyes, heavy makeup, wide-angle distortion, anime, cartoon, illustration, 3D render, subtitles, captions, watermark, low resolution, blurry face
```

**영상 (투샷)**
```
The glass door opens with rain behind him. Hyunwoo steps in with his hood up, water dripping from the hood and shoulders. He stops and looks up toward the counter, and both freeze, holding eye contact. Subtle breathing, restrained natural expressions, no exaggerated acting. Quick whip pan from the door to the two-shot at the start. Keep both faces, hair, body proportions and outfits identical to the first frame; his hood stays up. No morphing, no face swap, no on-screen text. 6 seconds, 9:16.
Avoid: face morphing, face change, different person, face swap, moles, blemishes, short legs, hood falling down, umbrella appearing, extra fingers, distorted hands, on-screen text, subtitles, watermark
```

**영상 (지우 클로즈업)**
```
Jiwoo's eyes widen slightly, she takes a small breath and her lips part as if to say "오빠". Very slight push-in. Keep her face identical to the first frame, no morphing, no on-screen text. 3 seconds, 9:16.
Avoid: face morphing, face change, different person, moles, blemishes, on-screen text, subtitles, watermark
```

---

## SCENE 4 — 삼각김밥 건네기 (00:22–00:32) · 첨부: 지우 + 현우

**이미지 (오버숄더)**
```
IDENTITY LOCK — Jiwoo: same person as the attached Jiwoo reference image, clearly recognizable. Keep unchanged: face shape, eyes and eyelids, brows, nose, lips, jaw and chin, fair warm-ivory clear glowing skin, apparent age 24, hairline, glossy dark brown hair with see-through bangs, slim body. Outfit: fitted cropped cream ivory knit cardigan, white slim T-shirt, dark green convenience store apron with small white Hangul name tag "지우" on her left chest.
IDENTITY LOCK — Hyunwoo: same person as the attached Hyunwoo reference image. HOOD DOWN now, wet black comma-style fringe sticking to his forehead, broad shoulders, charcoal gray windbreaker wet from rain, slim black analog watch on his left wrist.
Scene: over-the-shoulder shot from behind Hyunwoo's RIGHT shoulder — the back of his wet head and his broad windbreaker shoulder soft-blurred in the foreground on the right. Focus on Jiwoo's face on the LEFT behind the counter, a warm small smile and a natural slight blush. On the counter: a new folded transparent convenience store umbrella with a price sticker. Hyunwoo's hand holds out a tuna mayo triangle kimbap with a Hangul label toward her.
Real camera photo, 50mm lens, shallow depth of field, warm store light, real light and shadows, Hangul only, no real brand logos, 9:16 vertical, 4K. Do not blend or swap the two faces.
Avoid: different person, face drift, changed face shape, blended faces, face swap, moles, freckles, acne, blemishes, scars, uneven skin, plastic skin, hood up, different outfit, missing name tag, missing umbrella on counter, extra fingers, distorted hands, wide-angle distortion, anime, cartoon, illustration, 3D render, Chinese or Japanese styling, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, subtitles, captions, watermark, low resolution, blurry face
```

**이미지 (손 인서트)**
```
Close-up insert across a convenience store counter: a man's large well-shaped hand with a slim black analog watch on his left wrist and a wet charcoal windbreaker sleeve hands a tuna mayo triangle kimbap with a Hangul label to a woman's slim elegant hand with a cream ivory knit cardigan ribbed cuff and short neat nude nails, no rings. Fingers almost touching. A folded transparent umbrella lies on the counter beside them. Five natural fingers on each hand, clear smooth skin. Warm store light.
Real camera photo, 100mm macro lens, shallow depth of field, real light and shadows, Hangul label only, no real brand logos, 9:16 vertical, 4K.
Avoid: extra fingers, missing fingers, fused fingers, distorted hands, chubby hands, moles, blemishes, rough skin, plastic skin, rings, digital watch, anime, cartoon, illustration, 3D render, Chinese or Japanese text, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, subtitles, watermark, low resolution
```

**영상 (오버숄더)**
```
Hyunwoo slowly slides the triangle kimbap across the counter toward Jiwoo. She hesitates for a beat, looks down at it, then back up at him with a small shy smile. Gentle handheld micro-movement, slow and quiet mood. The transparent umbrella stays on the counter. Keep both faces, hair, body proportions and outfits identical to the first frame; his hood stays down. No morphing, no face swap, no on-screen text. 6 seconds, 9:16.
Avoid: face morphing, face change, different person, face swap, moles, blemishes, hood up, umbrella disappearing, extra fingers, distorted hands, on-screen text, subtitles, watermark
```

**영상 (손 인서트)**
```
His hand pushes the triangle kimbap forward, her slim fingers reach in and take it, their fingertips brush for a moment. Slow, natural movement. Five fingers per hand at all times, no on-screen text. 4 seconds, 9:16.
Avoid: extra fingers, missing fingers, fused fingers, distorted hands, morphing hands, on-screen text, subtitles, watermark
```

---

## SCENE 5 — 우산 엔딩 (00:32–00:40) · 첨부: 지우 (+현우)

**이미지**
```
IDENTITY LOCK — Jiwoo: same person as the attached reference image. Glossy dark brown hair past the shoulders starting to get wet in the rain, slim body with long slender legs and model-like proportions. Outfit: fitted cropped cream ivory knit cardigan getting damp, dark green convenience store apron with strings tied at her back, high-waisted light blue slim straight jeans, white sneakers.
Scene: back view of Jiwoo running out of the convenience store into the rain on a Seoul street at night, holding the closed new transparent umbrella in her right hand. Far ahead on the wet street, a tall slim man in a charcoal hooded windbreaker with the hood up walks away in the rain, blurred. Warm store light spilling out behind her, wet asphalt reflections, cool blue night.
Real camera photo, 35mm lens follow shot from behind with the camera at waist height so her legs look long, natural lens perspective, real light and shadows, Hangul signage only, no real brand logos, 9:16 vertical, 4K.
Avoid: different person, short legs, stubby proportions, large head, chubby, baggy oversized clothes, different outfit, open umbrella, distorted hands, extra fingers, wide-angle distortion, anime, cartoon, illustration, 3D render, Chinese or Japanese styling, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, subtitles, captions, watermark, low resolution
```

**영상**
```
Camera follows behind Jiwoo as she runs out into the rain toward the distant tall figure with his hood up. She opens the transparent umbrella while running, her hair moving and getting wet. End on a close-up of the umbrella canopy with raindrops sliding down, warm store light glowing through it. Keep her hair, slim long-legged proportions and outfit identical to the first frame, no morphing, no on-screen text. 8 seconds, 9:16.
Avoid: face morphing, different person, short legs, stubby proportions, distorted hands, extra fingers, on-screen text, subtitles, watermark
```
