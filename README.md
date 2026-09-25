# VISTA

## Satellite Video Tracking

Small targets, weak contrast, motion blur, background clutter, and occlusion make satellite video tracking challenging. The examples below illustrate these conditions across vehicles, ships, trains, and aircraft.

<p align="center">
  <img src="assets/satellite-scenes.jpg" width="720" alt="Satellite video scenes with small targets, weak contrast, clutter, and occlusion">
</p>

## Evaluation

VISTA is evaluated on SatSOT, SV248S, and OOTB. All results follow a one-pass evaluation protocol.

## SatSOT

### Quantitative Results

The plots below show precision and success curves against 15 generic video trackers and 13 satellite video trackers.

![SatSOT results against generic video trackers](assets/satsot-generic-curves.jpg)

![SatSOT results against satellite video trackers](assets/satsot-satellite-curves.jpg)

### Attribute Analysis

The radar plots summarize PR and SR across 11 tracking challenges. VISTA performs particularly well under background clutter, rotation, deformation, and aspect ratio changes. Performance varies across attributes: STAR remains stronger under full occlusion, while tiny objects and similar distractors remain challenging. VISTA is highlighted in red; the values beside each attribute indicate the minimum and maximum scores in the comparison set.

![SatSOT precision and success across tracking attributes](assets/satsot-attributes.jpg)

### Qualitative Results

The examples show tracking results on six SatSOT sequences: Car-52, Car-65, Ship-02, Train-05, Train-12, and Plane-03. Ground-truth boxes are blue, and VISTA predictions are red. The sequences illustrate tracking through urban clutter, weak appearance, and occlusion, including a ship passing beneath a bridge.

![Tracking comparisons on six SatSOT sequences](assets/satsot-tracking-examples.jpg)

## Generalization to SV248S

VISTA achieves the highest SR among the evaluated trackers on SV248S. Its PR ranks second behind SiamTM, indicating competitive center localization alongside improved bounding-box overlap.


![SV248S precision and success curves](assets/sv248s-curves.jpg)

## Generalization to OOTB

VISTA achieves the highest PR and SR among the evaluated trackers on OOTB. Its NPR is close to MemTrack, which obtains the highest normalized precision. The curves report precision, normalized precision, and success from left to right.


![OOTB precision, normalized precision, and success curves](assets/ootb-curves.jpg)
