# 편의점 11시 — 통합 프롬프트 (복사해서 바로 쓰는 버전)

## 사용법
> **네거티브 포함 버전:** 아래 STEP·씬 프롬프트는 끝에 `Avoid:` 네거티브가 이미 붙어 있다. 코드 블록 하나를 통째로 복사해서 붙여넣으면 끝. (툴에 Negative 칸이 따로 있으면 `Avoid:` 줄만 잘라서 그 칸에 넣어도 된다.)

1. **STEP 1**로 지우·현우 레퍼런스 시트를 **각각 따로** 만들고 마음에 드는 것 하나씩 고른다.
2. 씬 이미지를 만들 때 해당 인물의 레퍼런스 이미지를 **항상 첨부**한다. 둘 다 나오는 씬은 두 장 모두 첨부.
3. 씬마다 **[이미지 프롬프트] + [네거티브]** 로 첫 프레임을 만든다. 얼굴이 레퍼런스와 다르면 1회 재생성.
4. 통과한 첫 프레임을 넣고 **[영상 프롬프트]** 로 영상을 만든다.
5. 대사·자막·"다음 편: 우산"은 편집에서 넣는다(생성 화면에 글자 넣지 않음).

---

## 공통 네거티브 — 이미지용 (모든 이미지에 매번 사용)

STEP 1 레퍼런스 시트와 씬 1~5의 **모든 이미지**에 똑같이 넣는다.

```
different person, face drift, changed face shape, enlarged eyes, slimmed face, V-line chin, sharpened chin, skin whitening, pale porcelain skin, airbrushed skin, plastic skin, beauty filter, heavy makeup, younger-looking face, older-looking face, mirrored mole position, blended faces, face swap, extra fingers, missing fingers, fused fingers, distorted hands, wide-angle face distortion, different outfit, missing name tag, watch on wrong wrist, anime, cartoon, illustration, 3D render, Chinese or Japanese styling, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, subtitles, captions, watermark, low resolution, blurry face
```

**넣는 위치**

| 툴 화면 | 넣는 방법 |
| --- | --- |
| Negative prompt 칸이 따로 있음 | 그 칸에 위 네거티브를 통째로 붙여넣기 |
| 칸이 없음 (프롬프트 칸 하나뿐) | 씬 이미지 프롬프트 맨 끝에 `Avoid:`를 쓰고 그 뒤에 붙이기 |

칸이 없을 때 예시:
```
...9:16 vertical, 4K. Avoid: different person, face drift, changed face shape, enlarged eyes, ...(위 네거티브 전체)
```

## 공통 네거티브 — 영상용 (선택)

영상 프롬프트마다 "no morphing, no face change, no on-screen text"가 이미 들어 있어서 **필수는 아니다.** 영상 툴에 네거티브 칸이 있을 때만 아래 짧은 버전을 넣는다.

```
face morphing, face change, different person, extra fingers, distorted hands, on-screen text, subtitles, watermark
```

> 스타일 문구(Real camera photo, 렌즈, 9:16 등)는 각 씬 프롬프트 안에 이미 들어 있으므로 따로 붙이지 않는다.

---

## STEP 1-A. 지우 레퍼런스 시트 (참조 이미지 없이)

```
Hyper-realistic photo of ONE person: Jiwoo, 24-year-old modern South Korean woman.
Face: soft oval face with natural cheek fullness, medium almond-shaped dark brown eyes with natural size and average spacing, natural thin in-out double eyelids tapered at the inner corner, thin natural straight brows with a soft arch at the outer third, straight soft nose bridge of medium length with a small rounded tip, natural medium-full lips with a slightly fuller lower lip and muted rose tint, gentle rounded jawline with a soft rounded chin, light warm beige skin tone, small mole under her LEFT eye, light freckles across the nose bridge, natural rounded hairline with a side part on her right, apparent age 24.
Skin: visible natural pores, fine peach fuzz, slight under-eye shadow from night shift, minimal makeup, no porcelain or plastic filter look.
Hair: shoulder-length dark brown layered cut, soft curtain bangs, slightly wavy ends, right side tucked behind ear, a few loose strands on cheek, natural shine, no bright dye.
Outfit: cream ivory knit cardigan, loose fit, ribbed cuffs, top 2 buttons undone; plain white crew-neck T-shirt; dark green convenience store apron with a small white Hangul name tag "지우" on her left chest, strings tied at back; light blue straight-fit jeans with slightly faded knees; white low-top canvas sneakers with slightly worn soles; thin silver stud earrings, no necklace, no rings.
Layout: character reference sheet on a clean light gray studio background — FRONT full-body, SIDE profile, 3/4 view, head-and-shoulders close-up. Identical face, identical mole position and identical outfit in every view.
Real camera photo, 50mm and 85mm lens, soft even studio lighting with natural soft shadows, believable hands, accurate Hangul only.
Avoid: different person, face drift, changed face shape, enlarged eyes, slimmed face, V-line chin, sharpened chin, skin whitening, pale porcelain skin, airbrushed skin, plastic skin, beauty filter, heavy makeup, younger-looking face, older-looking face, mirrored mole position, blended faces, face swap, extra fingers, missing fingers, fused fingers, distorted hands, wide-angle face distortion, different outfit, missing name tag, watch on wrong wrist, anime, cartoon, illustration, 3D render, Chinese or Japanese styling, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, subtitles, captions, watermark, low resolution, blurry face
```

