# scenepad figure parts catalogue

Every actor is assembled procedurally from parts.
Claude reads the story, derives the properties for each actor,
then builds the SVG from the parts below.
Never copy a template. Always assemble from parts.

---

## Actor properties (derive from story)

For each actor extract:

  role        → accessory to draw on head
  emotion     → face assembly (brows + eyes + mouth + extras)
  action      → body pose (arm positions)
  skin_tone   → one of 6 skin tones below
  hair_style  → one of 5 styles below
  shirt_color → pick from color palette, unique per actor in scene
  pants_color → matching darker shade from same palette entry
  name        → label below feet

Clothing colors must be unique across all actors in the scene.
Skin tones and hair styles can repeat.
Carry all properties across panels — same actor = same colors every panel.

---

## Coordinate system

Each actor is positioned by:
  cx = horizontal center of actor
  cy = vertical center of head circle

All part coordinates below are expressed as offsets from (cx, cy).
Head radius = 34px.
Total actor height from head top to feet: ~200px.

Head top    = cy - 34
Chin        = cy + 34
Neck top    = cy + 34
Neck bottom = cy + 50
Shoulder    = cy + 58
Hip         = cy + 108
Knee        = cy + 148
Feet        = cy + 192

---

## Skin tones

| ID | Name          | Skin hex  | Use for                  |
|----|---------------|-----------|--------------------------|
| S1 | light peach   | #FFDAB9   | default light            |
| S2 | warm beige    | #FDBF8A   | default warm             |
| S3 | golden        | #E8A96A   | medium warm              |
| S4 | caramel       | #C68642   | medium brown             |
| S5 | brown         | #8D5524   | dark brown               |
| S6 | deep          | #4A2912   | deep brown               |

Assign randomly or infer from context. Vary across actors in a scene.
Ears, neck, hands all use same skin hex as face.

---

## Hair styles

| ID | Style         | How to draw                                                        |
|----|---------------|--------------------------------------------------------------------|
| H1 | short dark    | filled path: M cx-32 cy-18 Q cx-28 cy-50 cx cy-50 Q cx+28 cy-50 cx+32 cy-18 Q cx+28 cy-36 cx cy-36 Q cx-28 cy-36 cx-32 cy-18 Z fill=#3D2B1F |
| H2 | short light   | same path, fill=#D4A853                                            |
| H3 | black short   | same path, fill=#1a1a1a                                            |
| H4 | curly red     | four overlapping circles r=12-13 across top of head, fill=#C0392B |
| H5 | long dark     | H1 path PLUS two thick stroke lines down sides: left M cx-30 cy-10 Q cx-36 cy+60 cx-30 cy+100, right mirrored, stroke=#3D2B1F stroke-width=12 stroke-linecap=round |

Draw hair AFTER head circle, BEFORE face parts.
Hair overlaps top of head naturally.

---

## Base body parts (always present)

### Shadow
  ellipse cx=cx cy=cy+200 rx=28 ry=6 fill=#e8e4df

### Legs
  left leg:  rect x=cx-20 y=cy+108 width=16 height=76 rx=8 fill=pants_color
  right leg: rect x=cx+4  y=cy+108 width=16 height=76 rx=8 fill=pants_color

### Shoes
  left shoe:  ellipse cx=cx-12 cy=cy+188 rx=13 ry=7 fill=#222222
  right shoe: ellipse cx=cx+12 cy=cy+188 rx=13 ry=7 fill=#222222

### Torso
  ellipse cx=cx cy=cy+82 rx=32 ry=40 fill=shirt_color

### Collar crease
  path: M cx-14 cy+52 Q cx cy+62 cx+14 cy+52
  fill=none stroke=darker_shirt stroke-width=1.5
  (darker_shirt = pants_color, it is always darker than shirt)

### Neck
  rect x=cx-8 y=cy+34 width=16 height=18 rx=7 fill=skin_hex

### Head
  circle cx=cx cy=cy r=34 fill=skin_hex

### Ears
  left:  circle cx=cx-43 cy=cy r=11 fill=skin_hex
  right: circle cx=cx+43 cy=cy r=11 fill=skin_hex

---

## Arm poses

Replace left/right arm independently. Default = arms relaxed at sides.

