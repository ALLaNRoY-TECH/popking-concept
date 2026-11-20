# Popking hero videos: Veo (Gemini) prompts

The hero is wired for one short video per flavour. Save each finished clip as
`popking-concept/videos/<slug>.mp4`. It replaces that flavour's photo automatically:
it plays on its own and moves frame by frame as you scroll.

## Tips for consistent results
- In Veo, use **image-to-video** and upload the matching product photo (links below) as the
  first frame, so the tub, label and lighting match the brand exactly.
- Aspect ratio **1:1** (or 16:9, centre-cropped to square). Length **4–6 s**. No text, no people.
- Keep the camera **locked off** (static tripod). A slow push-in is the most a scroll scrub should get.
- Make every clip end the way it started (seamless loop).

## Master prompt (paste first, then add the flavour line)
> Ultra-premium product commercial, macro cinematography. A single Popking gourmet popcorn tub
> sits on dark black slate in a moody studio, against a deep black backdrop with a soft warm rim light.
> Fresh popcorn bursts up from the tub in slow motion (1000 fps feel), individual kernels tumbling
> through the air, catching the light, then settling back onto the slate. Floating seasoning dust
> catches the light. Shallow depth of field, anamorphic, high contrast, rich blacks,
> luxury car-commercial aesthetic. Static camera with a very slow push-in. Seamless loop. No text, no people.

## Flavour lines
| File (`videos/…`) | Add to master prompt | Reference photo |
|---|---|---|
| `masala.mp4` | Amber-orange rim light. Red chilli powder and whole spices (cumin, star anise, cinnamon) drift in the air. | IMG-8855 |
| `peri-peri.mp4` | Deep red rim light. Fiery red peri peri dust swirls, a lime half and dried chillies on the slate, faint smoke wisps. | IMG-8846 |
| `caramel.mp4` | Golden rim light. Glossy caramel-coated popcorn, a thin ribbon of liquid caramel pours and glistens, sea-salt flakes sparkle. | IMG-8848 |
| `dark-choco-caramel.mp4` | Warm brown rim light. Chocolate-coated popcorn, broken dark chocolate shards and cocoa beans, cocoa powder puff. | IMG-8862 |
| `blueberry-blast.mp4` | Violet rim light. Purple-coated popcorn, fresh blueberries bounce on the slate, fine violet sugar dust. | IMG-8867 |
| `shahi-rasmalai.mp4` | Saffron-gold rim light. Saffron strands, crushed pistachio and cardamom pods float. Royal, festive mood. | IMG-8864 |
| `strawberry-creme.mp4` | Soft pink rim light. Pink-coated popcorn, fresh strawberries, a splash of cream in slow motion. | IMG-8863 |

Reference photos: `https://cdn.shopify.com/s/files/1/0798/6538/1174/files/<ID>.png?width=1600`

## Make the clips scroll-smooth (important)
A scroll scrub needs every frame to be a keyframe, or it will stutter. Re-encode each clip once:

```powershell
ffmpeg -i masala-raw.mp4 -vf "scale=1080:1080:force_original_aspect_ratio=increase,crop=1080:1080" -c:v libx264 -g 1 -crf 22 -preset slow -an -movflags +faststart videos/masala.mp4
```