## STEP 1-B. 현우 레퍼런스 시트 (참조 이미지 없이, 지우와 별도 생성)

```
Hyper-realistic photo of ONE person: Hyunwoo, 26-year-old modern South Korean man.
Face: clean oval face with a slightly longer lower third, medium-narrow dark brown eyes with slightly upturned outer corners and average spacing, inner (in-fold) double eyelids visible only at the outer half, medium-thick straight dark brows, straight nose with a medium-high bridge and slightly defined tip, natural medium lips with a defined cupid's bow, defined but soft jawline with a straight chin, medium warm beige skin tone, faint acne scar on his RIGHT cheek, light stubble shadow on chin, straight natural hairline, apparent age 26.
Skin: visible pores, natural skin texture, no makeup.
Hair: short black Korean two-block cut, longer textured top, neatly faded sides, front fringe falling over forehead.
Outfit: charcoal gray oversized hooded windbreaker zipped halfway; black crew-neck T-shirt; dark navy straight-fit chinos; black-and-white low-top sneakers; black digital watch on his LEFT wrist, no other accessories.
Layout: character reference sheet on a clean light gray studio background — FRONT full-body, SIDE profile, 3/4 view, head-and-shoulders close-up. Identical face, identical scar position and identical outfit in every view.
Real camera photo, 50mm and 85mm lens, soft even studio lighting with natural soft shadows, believable hands.
Avoid: different person, face drift, changed face shape, enlarged eyes, slimmed face, V-line chin, sharpened chin, skin whitening, pale porcelain skin, airbrushed skin, plastic skin, beauty filter, heavy makeup, younger-looking face, older-looking face, mirrored mole position, blended faces, face swap, extra fingers, missing fingers, fused fingers, distorted hands, wide-angle face distortion, different outfit, missing name tag, watch on wrong wrist, anime, cartoon, illustration, 3D render, Chinese or Japanese styling, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, subtitles, captions, watermark, low resolution, blurry face
```

---

## SCENE 1 — 비 오는 편의점 외관 (00:00–00:05) · 첨부: 지우

**이미지**
```
IDENTITY LOCK — Jiwoo: same person as the attached reference image, clearly recognizable. Keep unchanged: face outline, eye shape, size and spacing, eyelid fold, eyebrows, nose length and tip, lip shape, jaw and chin, light warm beige skin tone, small mole under her left eye, light freckles on nose bridge, apparent age 24, hairline. Shoulder-length dark brown layered hair with curtain bangs, right side tucked behind ear. Outfit unchanged: cream ivory knit cardigan, white crew-neck T-shirt, dark green convenience store apron with small white Hangul name tag "지우" on her left chest, light blue straight jeans, white canvas sneakers, thin silver stud earrings.
Scene: rainy night in Seoul, exterior of a small modern South Korean convenience store, warm interior light glowing through rain-streaked glass, wet asphalt reflections, Jiwoo visible inside behind the counter as a small mid-ground figure, cool blue night outside vs warm 3200K light inside, shallow depth of field with raindrops on the glass in the foreground.
Real camera photo, 35mm lens, natural lens perspective, real light and shadows, natural skin texture, no beauty retouching, Hangul signage only, no real brand logos, 9:16 vertical, 4K.
Avoid: different person, face drift, changed face shape, enlarged eyes, slimmed face, V-line chin, sharpened chin, skin whitening, pale porcelain skin, airbrushed skin, plastic skin, beauty filter, heavy makeup, younger-looking face, older-looking face, mirrored mole position, blended faces, face swap, extra fingers, missing fingers, fused fingers, distorted hands, wide-angle face distortion, different outfit, missing name tag, watch on wrong wrist, anime, cartoon, illustration, 3D render, Chinese or Japanese styling, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, subtitles, captions, watermark, low resolution, blurry face
```