### relaxed (default)
  left:  rect x=cx-46 y=cy+58 width=14 height=36 rx=7 fill=shirt_color transform="rotate(-12, cx-39, cy+58)"
         hand: circle cx=cx-50 cy=cy+94 r=10 fill=skin_hex
  right: rect x=cx+32 y=cy+58 width=14 height=36 rx=7 fill=shirt_color transform="rotate(12, cx+39, cy+58)"
         hand: circle cx=cx+50 cy=cy+94 r=10 fill=skin_hex

### pointing right (presenting, directing)
  right: rect x=cx+32 y=cy+44 width=14 height=36 rx=7 fill=shirt_color transform="rotate(38, cx+39, cy+44)"
         hand: circle cx=cx+62 cy=cy+72 r=10 fill=skin_hex

### pointing left
  left: rect x=cx-46 y=cy+44 width=14 height=36 rx=7 fill=shirt_color transform="rotate(-38, cx-39, cy+44)"
        hand: circle cx=cx-62 cy=cy+72 r=10 fill=skin_hex

### arms out / explaining / shrugging
  left:  rect x=cx-52 y=cy+54 width=14 height=36 rx=7 fill=shirt_color transform="rotate(-32, cx-45, cy+54)"
         hand: circle cx=cx-68 cy=cy+78 r=10 fill=skin_hex
  right: rect x=cx+38 y=cy+54 width=14 height=36 rx=7 fill=shirt_color transform="rotate(32, cx+45, cy+54)"
         hand: circle cx=cx+68 cy=cy+78 r=10 fill=skin_hex

### both arms raised / celebrating
  left:  rect x=cx-48 y=cy+36 width=14 height=36 rx=7 fill=shirt_color transform="rotate(-42, cx-41, cy+36)"
         hand: circle cx=cx-68 cy=cy+56 r=10 fill=skin_hex
  right: rect x=cx+34 y=cy+36 width=14 height=36 rx=7 fill=shirt_color transform="rotate(42, cx+41, cy+36)"
         hand: circle cx=cx+68 cy=cy+56 r=10 fill=skin_hex

### arms flung out in shock
  left:  rect x=cx-52 y=cy+48 width=14 height=36 rx=7 fill=shirt_color transform="rotate(-48, cx-45, cy+48)"
         hand: circle cx=cx-72 cy=cy+68 r=10 fill=skin_hex
  right: rect x=cx+38 y=cy+48 width=14 height=36 rx=7 fill=shirt_color transform="rotate(48, cx+45, cy+48)"
         hand: circle cx=cx+72 cy=cy+68 r=10 fill=skin_hex

### arms crossed (stubborn, resistant)
  left:  rect x=cx-16 y=cy+58 width=14 height=36 rx=7 fill=shirt_color transform="rotate(28, cx-9, cy+58)"
         hand: circle cx=cx+10 cy=cy+90 r=10 fill=skin_hex
  right: rect x=cx+2  y=cy+58 width=14 height=36 rx=7 fill=shirt_color transform="rotate(-28, cx+9, cy+58)"
         hand: circle cx=cx-10 cy=cy+90 r=10 fill=skin_hex

### scratching head (confused)
  left:  relaxed (default)
  right: rect x=cx+30 y=cy+34 width=14 height=36 rx=7 fill=shirt_color transform="rotate(-52, cx+37, cy+34)"
         hand: circle cx=cx+18 cy=cy+14 r=10 fill=skin_hex

### typing at laptop
  left:  rect x=cx-44 y=cy+62 width=14 height=32 rx=7 fill=shirt_color transform="rotate(-8, cx-37, cy+62)"
         hand: circle cx=cx-42 cy=cy+94 r=10 fill=skin_hex
  right: rect x=cx+30 y=cy+62 width=14 height=32 rx=7 fill=shirt_color transform="rotate(8, cx+37, cy+62)"
         hand: circle cx=cx+42 cy=cy+94 r=10 fill=skin_hex
  laptop body:  rect x=cx-34 y=cy+94 width=68 height=40 rx=5 fill=#2C2C2C
  laptop screen: rect x=cx-32 y=cy+96 width=64 height=32 rx=3 fill=#1a1a2e
  screen glow:  rect x=cx-32 y=cy+96 width=64 height=32 rx=3 fill=#3D8BFF opacity=0.2
  laptop base:  rect x=cx-38 y=cy+134 width=76 height=6 rx=3 fill=#444
  code line 1:  text x=cx-24 y=cy+112 font-size=7 font-family=monospace fill=#7fff7f
                content: pick 1 from: ">_ deploy" / "git push" / "npm run" / "$ fix"

