# VISTA

VISTA is a visual tracking method for moving objects in satellite videos. This page presents its performance on SatSOT, SV248S, and OOTB through quantitative comparisons, benchmark curves, and tracking examples.

## Satellite Video Tracking

Small targets, weak contrast, motion blur, background clutter, and occlusion make satellite video tracking challenging. The examples below illustrate these conditions across vehicles, ships, trains, and aircraft.

<p align="center">
  <img src="assets/satellite-scenes.jpg" width="720" alt="Satellite video scenes with small targets, weak contrast, clutter, and occlusion">
</p>

## Evaluation

VISTA is trained on SatSOT and evaluated on SatSOT, SV248S, and OOTB. Evaluation on SV248S and OOTB assesses cross-dataset generalization. All results follow a one-pass evaluation protocol.

- PR measures center-location accuracy.
- SR is the area under the intersection-over-union success curve.
- NPR, additionally reported on OOTB, is the area under the normalized precision curve.

Higher values indicate better performance. Each table includes the four satellite video trackers with the highest SR on that benchmark, together with SiamCAR and ARTrackV2 as generic video trackers. The curves show the broader comparison sets.

## SatSOT

### Quantitative Results

VISTA achieves the highest PR and SR among the evaluated generic and satellite video trackers on SatSOT.

| Tracker | Type | PR | SR |
|:---|:---|---:|---:|
| SiamCAR | Generic video | 0.587 | 0.441 |
| ARTrackV2 | Generic video | 0.626 | 0.478 |
| MACF | Satellite video | 0.637 | 0.495 |
| RDTracker | Satellite video | 0.646 | 0.501 |
| SiamTITP | Satellite video | 0.649 | 0.513 |
| STAR | Satellite video | 0.639 | 0.537 |
| VISTA | Ours | 0.665 | 0.556 |

The plots below show precision and success curves against 15 generic video trackers and 13 satellite video trackers.

![SatSOT results against generic video trackers](assets/satsot-generic-curves.jpg)

![SatSOT results against satellite video trackers](assets/satsot-satellite-curves.jpg)

### Attribute Analysis

The radar plots summarize PR and SR across 11 tracking challenges. VISTA performs particularly well under background clutter, rotation, deformation, and aspect ratio changes. Performance varies across attributes: STAR remains stronger under full occlusion, while tiny objects and similar distractors remain challenging. VISTA is highlighted in red; the values beside each attribute indicate the minimum and maximum scores in the comparison set.

![SatSOT precision and success across tracking attributes](assets/satsot-attributes.jpg)

### Tracking Speed

VISTA runs at 88.6 frames per second on an NVIDIA RTX 4090, offering a favorable balance between tracking accuracy and speed.

### Qualitative Results

The examples show tracking results on six SatSOT sequences: Car-52, Car-65, Ship-02, Train-05, Train-12, and Plane-03. Ground-truth boxes are blue, and VISTA predictions are red. The sequences illustrate tracking through urban clutter, weak appearance, and occlusion, including a ship passing beneath a bridge.

![Tracking comparisons on six SatSOT sequences](assets/satsot-tracking-examples.jpg)

## Generalization to SV248S

VISTA achieves the highest SR among the evaluated trackers on SV248S. Its PR ranks second behind SiamTM, indicating competitive center localization alongside improved bounding-box overlap.

| Tracker | Type | PR | SR |
|:---|:---|---:|---:|
| SiamCAR | Generic video | 0.697 | 0.433 |
| ARTrackV2 | Generic video | 0.524 | 0.224 |
| RAMC | Satellite video | 0.707 | 0.384 |
| SiamMDM | Satellite video | 0.711 | 0.453 |
| SVLPNet | Satellite video | 0.688 | 0.471 |
| SiamTM | Satellite video | 0.746 | 0.487 |
| VISTA | Ours | 0.732 | 0.495 |

![SV248S precision and success curves](assets/sv248s-curves.jpg)

## Generalization to OOTB

VISTA achieves the highest PR and SR among the evaluated trackers on OOTB. Its NPR is close to MemTrack, which obtains the highest normalized precision. The curves report precision, normalized precision, and success from left to right.

| Tracker | Type | PR | NPR | SR |
|:---|:---|---:|---:|---:|
| SiamCAR | Generic video | 0.824 | 0.779 | 0.607 |
| ARTrackV2 | Generic video | 0.823 | 0.782 | 0.598 |
| CFME | Satellite video | 0.753 | 0.714 | 0.610 |
| DF | Satellite video | 0.758 | 0.747 | 0.623 |
| STAR | Satellite video | 0.846 | 0.826 | 0.678 |
| MemTrack | Satellite video | 0.887 | 0.848 | 0.694 |
| VISTA | Ours | 0.897 | 0.847 | 0.701 |

![OOTB precision, normalized precision, and success curves](assets/ootb-curves.jpg)