**영상**
```
Slow tilt up from raindrops on the glass to the glowing store sign, then a slow dolly-in toward the window where Jiwoo stands behind the counter. Steady rain, light reflections shimmering on the wet street. Jiwoo stays mostly still, small natural breathing. Keep her face, hair and outfit identical to the first frame. No morphing, no face change, no on-screen text. 5 seconds, 9:16.
Avoid: face morphing, face change, different person, extra fingers, distorted hands, on-screen text, subtitles, watermark
```

---

## SCENE 2 — 손 인서트 (00:05–00:12) · 첨부: 지우

**이미지**
```
Same Jiwoo as the attached reference image — only her hands and forearms are visible: cream ivory knit cardigan with ribbed cuffs, light warm beige skin, short natural unpolished nails, no rings.
Scene: close-up insert of her hands arranging triangle kimbap with Hangul packaging on a Korean convenience store shelf, a cup ramen and a warm canned coffee nearby, warm shelf light, plastic wrapper texture, five natural fingers on each hand.
Real camera photo, 100mm macro lens, shallow depth of field, real light and shadows, natural skin texture, Hangul labels only, no real brand logos, 9:16 vertical, 4K.
Avoid: different person, face drift, changed face shape, enlarged eyes, slimmed face, V-line chin, sharpened chin, skin whitening, pale porcelain skin, airbrushed skin, plastic skin, beauty filter, heavy makeup, younger-looking face, older-looking face, mirrored mole position, blended faces, face swap, extra fingers, missing fingers, fused fingers, distorted hands, wide-angle face distortion, different outfit, missing name tag, watch on wrong wrist, anime, cartoon, illustration, 3D render, Chinese or Japanese styling, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, subtitles, captions, watermark, low resolution, blurry face
```

**영상**
```
Slow pan following Jiwoo's hands as she places triangle kimbap neatly on the shelf, then lightly touches a cup ramen and wraps her fingers around a warm canned coffee. Natural, unhurried finger movement. Cardigan cuffs unchanged. Five fingers per hand at all times, no extra fingers, no on-screen text. 7 seconds, 9:16.
Avoid: face morphing, face change, different person, extra fingers, distorted hands, on-screen text, subtitles, watermark
```

---

## SCENE 3 — 재회 투샷 (00:12–00:22) · 첨부: 지우 + 현우

**이미지 (투샷)**
```
IDENTITY LOCK — Jiwoo: same person as the attached Jiwoo reference image, clearly recognizable. Keep unchanged: face outline, eye shape, size and spacing, eyelid fold, eyebrows, nose length and tip, lip shape, jaw and chin, light warm beige skin tone, small mole under her left eye, light freckles on nose bridge, apparent age 24, hairline. Shoulder-length dark brown layered hair with curtain bangs, right side tucked behind ear. Outfit unchanged: cream ivory knit cardigan, white crew-neck T-shirt, dark green convenience store apron with small white Hangul name tag "지우" on her left chest.
IDENTITY LOCK — Hyunwoo: same person as the attached Hyunwoo reference image, clearly recognizable. Keep unchanged: face outline, eye shape, size and spacing, inner eyelid fold, eyebrows, nose length and tip, lip shape, jaw and chin, medium warm beige skin tone, faint acne scar on his right cheek, apparent age 26, hairline. Short black two-block haircut, rain-wet. Outfit unchanged: charcoal gray hooded windbreaker zipped halfway and wet from rain, black crew-neck T-shirt, dark navy chinos, black digital watch on left wrist.
Scene: inside a Korean convenience store at night. Hyunwoo on the RIGHT, just stepping in through the glass door, rain on his hair and jacket, holding a wet transparent umbrella. Jiwoo on the LEFT behind the counter, surprised, their eyes meeting. Hangul shelf signs softly blurred in the background, fluorescent light mixed with warm light.
Real camera photo, 35mm lens medium two-shot at eye level, natural lens perspective, real light and shadows, natural skin texture, no beauty retouching, Hangul only, no real brand logos, 9:16 vertical, 4K. Do not blend or swap the two faces.
Avoid: different person, face drift, changed face shape, enlarged eyes, slimmed face, V-line chin, sharpened chin, skin whitening, pale porcelain skin, airbrushed skin, plastic skin, beauty filter, heavy makeup, younger-looking face, older-looking face, mirrored mole position, blended faces, face swap, extra fingers, missing fingers, fused fingers, distorted hands, wide-angle face distortion, different outfit, missing name tag, watch on wrong wrist, anime, cartoon, illustration, 3D render, Chinese or Japanese styling, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, subtitles, captions, watermark, low resolution, blurry face
```