### on phone
  left:  relaxed (default)
  right: rect x=cx+30 y=cy+36 width=14 height=34 rx=7 fill=shirt_color transform="rotate(-52, cx+37, cy+36)"
         hand: circle cx=cx+18 cy=cy+16 r=10 fill=skin_hex
  phone: rect x=cx+14 y=cy+4 width=12 height=22 rx=3 fill=#2C2C2C
         rect x=cx+15 y=cy+6 width=10 height=16 rx=2 fill=#4a90e2 opacity=0.5

### holding coffee (tired / casual)
  left:  relaxed (default)
  right: rect x=cx+30 y=cy+64 width=14 height=32 rx=7 fill=shirt_color transform="rotate(-14, cx+37, cy+64)"
         hand: circle cx=cx+42 cy=cy+96 r=10 fill=skin_hex
  cup body:   rect x=cx+46 y=cy+90 width=20 height=24 rx=5 fill=#8B4513
  cup handle: path M cx+66 cy+96 Q cx+74 cy+96 cx+74 cy+102 Q cx+74 cy+108 cx+66 cy+108 fill=none stroke=#8B4513 stroke-width=2.5
  cup top:    rect x=cx+47 y=cy+90 width=18 height=6 rx=3 fill=#A0522D
  steam 1:    path M cx+52 cy+88 Q cx+50 cy+80 cx+54 cy+74 fill=none stroke=#ccc stroke-width=1.5 stroke-linecap=round opacity=0.7
  steam 2:    path M cx+60 cy+88 Q cx+58 cy+80 cx+62 cy+73 fill=none stroke=#ccc stroke-width=1.5 stroke-linecap=round opacity=0.5

---

## Accessories (drawn on head, before face parts)

### none
  (draw nothing)

### headset (support, customer service)
  arc:       path M cx-44 cy Q cx-44 cy-26 cx cy-26 Q cx+44 cy-26 cx+44 cy
             fill=none stroke=#1a1a1a stroke-width=3
  left pad:  rect x=cx-50 y=cy-8 width=14 height=18 rx=6 fill=#333
  right pad: rect x=cx+36 y=cy-8 width=14 height=18 rx=6 fill=#333
  mic arm:   path M cx-46 cy+10 Q cx-56 cy+22 cx-58 cy+36 fill=none stroke=#333 stroke-width=2.5 stroke-linecap=round
  mic tip:   circle cx=cx-58 cy=cy+38 r=5 fill=#333

### hard hat (engineer, ops, construction)
  dome:  path M cx-36 cy Q cx-34 cy-30 cx cy-30 Q cx+34 cy-30 cx+36 cy fill=#F5A623
  brim:  rect x=cx-42 y=cy-2 width=84 height=10 rx=5 fill=#E8941A

### crown (executive, CEO, decision-maker)
  path: M cx-20 cy-2 L cx-20 cy-18 L cx-10 cy-10 L cx cy-18 L cx+10 cy-10 L cx+20 cy-18 L cx+20 cy-2 Z
  fill=none stroke=#1a1a1a stroke-width=2

### glasses (analyst, researcher, thoughtful)
  left lens:  circle cx=cx-14 cy=cy rx=0 r=13 fill=none stroke=#1a1a1a stroke-width=2
  right lens: circle cx=cx+14 cy=cy rx=0 r=13 fill=none stroke=#1a1a1a stroke-width=2
  bridge:     line x1=cx-1 y1=cy x2=cx+1 y2=cy stroke=#1a1a1a stroke-width=2
  left arm:   line x1=cx-27 y1=cy x2=cx-46 y2=cy+6 stroke=#1a1a1a stroke-width=2 stroke-linecap=round
  right arm:  line x1=cx+27 y1=cy x2=cx+46 y2=cy+6 stroke=#1a1a1a stroke-width=2 stroke-linecap=round

---

## Eye assemblies

Eyes drawn AFTER hair, BEFORE brows and mouth.
All eye sets centered on (cx-16, cy-4) left and (cx+16, cy-4) right.

