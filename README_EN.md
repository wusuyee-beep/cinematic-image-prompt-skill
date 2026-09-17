# Cinematic Image Prompt Skill

A Chinese-first Agent Skill that turns a short visual idea into a clear, controllable image-generation prompt. It prioritizes subject identity, count, spatial relationships, motivated lighting, coherent color, and model-specific failure prevention before decorative style terms.

## What it does

- Converts short ideas, reference images, scripts, and product briefs into executable prompts.
- Separates camera position, shot size, field of view, perspective, focus, and depth of field.
- Keeps attributes bound to the correct subject in multi-subject scenes.
- Designs lighting with a source, direction, quality, and visible purpose.
- Adds only scene-specific negative constraints.
- Runs a 100-point internal review and rewrites outputs that fail hard gates or score below 90.

## Quick use

```text
Use $cinematic-image-prompt to rewrite “a girl waiting at a bus stop on a rainy night” as a cinematic image prompt.
```

The Skill outputs Chinese by default. Ask for English explicitly when needed. It only invokes an image-generation tool when the user explicitly asks to generate, render, or create the image.

## Installation

The repository follows the open `SKILL.md` folder format. See the [multi-agent installation and compatibility guide](docs/agent-installation.md) for Codex, Claude Code, WorkBuddy, CodeBuddy, Qwen Code, Qoder, QoderWork, and generic agents.

Platforms without native Skill support can use the [self-contained Chinese system-prompt adapter](adapters/system-prompt.zh-CN.md).

## Case study

The [SHEPHARD THE SHEPHERD spokesperson case](cases/shepherd-spokesperson.md) connects a user-supplied generated video, representative frames, visual-language analysis, and a reusable still-image prompt.

## Sources

The method draws from professional cinematography and visual-language references, official image-model prompting guidance, and research on detailed descriptions, layout planning, subject omission, and attribute binding. See [`references/sources.md`](references/sources.md).

[中文说明](README.md)