**이미지 (지우 클로즈업 컷인)**
```
IDENTITY LOCK — Jiwoo: same person as the attached reference image, clearly recognizable. Keep unchanged: face outline, eye shape, size and spacing, eyelid fold, eyebrows, nose length and tip, lip shape, jaw and chin, light warm beige skin tone, small mole under her left eye, light freckles on nose bridge, apparent age 24, hairline. Shoulder-length dark brown layered hair with curtain bangs, right side tucked behind ear. Cream ivory knit cardigan and dark green apron visible at the bottom of the frame.
Scene: close-up of Jiwoo's face behind a convenience store counter, surprised, lips slightly parted, eyes glistening slightly, soft warm store light from the side.
Real camera photo, 85mm lens at eye level, shallow depth of field, real light and shadows, visible pores and fine peach fuzz, no beauty retouching, 9:16 vertical, 4K.
Avoid: different person, face drift, changed face shape, enlarged eyes, slimmed face, V-line chin, sharpened chin, skin whitening, pale porcelain skin, airbrushed skin, plastic skin, beauty filter, heavy makeup, younger-looking face, older-looking face, mirrored mole position, blended faces, face swap, extra fingers, missing fingers, fused fingers, distorted hands, wide-angle face distortion, different outfit, missing name tag, watch on wrong wrist, anime, cartoon, illustration, 3D render, Chinese or Japanese styling, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, subtitles, captions, watermark, low resolution, blurry face
```

**영상 (투샷)**
```
The glass door opens with rain falling behind him. Hyunwoo steps in, shakes rain off lightly and leans the transparent umbrella against the side of the counter. He looks up and both freeze, holding eye contact. Subtle breathing, restrained natural expressions, no exaggerated acting. Quick whip pan from the door to the two-shot at the start. Keep both faces, hair and outfits identical to the first frame. No morphing, no face swap, no on-screen text. 6 seconds, 9:16.
Avoid: face morphing, face change, different person, extra fingers, distorted hands, on-screen text, subtitles, watermark
```

**영상 (지우 클로즈업)**
```
Jiwoo's eyes widen slightly, she takes a small breath and her lips part as if to say a word. Very slight push-in. Keep her face identical to the first frame, no morphing, no on-screen text. 3 seconds, 9:16.
Avoid: face morphing, face change, different person, extra fingers, distorted hands, on-screen text, subtitles, watermark
```

---

## SCENE 4 — 삼각김밥 건네기 (00:22–00:32) · 첨부: 지우 + 현우

**이미지 (오버숄더)**
```
IDENTITY LOCK — Jiwoo: same person as the attached Jiwoo reference image, clearly recognizable. Keep unchanged: face outline, eye shape, size and spacing, eyelid fold, eyebrows, nose length and tip, lip shape, jaw and chin, light warm beige skin tone, small mole under her left eye, light freckles on nose bridge, apparent age 24, hairline. Shoulder-length dark brown layered hair with curtain bangs, right side tucked behind ear. Outfit unchanged: cream ivory knit cardigan, white crew-neck T-shirt, dark green convenience store apron with small white Hangul name tag "지우" on her left chest.
IDENTITY LOCK — Hyunwoo: same person as the attached Hyunwoo reference image. Short black rain-wet two-block haircut, charcoal gray hooded windbreaker wet from rain, black digital watch on left wrist.
Scene: over-the-shoulder shot from behind Hyunwoo's RIGHT shoulder — the back of his wet head and his windbreaker shoulder soft-blurred in the foreground on the right. Focus on Jiwoo's face on the LEFT behind the counter, a warm small smile and natural slight blush. Hyunwoo's hand holds out a tuna mayo triangle kimbap with a Hangul label across the counter.
Real camera photo, 50mm lens, shallow depth of field, warm store light, real light and shadows, natural skin texture, no beauty retouching, Hangul only, no real brand logos, 9:16 vertical, 4K. Do not blend or swap the two faces.
Avoid: different person, face drift, changed face shape, enlarged eyes, slimmed face, V-line chin, sharpened chin, skin whitening, pale porcelain skin, airbrushed skin, plastic skin, beauty filter, heavy makeup, younger-looking face, older-looking face, mirrored mole position, blended faces, face swap, extra fingers, missing fingers, fused fingers, distorted hands, wide-angle face distortion, different outfit, missing name tag, watch on wrong wrist, anime, cartoon, illustration, 3D render, Chinese or Japanese styling, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, subtitles, captions, watermark, low resolution, blurry face
```