### normal eyes (base, used in most emotions)
  left white:  ellipse cx=cx-16 cy=cy-4 rx=13 ry=14 fill=white
  right white: ellipse cx=cx+16 cy=cy-4 rx=13 ry=14 fill=white
  left iris:   circle  cx=cx-15 cy=cy-2 r=8  fill=iris_color
  right iris:  circle  cx=cx+17 cy=cy-2 r=8  fill=iris_color
  left pupil:  circle  cx=cx-14 cy=cy-1 r=4  fill=#1a1a1a
  right pupil: circle  cx=cx+18 cy=cy-1 r=4  fill=#1a1a1a
  left shine:  circle  cx=cx-12 cy=cy-5 r=2.2 fill=white
  right shine: circle  cx=cx+20 cy=cy-5 r=2.2 fill=white

### wide eyes (surprised, excited, scared)
  same as normal but:
  left white rx=15 ry=16, right white rx=15 ry=16
  iris r=10, pupil r=5
  extra shine: circle r=1.5 at cx-10 cy-8 and cx+22 cy-8

### squint eyes (determined, suspicious, angry)
  normal eyes, PLUS top lid overdraw:
  left lid:  path M cx-29 cy-10 Q cx-16 cy-2 cx-3 cy-10 fill=skin_hex stroke=none
  right lid: path M cx+3  cy-10 Q cx+16 cy-2 cx+29 cy-10 fill=skin_hex stroke=none

### droopy eyes (sad, tired)
  normal eyes, PLUS heavy top lid:
  left lid:  path M cx-29 cy-12 Q cx-16 cy-4  cx-3 cy-12 fill=skin_hex stroke=none
  right lid: path M cx+3  cy-12 Q cx+16 cy-4  cx+29 cy-12 fill=skin_hex stroke=none
  bags under: path M cx-29 cy+4 Q cx-16 cy+10 cx-3 cy+4 fill=none stroke=skin_hex_dark stroke-width=2.5 stroke-linecap=round opacity=0.6
              path M cx+3  cy+4 Q cx+16 cy+10 cx+29 cy+4 fill=none stroke=skin_hex_dark stroke-width=2.5 stroke-linecap=round opacity=0.6
  (skin_hex_dark = darken skin_hex by 20%)

### star eyes (celebrating, amazed, in love)
  replace iris+pupil+shine with a star polygon each side:
  left star:  polygon points= cx-22,cy-10 cx-20,cy-4 cx-14,cy-4 cx-19,cy cx-17,cy+6 cx-22,cy+2 cx-27,cy+6 cx-25,cy cx-30,cy-4 cx-24,cy-4
              fill=#FFD700 stroke=#E8A000 stroke-width=0.5
  right star: same mirrored at cx+22

### heart eyes (love, adoration, fan)
  replace iris with:
  left heart:  path M cx-18 cy-6 Q cx-18 cy-12 cx-14 cy-12 Q cx-10 cy-12 cx-10 cy-6 L cx-14 cy-2 Z fill=#FF4D6D
  right heart: path M cx+10 cy-6 Q cx+10 cy-12 cx+14 cy-12 Q cx+18 cy-12 cx+18 cy-6 L cx+14 cy-2 Z fill=#FF4D6D

---

## Iris colors (assign one per actor, keep consistent)

  blue:   #3D6BE8
  green:  #27AE60
  hazel:  #8B6914
  brown:  #5C3317
  purple: #7B2D8B
  teal:   #1A9E8B
  grey:   #6B7280

---

## Brow assemblies

Drawn above eyes. Brows are the primary emotion signal.

### neutral (relaxed)
  left:  path M cx-29 cy-18 Q cx-16 cy-22 cx-3 cy-18 fill=none stroke=hair_color stroke-width=2.5 stroke-linecap=round
  right: path M cx+3  cy-18 Q cx+16 cy-22 cx+29 cy-18 fill=none stroke=hair_color stroke-width=2.5 stroke-linecap=round

### raised (happy, excited, surprised)
  left:  path M cx-29 cy-22 Q cx-16 cy-28 cx-3 cy-22 fill=none stroke=hair_color stroke-width=2.8 stroke-linecap=round
  right: path M cx+3  cy-22 Q cx+16 cy-28 cx+29 cy-22 fill=none stroke=hair_color stroke-width=2.8 stroke-linecap=round

