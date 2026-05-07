# Video & Ads

Create video ads (VEO3 storyboard process), YouTube video outlines, reverse-engineer successful videos, and build the perfect B2B ad template. Combines AI scripting with practical video production workflows.

## 4-Step Video Ad Process (VEO3)

### Step 1: The Idea
The one step hardest to outsource to AI. Start with a concept that already resonated (e.g., a high-engagement post). AI can brainstorm but rarely produces truly creative ideas.

### Step 2: The Storyboard
Brief your model to create a scene-by-scene storyboard. Each scene ≤8 seconds (VEO3 clip limit).

Output per scene: visual description + dialogue/audio.

### Step 3: Storyboard + Reference Images (Most Critical)
**Key tip:** Prompt from ingredients to video (image → video), NOT text → video.

- Create reference images for each scene using image generation
- Use a master character image for consistency (feed to Nano Banana for scene variations)
- Organize in Figma: each scene gets visual description, dialogue, and reference images
- Reference images serve dual purpose: consistency across image generation AND VEO3 input

### Step 4: Create Videos
For each scene, create a VEO3 prompt referencing the scene's images (max 3):

```
Create an 8-second {{SCENE_DESCRIPTION}} for a {{STYLE}} video.

Use the provided reference images to maintain identity and styling:
1) the main character's face, hairstyle, and clothing
2) {{PROP/SET ELEMENT}}
3) {{ENVIRONMENT}}

{{DETAILED VISUAL DIRECTION}}

{{AUDIO DIRECTION: music, dialogue, sound effects}}

Maintain character and prop consistency throughout.
```

Select "ingredients to video" in VEO3 to include reference images. Expect iteration. Stitch clips in iMovie or similar.

**Gotchas:**
- Models struggle with two speaking characters in same scene — may need workarounds
- Character can't say brand names (copyright triggers) — use visual workarounds
- Character consistency requires reference images per scene

## Tone-Shifting Ad Script (52-second, 7 clips)

```
You are an elite ad creative strategist.
Product: {{PRODUCT}} | ICP: {{ICP}}

Step 1: Determine the single most compelling core claim for this ICP.
Base on ICP's pains, desires, product's unique advantages. Bold + memorable.

Step 2: Create a 52-second ad (7 clips × 8 seconds for Veo3).
Tone shifts: Clips 1-2: Paranoid | Clips 3-4: Pragmatic | Clips 5-7: Playful + CTA
Each clip visually memorable + self-contained.

Output:
Core Claim: {{claim}}
Reasoning: {{2 sentences}}
Clip 1-7: [Tone]: {{8-second script}}
```

## Perfect B2B Ad Template (Reverse-Engineered)

Built from meta-analysis of top B2B YouTube ads:

```
(0:00-0:05) SECTION 1: THE PATTERN INTERRUPT HOOK
"Stop. If you're still managing {{PROCESS}} inside {{COMMON_TOOL}}, you are
wasting {{NUMBER}} hours a week."
Psychology: Loss Aversion

(0:05-0:15) SECTION 2: THE AGITATION (THE VILLAIN)
Walk through the pain. Blame the tool, not the user.
"It's not your fault; it's your stack. {{COMPETITOR}} wasn't built for {{YEAR}}."
Psychology: Empathy & Externalization

(0:15-0:25) SECTION 3: THE PIVOT (THE SKEPTIC)
"I know. You've tried five different tools. They were all 'game changers,' right?
And yet... you're still watching this ad."
Psychology: The "Yes Ladder"

(0:25-0:45) SECTION 4: THE "MAGIC TRICK" DEMO
High-res UI, bright colors, large cursor, smooth movement, sound effects.
"Instead of {{OLD_PROCESS}}, you just {{ACTION}}. Boom."
Psychology: Cognitive Ease

(0:45-0:55) SECTION 5: SOCIAL PROOF BRIDGE
Logos scrolling. "{{NUMBER}} teams like {{COMPANY_A}} and {{COMPANY_B}} switched
and saved {{METRIC}}."
Psychology: Bandwagon Effect

(0:55-1:00) SECTION 6: THE DIRECT CTA
"Stop working in the past. Click the link, start your free trial."
Psychology: Command Tonality
```

## Reverse-Engineer YouTube Videos

```
Act as a World-Class YouTube Strategist (Paddy Galloway / MrBeast style).

PART 1: THE REPLICABLE BLUEPRINT
Break video into Script Skeleton. For each section:
1. Time/Section Name
2. What Happens (one sentence)
3. Engagement Psychology (how it drives views/retention — loops, stakes, validation)

PART 2: THE ENGAGEMENT ENGINE
List Core Elements used, assign Weight by frequency.
Format: [Element Name]: [Description] → [Impact on metric]

PART 3: THE AUDIT
1. Grade (1-5 based on YouTube meta-standards)
2. The Fix: 3-5 improvements for more views (pacing, hooks, engagement loops,
   title/thumbnail alignment)

Video: {{PASTE VIDEO}}
```

## YouTube Video Outline (World-Class)

```
Act as Research Analyst, Narrative Strategist, and Creative Video Scriptwriter.

Topic: {{TOPIC}}
Target Audience: {{AUDIENCE}}
Desired Length: {{LENGTH}}

Phase 1: Foundational Research
- Investigate beyond surface level (primary sources, expert opinions, case studies)
- Identify core narrative (central tension, mystery, or breakthrough)
- Define key takeaway
- Pinpoint engaging elements (surprising stats, analogies, ethical dilemmas)

Phase 2: Video Outline
1. 🎯 Hook (0:00-0:25) — shocking stat, provocative question, micro-story
2. 🎯 Intro: Premise & Promise (0:25-0:50) — core topic + viewer benefit
3. 🎯 Context (0:50-1:45) — connect to current events, define concepts
4. 🎯 Core Insights (1:45+) — 2-4 digestible segments with stories/data
5. 🎯 Impact & Implications — how findings affect viewers
6. 🎯 Nuance & Critical Perspective — limitations, alternate views
7. 🎯 Call to Action — specific engagement question + subscribe CTA
8. 🎯 End Screen — recommend related content

Phase 3: Discoverability
- 3-5 title options (keyword, intrigue, benefit-driven)
- Description key points for SEO
- 10-15 keywords/tags
- Sound design/music cues per section
```

## B2B Ad Template Generator (5-Phase Meta-Analysis)

```
Act as World-Class B2B Creative Strategist.

Phase 1: Identify 10 high-performing B2B YouTube ads (Monday.com, ClickUp,
Grammarly, HubSpot, Slack, etc.)

Phase 2: For each — summarize concept, extract success elements, identify pain point

Phase 3: Compare all 10, find common DNA, assign weight by frequency

Phase 4: Stack-ranked list of core elements
Format: [Rank] - [Element] - [Frequency /10] - [Why it works in B2B]

Phase 5: Fill-in-the-blanks script template based on top elements.
Include stage directions (visuals) + script lines (audio).
Label each section with psychological principle.
```

## Tools
- **VEO3** — 8-second video clips from image + text prompts
- **Flow** — Stitch multiple VEO3 clips together
- **Nano Banana PRO** — Character-consistent image generation
- **ChatGPT** — Storyboard creation, VEO3 prompt crafting
- **Figma** — Organize storyboard + reference images
- **iMovie** — Basic video editing
- **GenSpark** — Turn ad concepts into visual presentations
- **Gemini 3** — YouTube video analysis at scale