**이미지 (손 인서트)**
```
Close-up insert across a convenience store counter: a man's hand with a black digital watch on his left wrist and a wet charcoal windbreaker sleeve hands a triangle kimbap with a Hangul label to a woman's hand with a cream ivory knit cardigan ribbed cuff and short natural nails, no rings. Five natural fingers on each hand, fingers almost touching. Warm store light.
Real camera photo, 100mm macro lens, shallow depth of field, real light and shadows, natural skin texture, Hangul label only, no real brand logos, 9:16 vertical, 4K.
Avoid: different person, face drift, changed face shape, enlarged eyes, slimmed face, V-line chin, sharpened chin, skin whitening, pale porcelain skin, airbrushed skin, plastic skin, beauty filter, heavy makeup, younger-looking face, older-looking face, mirrored mole position, blended faces, face swap, extra fingers, missing fingers, fused fingers, distorted hands, wide-angle face distortion, different outfit, missing name tag, watch on wrong wrist, anime, cartoon, illustration, 3D render, Chinese or Japanese styling, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, subtitles, captions, watermark, low resolution, blurry face
```

**영상 (오버숄더)**
```
Hyunwoo slowly slides the triangle kimbap across the counter toward Jiwoo. She hesitates for a beat, looks down at it, then back up at him with a small shy smile. Gentle handheld micro-movement, slow and quiet mood. Keep both faces, hair and outfits identical to the first frame. No morphing, no face swap, no on-screen text. 6 seconds, 9:16.
Avoid: face morphing, face change, different person, extra fingers, distorted hands, on-screen text, subtitles, watermark
```

**영상 (손 인서트)**
```
His hand pushes the triangle kimbap forward, her fingers reach in and take it, their fingertips brush for a moment. Slow, natural movement. Five fingers per hand at all times, no extra fingers, no on-screen text. 4 seconds, 9:16.
Avoid: face morphing, face change, different person, extra fingers, distorted hands, on-screen text, subtitles, watermark
```

---

## SCENE 5 — 우산 엔딩 (00:32–00:40) · 첨부: 지우 (+현우)

**이미지**
```
IDENTITY LOCK — Jiwoo: same person as the attached reference image. Shoulder-length dark brown layered hair with curtain bangs, now getting wet in the rain. Outfit unchanged: cream ivory knit cardigan, dark green convenience store apron with strings tied at her back, light blue straight jeans, white canvas sneakers.
Scene: back view of Jiwoo running out of the convenience store into the rain on a Seoul street at night, holding a closed transparent umbrella in her right hand. Far ahead on the wet street, a blurred male figure in a charcoal hooded windbreaker walks away. Warm store light spilling out behind her, wet asphalt reflections, cool blue night.
Real camera photo, 35mm lens follow shot from behind, natural lens perspective, real light and shadows, Hangul signage only, no real brand logos, 9:16 vertical, 4K.
Avoid: different person, face drift, changed face shape, enlarged eyes, slimmed face, V-line chin, sharpened chin, skin whitening, pale porcelain skin, airbrushed skin, plastic skin, beauty filter, heavy makeup, younger-looking face, older-looking face, mirrored mole position, blended faces, face swap, extra fingers, missing fingers, fused fingers, distorted hands, wide-angle face distortion, different outfit, missing name tag, watch on wrong wrist, anime, cartoon, illustration, 3D render, Chinese or Japanese styling, Hanzi, Kanji, Hiragana, Katakana, non-Hangul text, garbled Hangul, real brand logos, subtitles, captions, watermark, low resolution, blurry face
```

**영상**
```
Camera follows behind Jiwoo as she runs out into the rain toward the distant figure. She opens the transparent umbrella while running. End on a close-up of the umbrella canopy with raindrops sliding down, warm store light glowing through it. Keep her hair and outfit identical to the first frame, no morphing, no on-screen text. 8 seconds, 9:16.
Avoid: face morphing, face change, different person, extra fingers, distorted hands, on-screen text, subtitles, watermark
```