### angry V (angry, furious)
  left:  line x1=cx-29 y1=cy-18 x2=cx-3 y2=cy-10 stroke=#1a1a1a stroke-width=3.5 stroke-linecap=round
  right: line x1=cx+29 y1=cy-18 x2=cx+3 y2=cy-10 stroke=#1a1a1a stroke-width=3.5 stroke-linecap=round

### worried angled (worried, scared, sad)
  left:  path M cx-29 cy-16 Q cx-20 cy-24 cx-3 cy-16 fill=none stroke=hair_color stroke-width=2.8 stroke-linecap=round
  right: path M cx+3  cy-16 Q cx+20 cy-24 cx+29 cy-16 fill=none stroke=hair_color stroke-width=2.8 stroke-linecap=round
  crease: line x1=cx-3 y1=cy-16 x2=cx+3 y2=cy-12 stroke=hair_color stroke-width=1.5 stroke-linecap=round

### heavy flat (determined, tired)
  left:  line x1=cx-29 y1=cy-16 x2=cx-3 y2=cy-14 stroke=#1a1a1a stroke-width=3.5 stroke-linecap=round
  right: line x1=cx+3  y1=cy-14 x2=cx+29 y2=cy-16 stroke=#1a1a1a stroke-width=3.5 stroke-linecap=round

### mismatched (confused)
  left:  path M cx-29 cy-18 Q cx-20 cy-22 cx-3 cy-16 fill=none stroke=hair_color stroke-width=2.8 stroke-linecap=round
  right: path M cx+3  cy-14 Q cx+20 cy-20 cx+29 cy-18 fill=none stroke=hair_color stroke-width=2.8 stroke-linecap=round

---

## Mouth assemblies

### big smile with teeth (happy, celebrating)
  outer: path M cx-18 cy+24 Q cx cy+40 cx+18 cy+24 fill=white stroke=#1a1a1a stroke-width=2.5 stroke-linecap=round
  line:  path M cx-18 cy+24 Q cx cy+28 cx+18 cy+24 fill=none stroke=#1a1a1a stroke-width=1.5

### small smile (content, slight happy)
  path M cx-12 cy+26 Q cx cy+34 cx+12 cy+26 fill=none stroke=#1a1a1a stroke-width=2.5 stroke-linecap=round

### huge open grin teeth+tongue (celebrating, excited)
  outer: path M cx-22 cy+22 Q cx cy+44 cx+22 cy+22 fill=white stroke=#1a1a1a stroke-width=2.5 stroke-linecap=round
  line:  path M cx-22 cy+22 Q cx cy+26 cx+22 cy+22 fill=none stroke=#1a1a1a stroke-width=1.5
  tongue: ellipse cx=cx cy=cy+36 rx=10 ry=7 fill=#FF8BA0

### frown (sad, unhappy)
  path M cx-16 cy+30 Q cx cy+22 cx+16 cy+30 fill=none stroke=#1a1a1a stroke-width=2.8 stroke-linecap=round

### strong downward curve (sad)
  path M cx-14 cy+28 Q cx cy+18 cx+14 cy+28 fill=none stroke=#1a1a1a stroke-width=3 stroke-linecap=round

### tight line (angry, determined)
  path M cx-16 cy+26 Q cx cy+24 cx+16 cy+26 fill=#CC8866 stroke=#1a1a1a stroke-width=2 stroke-linecap=round

### clenched downward (furious)
  path M cx-14 cy+28 Q cx cy+22 cx+14 cy+28 fill=none stroke=#1a1a1a stroke-width=3.5 stroke-linecap=round

### open O (surprised)
  ellipse cx=cx cy=cy+28 rx=11 ry=13 fill=white stroke=#1a1a1a stroke-width=2.5
  inner:  ellipse cx=cx cy=cy+30 rx=7 ry=6 fill=#CC6680 opacity=0.6

### wavy (confused, uncertain)
  path M cx-18 cy+26 Q cx-10 cy+20 cx cy+26 Q cx+10 cy+32 cx+18 cy+26 fill=none stroke=#1a1a1a stroke-width=2.5 stroke-linecap=round

