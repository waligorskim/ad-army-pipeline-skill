# Ad Army Pipeline — Claude Skill

> Recon sweep of [ad.army](https://ad.army) Pipeline canvas. Covers all node types, models, fields, triggers, and settings. Use this as a skill reference when helping users build or debug Ad Army pipelines.

---

## DASHBOARD

- **Workspace name:** Displate
- **Sidebar items:** All Operations | Recent | CLASS: Pipelines | Studio | New Pipeline | New sector
- **Top bar (left→right):** Ad Army logo | [D] Displate workspace switcher | Open workspace settings (gear) | Home | Assets | Prompts | Feeds | [tab: project] | [tab: pipeline] | New pipeline (+) | 100 (credit counter) | Field Report (?) | Profile (avatar)
- **Dashboard buttons:** New Pipeline | New Studio | Grid/List toggle | All operatives filter | Scan search | Recent sort | Destroy (per card)

---

## PIPELINE CANVAS

### Top bar (left→right)
Back to Pipelines | pipeline name (editable) | `draft` badge | `Automation` badge | Pipeline settings (gear) | error badge | **Publish** button

### Canvas hints
- Context source bar: "Brand assets, guidelines, or references shared with every step"
- Advisor: "Looking good. Hit Publish to lock in v1 and begin deploying."
- Advisor: "Engage steps are independent. Connect them to chain outputs."
- Node result area: "Results appear after testing"
- Action node: "Action results appear here"
- Merge node: "Merged content appears here"

### Add Context Source options
| Label | Description |
|---|---|
| Text | Brand voice, guidelines, copy |
| Image | Logos, assets, references |
| File | PDFs, docs, spreadsheets |
| Feed | RSS or data feed |
| App | Shopify, Slack, Notion... |

### Pipeline Settings tabs

**GENERAL:** Name* | Description | Icon (emoji) | Tags | Cancel/Save

**AUTOMATION:**
- Status: Automation Status | Trigger | Last delivery | Last run outcome | Enable automation toggle | Save draft
- Source Setup: Choose App (Pipedream catalogue) | Choose Trigger | Trigger Settings
- Test Trigger: Run sample event | Sample payload preview (JSON)
- Recent Deliveries
- Prerequisites: Pipeline must be Published; Action steps set to Auto advance

**ENV VARS:**
- "Pipeline Sandbox Env Vars" — write-only after save, override workspace vars at runtime
- Key (placeholder: API_KEY) | Value (password) | Save Secret

---

## NODE TYPES

### START (Entry — fixed, not addable)

- Fixed leftmost node, always present
- Badge: ENTRY (green dot) | Title: "Start"
- "Live events enter here. Configure the source here, then launch manually below when you want to test."
- "Automation ready" / "Keep the trigger setup here. Manual launch stays separate."
- Buttons: Configure trigger | Run Manually (disabled pre-publish)
- Icon: wireless/broadcast icon

---

### GENERATE

**Dropdown:** Generate — "AI fires from your briefing"
**Panel sub-label:** Lineage lane
**Description:** "Compose the prompt, connect sources, and tune the model output."
**Auto-saves:** "Changes save automatically."

#### Output type selector: Text | Image | Video (buttons)

#### Common fields (all output types)

| Field | Type | Notes |
|---|---|---|
| Tab: [step name] | button | editable label |
| Tab: Data sources | button | shows N/M connected |
| Inputs available | button | "N inputs available. Type to reference them." |
| Prompt editor | ProseMirror contenteditable | @ triggers reference dropdown |
| Choose prompt | button | opens prompt library |
| Model selector | dropdown | see Models section |
| Quantity (x1) | dropdown | x1/x2/x3/x4/custom 1-10 — "Versions per input" |
| Test Step | button | "Enter a prompt to test this step" |

#### Text-only fields

| Field | Type | Notes |
|---|---|---|
| Run mode | buttons | Independent \| Split ("Each input is processed separately into its own output") |
| Advanced: Temperature | range slider | default 1 |
| Advanced: Google Search grounding | checkbox | |

#### Image-only fields

| Field | Type | Notes |
|---|---|---|
| Size quick picker | button | "auto" label |
| Multi-Format Output | checkbox | on by default |
| Advanced: Aspect Ratio | combobox | auto, 1:1, 16:9, 9:16, 4:3, 3:4, 3:2, 2:3, 21:9, 5:4, 4:5 |
| Advanced: Resolution | combobox | Default, 1K, 2K, 4K |
| Advanced: Format | combobox | Default, png |
| Advanced: Thinking Level | combobox | Minimal, High |

#### Video-only fields

| Field | Type | Notes |
|---|---|---|
| Aspect ratio quick picker | button | 1:1 / 16:9 / 9:16 / 4:3 / 3:4 |
| Multi-Format Output | checkbox | on by default |
| Advanced: Duration (seconds) | combobox | 4s / 6s (default) / 8s |
| Advanced: Generate with audio | checkbox | |

#### Data sources tab
- "From upstream steps" — toggle per available step (shows: incoming_event from Trigger; prior step names)
- "Add source step" button

#### Validation
- Error: "Generate step must have a non-empty prompt"
- Error: "Pipeline has 2 lineage start steps: [names]. Only one lineage step can start without another upstream."
- Warning: "This step has inputs available but doesn't reference them — output won't use upstream data"

---

### ACTION

**Dropdown:** Action — "Connect to an external app"
**Default step label:** Combine
**Panel sub-label:** Action / Lineage lane
**Description:** "Choose an app action and map upstream data into its fields."

| Field | Type | Notes |
|---|---|---|
| Search for an app… | text | full Pipedream catalogue (1000s of apps) |
| Advanced: Label | text | editable, default "Combine" |
| Advanced: Run behavior | combobox | Manual review (default) \| Auto advance |
| Advanced: Card response | combobox | Text (default) \| Image \| Video |
| Advanced: Field path | text | placeholder: "Leave empty to render the whole JSON response" |

Inline reference hint: "Type inline references directly in any text field above."
Examples: `@step`, `@step.field`

- **Run when ready** button | **Waiting on:** upstream step badge
- Card: "Action results appear here"

**Validation:**
- "Action step must have non-empty sourceKey, appSlug, and componentKey"
- "Connected source step is not referenced in the prompt"

---

### MERGE (Concatenate)

**Dropdown:** Merge — "Combine outputs from multiple steps"
**Default step label:** Combine (internal type: **Concatenate**)
**Panel sub-label:** Concatenate / Lineage lane
**Description:** "Assemble lineage text from earlier steps into one output."

| Field | Type | Notes |
|---|---|---|
| Label | text | editable, default "Combine" |
| Steps to combine | checklist | checkbox \| step name \| (type tag) for each prior step |

- "Pick 2 or more steps to combine into one output."
- **Run Merge** button (grayed until ≥2 selected)
- Card: "Merged content appears here"

**Validation:** "Concatenate step needs at least 2 source steps"

> Note: Internally called "Concatenate" in sub-label and canvas card badge.

---

### SOURCE

**Dropdown:** Source — "Variable intel — changes each deployment"
**Default step label:** Source N
**Panel sub-label:** Input / Lineage lane
**Description:** "Define the resources this step provides to the rest of the pipeline."

**Mode toggle:** User Provided | AI Generate

**User Provided sub-types:**

| Sub-type | Notes |
|---|---|
| File | file upload |
| Image | image upload |
| Text | text input |
| Feed Item | RSS/feed item |
| Connect App | app integration |
| Code Sandbox | in-browser code execution as input |

**AI Generate sub-types:** Text | Image | "+ Add description" | "Change type"

**Batch input:** "Use batch input" toggle — "Create one lane per uploaded image and reference it with a dedicated batch token."

- Canvas card: "empty" badge until configured; "Configure sources…" button
- **Validation:** "Input step must have at least one resource"

---

## @ LINKING

Trigger: type `@` in the Generate node prompt editor or inline in any Action text field.

| Display name | Token |
|---|---|
| Trigger | `@prep_trigger` |
| Generate | `@card_group_generate` |

**Reference formats:**
- `@prep_trigger` — trigger/entry node
- `@card_group_generate` — generate step
- `@step` — generic step reference (action fields)
- `@step.field` — dot-notation field access

**Works in:** Generate prompt editor (dropdown UI) | Action node text fields (inline, no dropdown)

---

## MODELS

### Text

| Provider | Models |
|---|---|
| Google | Gemini 3.1 Pro Preview, Gemini 3 Pro Preview, **Gemini 3 Flash Preview** (default) |
| OpenAI | GPT-5.4, GPT-5.2, GPT-5.2 Pro, GPT-5.2 Codex, GPT-5 Mini, GPT-4.1, GPT-4.1 Mini, GPT-4.1 Nano, GPT-4o, GPT-4o Mini, o3-mini, o1, o1-mini, o1-pro, GPT-4 Turbo |
| Anthropic | Claude Opus 4.6, Claude Sonnet 4.6, Claude Opus 4.5, Claude Sonnet 4.5 |
| xAI | Grok 4.20, Grok 4.20 Reasoning, Grok 4.1 Fast, Grok 4.1 Fast Reasoning, Grok 3, Grok 3 Fast, Grok 3 Mini, Grok 3 Mini Fast, Grok 2, Grok 2 Vision |
| ByteDance | Seed 1.8, Seed 1.6, Seed 1.6 Flash |

### Image

| Provider | Models |
|---|---|
| Google | **Gemini 3.1 Flash Image Preview** (default), Gemini 3 Pro Image |
| OpenAI | GPT Image 1.5 |
| xAI | Grok Imagine, Grok Imagine Pro |
| ByteDance | Seedream 4.5, Seedream 4.0 |
| Recraft | Recraft V4, Recraft V4 Pro, Recraft V4 SVG |

### Video

| Provider | Models |
|---|---|
| Google | **Veo 3.1** (default), Veo 2 |
| OpenAI | Sora 2, Sora 2 Pro |
| xAI | Grok Video |
| Kling | Kling 3.0, Kling 3.0 Pro, Kling O3, Kling O3 Pro, Kling 2.6, Kling 2.6 Pro, Kling 2.5 Pro |
| ByteDance | Seedance 1.5 Pro, Seedance 1.0 Pro, Seedance 1.0 Pro Fast |

---

## TRIGGER CONFIG

Accessible via: Start node → "Configure trigger" button **OR** Pipeline settings → Automation tab.

**Sections:**
1. **Trigger Automation** — status overview + Enable automation toggle
2. **Source Setup** — Choose App (Pipedream catalogue) | Choose Trigger | Trigger Settings
3. **Test Trigger** — Run sample event | Sample payload preview (JSON, default null)
4. **Recent Deliveries** — inbound events, run links, delivery errors

**To enable automation:** Publish pipeline first + all Action steps must be Auto advance (not Manual review).

---

## STATE SIGNALS

| Signal | Indicator |
|---|---|
| Canvas loaded | Step cards render; advisor bar appears at bottom |
| Node configured | Output type badge updates; error count decrements; "Changes save automatically." |
| Publish-ready | Error badge gone; Publish active; Run Manually enabled |
| Error | Red badge: "N validation errors — fix to publish"; per-node "!N" indicator |

**Error messages:**
- `"Generate step must have a non-empty prompt"`
- `"Pipeline has 2 lineage start steps — only one can start without upstream."`
- `"Action step must have non-empty sourceKey, appSlug, and componentKey"`
- `"Concatenate step needs at least 2 source steps"`
- `"Input step must have at least one resource"`
- `"Connected source step is not referenced in the prompt"`

---

## SURPRISES

1. All new steps default to name **"Combine"** (both Action and Merge) — potential naming confusion.
2. Model labels include forward-looking versions (GPT-5.4, Claude 4.6, Grok 4.20).
3. **Recraft** included for vector/SVG image generation.
4. **Kling** has 7 video variants — most expansive video provider.
5. Source → **Code Sandbox** sub-type suggests runnable code as pipeline input.
6. Merge internally called **"Concatenate"** — differs from dropdown label.
7. @ tokens use internal IDs: `prep_trigger`, `card_group_generate` — not human-readable.
8. **"100" credit counter** (green circle, top bar) = generation credits.
9. Image Advanced: **Thinking Level (Minimal/High)** — model reasoning toggle.
10. Video Advanced: explicit **Generate with audio** toggle.
11. Pipeline type badge = **"Automation"** — a distinct pipeline mode.

---

## GAPS

- "Field Report" (?) button — not explored
- Source → Connect App, Code Sandbox, Feed Item detail panels
- Source → Batch input configuration
- Action node app selection detail
- Prompts / Assets / Feeds (top bar) — not in Pipeline scope
- Post-Publish versioning (v1, v2…)
- Non-Google text model Advanced params (system prompt, max tokens, etc.)
- Studio section — out of scope

---

*Recon: 2026-03-25 | Workspace: Displate (waligorskim)*
