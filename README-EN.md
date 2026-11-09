[简体中文](README.md) | **English** | [日本語](README-JP.md)

# Anime Screenshot to Genga · Reverse Anime Genga

An AI Agent Skill for reverse-engineering finished anime frames into Japanese animation key-drawing (genga) sheets with production-style information.

This skill generates genga-style images, which remain substantially different from authentic key drawings used in animation production. In actual genga, character construction, cel grouping, color-trace lines, and annotations serve specific animation and production needs that cannot be fully recovered from a single finished frame. Off-frame extensions, material groupings, and annotations in the output involve inference and may contain errors. The results are better suited to recreational uses such as visual simulation; they should not be treated as accurate reconstructions of original production materials or as substitutes for key drawings usable in subsequent production.

## What it can do

It focuses on **what information a key drawing should retain and what should be omitted.** While preserving the shot composition and character designs, it determines cel grouping, background simplification, off-frame extensions, shadow and highlight boundaries, and functional handwritten annotations.

- Convert anime screenshots into white-background genga-style illustrations with a camera frame.
- Correct excessive cel splitting, overly detailed backgrounds, missing off-frame information, and missing color-trace lines.
- Add inferred production annotations such as key-drawing numbers, 止め (hold), 口パク (lip sync), and クミ (compositing/overlap handling), and check whether they serve a meaningful purpose.
- Distinguish information visible in the finished frame from plausible production inferences.

This is a set of instructions and reference materials for an AI agent, not a standalone image-conversion program, model weights, or a training dataset. Actual drawing requires an environment with image-generation or editing capabilities.

## Core principles

| Aspect | Approach |
| --- | --- |
| Composition | Preserve character scale, placement, expressions, hand poses, and occlusion relationships inside the camera frame |
| Omission | Retain only background guides needed for positioning, contact, and occlusion; omit decorative and material details |
| Cel grouping | Decide according to independent timing, movement, reuse, and compositing needs, rather than splitting elements mechanically |
| Off-frame extensions | Complete necessary nearby cropped structures such as the crown of the head, elbows, cuffs, and tail tips; enlarge the sheet if needed without changing the camera frame |
| Color-trace lines | Use red, blue, and other boundary lines to convey actual lighting and color-separation information; do not add colored lines randomly |
| Annotations | Place notes near their subjects to identify materials, compositing relationships, and necessary production instructions |
| Handwriting | Use single-pass, quick strokes with naturally varied size and spacing, avoiding a uniform, rigid appearance |
| Overlapping lines | Overlay annotations directly on the drawing without white outlines or erased strips that interrupt underlying lines |
| Presentation | Use a flat white background without paper texture, peg holes, subtitles, or platform watermarks |

Circled numbers for each material group may be plausibly invented, such as A① and B③. They are not authentic production numbers recovered from the screenshot and do not indicate which group appears earlier or later.

## Copyright notice

When using this skill with frames from commercial animation, the input material and any protected content retained in the output may implicate third-party copyright. Converting a finished frame into line art or a genga-style drawing does not automatically remove the original work’s copyright restrictions. Attribution, non-commercial use, or a “for educational purposes only” statement does not by itself establish permission or a legal exception. Before uploading material to a third-party AI service or publicly displaying, distributing, selling, or otherwise using the output, ensure that you have the necessary authorization or that your use falls within an applicable copyright exception. This project grants no rights to third-party works. When sharing outputs, identify the work and source appropriately and clearly label the results as AI-generated reverse-engineered illustrations, so they are not mistaken for official genga or authentic production materials.

## How to use

### Environments supporting Agent Skills

1. Download or clone this repository.
2. Submit the `reverse-anime-genga/` folder to your agent’s skill installer, or place it in the skills directory according to that environment’s installation procedure. Keep `SKILL.md`, `references/`, `agents/`, and `assets/` intact.
3. Upload an anime screenshot and invoke `reverse-anime-genga`. Invocation syntax and installation paths depend on your environment.

Example request:

> Use reverse-anime-genga to reconstruct this screenshot as a genga-style drawing. Preserve the composition, choose sensible cel groupings, and complete structures that are only slightly cropped by the camera frame.

Targeted revisions:

> Preserve the composition and color-trace lines, and change only the annotations: write each stroke once, with more casual spacing, size, and slant. Overlay the notes on the existing lines without erasing the surrounding drawing.

> Only the elbow of the right arm is missing. Extend the sheet to the right and complete the bent elbow, keeping the shoulder and hand positions inside the frame unchanged.

### Environments without automatic installation

Ask the agent to read [SKILL.md](reverse-anime-genga/SKILL.md) and allow it to access the referenced files, then provide the screenshot and task. A text-only environment can help plan the reconstruction and check annotation logic, but this does not mean an image has been generated.

## Files

- [SKILL.md](reverse-anime-genga/SKILL.md): the main workflow, decision criteria, default output requirements, and ten-point checklist.
- [production-knowledge.md](reverse-anime-genga/references/production-knowledge.md): production knowledge summaries, original source links, and limits of applicability.
- [generation-guide.md](reverse-anime-genga/references/generation-guide.md): guidance for structuring generation prompts and templates for targeted revisions.
- `agents/openai.yaml`: the name, description, and default invocation prompt for compatible environments.
- `assets/icon.svg`: the skill icon.

## References and design sources

This skill was developed through repeated screenshot-reconstruction experiments, feedback on specific issues, and publicly available animation-production resources. References include P.A.WORKS animation instruction, REVOROOT’s digital animation manuals, tutorials from 日本アニメーション (Nippon Animation) and CELSYS, WEBアニメスタイル’s compositing lectures, annotated genga examples, and animator-training materials.

For full links and the purpose of each source, see [Production knowledge and sources](reverse-anime-genga/references/production-knowledge.md). This repository includes summaries and source references, not copies of third-party tutorial texts or example images.

Different studios and shots use different material groupings, line colors, and workflows. This skill adopts a white background, single-pass handwritten notes, and selective off-frame completion as default presentation conventions; these preferences are not presented as universal animation-production standards.

## Limitations

- A single finished frame cannot uniquely determine the original genga, cel grouping, timing, camera movement, or off-frame structure. Outputs are inferred reconstructions guided by production logic.
- Image models may still generate incorrect fingers, contours, Japanese text, or numbers. Inspect outputs and make targeted corrections as needed.
- A/B material labels in an image do not mean the output contains genuinely editable, separate layers.
- This version has undergone text-based scenario checks. This does not guarantee results across all image models and shots.

## Feedback

Please report specific issues through the repository’s Issues. Describe the input scene, expected behavior, and actual discrepancy. For image-related issues, include the actual input and output where possible and identify the problem area.

## License status

This repository does not currently specify an open-source license. Making this repository public does not change the rights associated with third-party tutorials, works, or related images.