### slight frown open (tired, meh)
  path M cx-12 cy+26 Q cx cy+22 cx+12 cy+26 fill=none stroke=#1a1a1a stroke-width=2 stroke-linecap=round

### small open worried
  path M cx-12 cy+26 Q cx cy+20 cx+12 cy+26 fill=none stroke=#1a1a1a stroke-width=2.5 stroke-linecap=round

---

## Emotion extras (floating elements near head)

### sweat drops (worried, stressed, nervous)
  large drop: path M cx+38 cy-28 Q cx+42 cy-38 cx+48 cy-28 Q cx+48 cy-18 cx+38 cy-18 Z fill=#89CFF0 opacity=0.85
  small drop: path M cx+44 cy-14 Q cx+46 cy-20 cx+50 cy-14 Q cx+50 cy-8 cx+44 cy-8 Z  fill=#89CFF0 opacity=0.6

### anger vein (angry)
  path M cx+20 cy-36 L cx+26 cy-44 L cx+32 cy-36 L cx+38 cy-44 fill=none stroke=#FF4444 stroke-width=2.2 stroke-linecap=round stroke-linejoin=round

### steam from ears (very angry)
  left steam 1:  path M cx-46 cy-8 Q cx-52 cy-18 cx-46 cy-28 fill=none stroke=#FF8888 stroke-width=2.2 stroke-linecap=round opacity=0.7
  left steam 2:  path M cx-50 cy-6 Q cx-58 cy-18 cx-52 cy-30 fill=none stroke=#FF8888 stroke-width=1.5 stroke-linecap=round opacity=0.5
  right steam 1: path M cx+46 cy-8 Q cx+52 cy-18 cx+46 cy-28 fill=none stroke=#FF8888 stroke-width=2.2 stroke-linecap=round opacity=0.7
  right steam 2: path M cx+50 cy-6 Q cx+58 cy-18 cx+52 cy-30 fill=none stroke=#FF8888 stroke-width=1.5 stroke-linecap=round opacity=0.5

### red face flush (angry, embarrassed)
  circle cx=cx cy=cy r=34 fill=#FF6B6B opacity=0.22
  (draw over head circle, before face parts)

### cheek blush (happy, excited, embarrassed)
  left:  ellipse cx=cx-26 cy=cy+10 rx=9 ry=5 fill=#FFB6A3 opacity=0.6
  right: ellipse cx=cx+26 cy=cy+10 rx=9 ry=5 fill=#FFB6A3 opacity=0.6

### sparkles (celebrating)
  four small star text elements positioned around head:
  text at cx-36 cy-40: ✦ font-size=14 fill=#FFD700
  text at cx+30 cy-44: ✦ font-size=12 fill=#FFD700
  text at cx+40 cy-20: ✦ font-size=10 fill=#FFB6C1
  text at cx-40 cy-20: ✦ font-size=10 fill=#FFB6C1

### ZZZ (tired, sleeping)
  text at cx+36 cy-22: z  font-size=12 font-weight=600 fill=#9999cc opacity=0.8
  text at cx+44 cy-34: z  font-size=14 font-weight=600 fill=#9999cc opacity=0.7
  text at cx+52 cy-48: z  font-size=16 font-weight=600 fill=#9999cc opacity=0.6

### question mark (confused)
  text at cx+38 cy-36: ? font-size=22 font-weight=700 fill=#1a1a1a

### double exclamation (shocked, surprised)
  text at cx cy-48: !! font-size=20 font-weight=700 fill=#1a1a1a text-anchor=middle

### hearts (excited, love, fan)
  text at cx-38 cy-42: ♥ font-size=13 fill=#FF6B9D
  text at cx+32 cy-46: ♥ font-size=15 fill=#FF6B9D

### tear drops (sad, crying)
  left tear:  path M cx-22 cy+16 Q cx-20 cy+8 cx-16 cy+16 Q cx-16 cy+26 cx-22 cy+26 Z fill=#89CFF0 opacity=0.9
  right tear: path M cx+16 cy+18 Q cx+18 cy+10 cx+22 cy+18 Q cx+22 cy+28 cx+16 cy+28 Z fill=#89CFF0 opacity=0.9

### thought dots (thinking, pondering — leads to thought bubble)
  circle at cx+34 cy+6:  r=3 fill=#cccccc
  circle at cx+42 cy-8:  r=4 fill=#cccccc
  circle at cx+48 cy-22: r=5 fill=#cccccc

---

## Emotion → parts lookup table

| Emotion      | Eyes    | Brows         | Mouth                    | Extras                              | Face flush | Blush |
|--------------|---------|---------------|--------------------------|-------------------------------------|------------|-------|
| happy        | normal  | raised        | big smile with teeth     | sparkles (optional)                 | none       | yes   |
| excited      | wide    | raised        | huge open grin+tongue    | hearts, sparkles                    | none       | yes   |
| celebrating  | star    | raised        | huge open grin+tongue    | sparkles                            | none       | yes   |
| angry        | squint  | angry V       | clenched downward        | anger vein, steam from ears         | red        | no    |
| furious      | squint  | angry V       | clenched downward        | anger vein, steam, vein on forehead | red+strong | no    |
| worried      | normal  | worried angled| small open worried       | sweat drops                         | none       | no    |
| stressed     | normal  | worried angled| wavy                     | sweat drops x2                      | none       | no    |
| sad          | droopy  | worried angled| strong downward curve    | tear drops                          | blue tinge | no    |
| surprised    | wide    | raised high   | open O                   | !! above head                       | none       | no    |
| confused     | normal  | mismatched    | wavy                     | ? above head                        | none       | no    |
| tired        | droopy  | heavy flat    | slight frown open        | ZZZ, coffee in hand                 | none       | no    |
| determined   | squint  | heavy flat    | tight line               | none                                | none       | no    |
| excited      | wide    | raised        | huge open grin+tongue    | hearts, sparkles                    | none       | yes   |
| neutral      | normal  | neutral       | small smile              | none                                | none       | no    |
| thinking     | normal  | neutral       | small smile              | thought dots                        | none       | no    |

---

## Clothing color palette (12 options)

Pick shirt_color + pants_color as a pair. Each actor gets a unique pair.
Never repeat the same shirt color in one scene.

| ID | Shirt      | Pants       |
|----|------------|-------------|
| C1 | #5B8DEF    | #2C3E6B     |
| C2 | #F4845F    | #8B3A2A     |
| C3 | #50C878    | #1E5C38     |
| C4 | #9B7FD4    | #4A2D8A     |
| C5 | #F5C842    | #8B6E00     |
| C6 | #F078A8    | #8B2252     |
| C7 | #4ECDC4    | #1A6B65     |
| C8 | #FF8C42    | #8B4200     |
| C9 | #E85D5D    | #8B1A1A     |
| C10| #7BC8A4    | #2D6B52     |
| C11| #5C6BC0    | #2A3580     |
| C12| #A0785A    | #4A2F1A     |

---

## Positioning guide

Panel width = 640. Place actors at these cx values:

| Actors | cx values                              |
|--------|----------------------------------------|
| 1      | 320                                    |
| 2      | 180, 460                               |
| 3      | 120, 320, 520                          |
| 4      | 100, 250, 390, 540                     |
| 5      | 80, 208, 320, 432, 560                 |

cy = panel_top + 140 for standard panels (220px tall).
This gives ~106px above head center for bubbles, ~80px below for feet+label.

Actor label: text cx cy+200 text-anchor=middle font-size=11 fill=#aaaaaa

---

## Assembly order (draw in this sequence)

1. shadow
2. legs
3. shoes
4. torso + collar
5. arms (both)
6. hands
7. neck
8. head circle
9. head flush/tint if any (anger red, sad blue)
10. ears
11. hair
12. accessory (headset/hat/crown/glasses)
13. eyes (whites + iris + pupils + shine)
14. eye overlays (lids for squint/droopy)
15. brows
16. mouth
17. blush if any
18. floating extras (sweat, vein, sparkles, ZZZ, ?, !!)
19. actor label

---

## clipPath — always wrap actors in panel clip

Every actor group must be wrapped in a clipPath matching its panel rect.
This prevents any part (feet, arms, floating extras) from rendering outside the panel.

  <defs>
    <clipPath id="panel-1-clip">
      <rect x="0" y="panel_top" width="640" height="220" rx="12"/>
    </clipPath>
  </defs>
  <g clip-path="url(#panel-1-clip)">
    <!-- all actors in panel 1 go here -->
  </g>

Define one clipPath per panel. Always. No exceptions.