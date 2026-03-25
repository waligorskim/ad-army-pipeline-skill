# Ad Army Pipeline — Claude Skill (v2)

> Full recon of [ad.army](https://ad.army) Pipeline canvas. Covers all node types, models, fields, triggers, settings, prompts library, assets, feeds, workspace settings, and the Action node app integration pattern. Use as a skill reference when helping users build or debug Ad Army pipelines.

---

## GLOBAL NAVIGATION

### Top bar (left→right)
Ad Army logo | [D] Workspace switcher (e.g. "Displate") | Open workspace settings (gear) | Home | **Assets** | **Prompts** | **Feeds** | [open tabs: pipelines/projects] | New pipeline (+) | Credit counter (green circle, e.g. "100") | Field Report (?) | Profile avatar

### Sidebar
- All Operations
- Recent
- CLASS: Pipelines | Studio | New Pipeline | New sector

---

## WORKSPACE SETTINGS

Access via gear icon next to workspace name. Tabs:

**GENERAL**
- Base Insignia (image upload, max 2MB, 256×256px recommended)
- Base Name (text field, e.g. "Displate")
- Plan & Billing: shows current plan (e.g. "free Plan — 1 active operative - Unlimited capacity") | Upgrade button

**SQUAD** — lists team members with roles (Owner, Editor, Viewer, Admin)

**RECRUITMENT** — invite by email, assign role (Editor / Viewer / Admin)

**ENV VARS**
- Heading: "Workspace Sandbox Env Vars"
- Note: "Values are write-only after save. Pipeline vars override workspace vars with the same key at runtime."
- Key (placeholder: API_KEY) | Value (password) | Save Secret

---

## ASSETS (top bar)

Page: ad.army/assets  
Heading: "Assets"  
Filters: All | Image | Text | Video  
Search: "Scan assets..."  
Filter by operative dropdown

> Assets are generated outputs saved from pipeline runs. Empty until pipelines produce content.  
> Empty state: "No assets in the depot — Generate content in your operations to populate the depot"

---

## PROMPTS LIBRARY (top bar)

Page: ad.army/prompts  
Heading: "Prompts"  
Button: "New Prompt"  
Search: "Search prompts..."  
Filter by operative | Tabs: All (25) | Text (16) | Image (5) | Video (4) | Favorites (0) | Custom (0)

### Prompt editor fields
- Name (text, placeholder "e.g. Ad Copy Generator")
- Output Type (combobox): Text | Image | Video
- Prompt body (ProseMirror rich text editor with toolbar)
- Toolbar: Bold | Italic | Strikethrough | Inline code | H1/H2/H3 | Bullet list | Numbered list | Task list | Quote | Code block | Add link | **Insert {{prompt}} placeholder**
- Actions: Cancel | Save Changes

### Variable placeholder
All prompts use `{{prompt}}` as the dynamic insertion point. This is replaced with the node's input at runtime.

### Built-in prompts (all by "Ad Army")

**Text prompts (16 total):**
| Name | First line of content |
|---|---|
| Quick Headlines | Create 5 compelling headlines for: {{prompt}} |
| Product Description | Write a compelling product description for: {{prompt}} |
| Social Media Post | Create a social media post about: {{prompt}} |
| Email Subject Lines | Generate 5 email subject lines for: {{prompt}} |
| Expand & Elaborate | Take this concept and expand it into detailed content: {{prompt}} |
| Summarize | Summarize the following content concisely: {{prompt}} |
| Rewrite Tone | Rewrite in a more [professional/casual/friendly/formal] tone: {{prompt}} |
| Image Prompt Engineer | Create a detailed image generation prompt for: {{prompt}} |
| Headline Generator Pro | # HEADLINE GENERATOR — elite direct-response copywriter role |
| Big Idea Generator | # BIG IDEA GENERATOR — senior strategist role |
| Banner Visual Direction | # VISUAL DIRECTION GENERATOR — elite creative director role |
| Tagline Generator | # TAGLINE GENERATOR — tagline specialist role |
| Headline Generator (Baerskin v1.0) | # BAERSKIN HEADLINE GENERATOR v1.0 |
| Big Idea (Baerskin v3.0) | # BAERSKIN BIG IDEAS GENERATOR v3.0 — Prompt 1 of 3: Ideation Engine |
| Banner Visual Direction (Baerskin v1.0) | # BAERSKIN VISUAL DIRECTION GENERATOR v1.0 — Prompt 4 of 4: Visual Spec Engine |
| Tagline (Baerskin v1.0) | # BAERSKIN TAGLINE GENERATOR v1.0 — Prompt 3 of 3: Tagline Engine |

**Image prompts (5):**
| Name | Style |
|---|---|
| Product Lifestyle | Professional product photography, lifestyle setting, magazine-quality |
| 3D Isometric Icon | Cute 3D isometric icon, pastel palette, matte blender render |
| Cinematic Photo | 35mm film, grain, cinematic lighting, dramatic atmosphere |
| Vector Logo | Minimalist vector, flat style, geometric shapes, white background |
| Watercolor Art | Watercolor painting, soft edges, artistic splashes, white paper texture |

**Video prompts (4):**
| Name | Style |
|---|---|
| Social Video | Cinematic, fast-paced, eye-catching, social media optimized |
| Drone Shot | Aerial establishing shot, cinematic lighting, smooth motion |
| Cyberpunk Loop | Neon lights, rain, night, Blade Runner style, volumetric |
| Nature Timelapse | Photorealistic 4K, nature documentary style |

### Headline Generator Pro — key structure
- Role: elite direct-response copywriter
- Rule of One: every headline conveys ONE idea
- Hierarchy: Tier 1 Benefit-Driven | Tier 2 Proclamation | Tier 3 Problem-First | Tier 4 Specificity
- Four U's scoring: Urgent | Useful | Unique | Ultra-Specific
- Hook patterns: Benefits Without Sacrifice | Problem-Agitate | Specificity-Led | Identity/Belonging | Curiosity Gap | Direct Challenge
- Output: 10 headlines, one per line, no labels

---

## INTEL FEEDS (top bar)

Page: ad.army/feeds  
Heading: "Intel Feeds"  
Button: "Import Intel"  
Filter by operative  
Empty state: "No feeds yet — Import First Feed"  
Right pane: "Select a feed to browse records / Or import a feed to begin"

### Import Intel modal (3 steps: Upload → Configure → Import)
**Upload tab:**
- Load Feed File: file upload (XML or JSON; supports Google Merchant Center, JSON feeds)
- Fetch from Source: URL field (placeholder: https://example.com/feed.xml) + Fetch button

---

## FIELD REPORT (? button)

Feedback/bug reporting tool. Tabs:
- **Malfunction** — bug reports
- **Field Report** — general reports
- **Equipment Request** — feature requests

Fields: Report details (textarea) | Transmit button

---

## PIPELINE CANVAS

### Sub-bar (below top bar)
`← Pipelines` | pipeline name (editable, "Click to rename") | `draft` badge | `• Automation` badge | Pipeline settings (gear) | error badge (`N errors — Fix to publish`) | **Publish** button

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
- Status region: Automation Status | Trigger | Last delivery | Last run outcome | Enable automation toggle | Save draft
- Warnings: "Publish the pipeline before enabling automation." | "Headless readiness still needs attention."
- Source Setup: Choose App (Pipedream catalogue) | Choose Trigger | Trigger Settings
- Test Trigger: Run sample event | Sample payload preview (JSON, default null)
- Recent Deliveries section
- Prerequisites: Publish first; all Action steps set to Auto advance (not Manual review)

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
- Wireless/broadcast icon top-right

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
| Tab: Data sources | button | N/M connected count |
| Data sources tab content | toggles per step | "From upstream steps" + "Add source step" |
| Inputs available | button | "N inputs available. Type to reference them." |
| Prompt editor | ProseMirror contenteditable | @ triggers reference dropdown |
| Choose prompt | button | opens Prompts library |
| Model selector | dropdown | see Models section |
| Quantity (x1) | dropdown | x1/x2/x3/x4/custom 1-10 — "Versions per input" |
| Test Step | button | "Enter a prompt to test this step" |

#### Text-only fields

| Field | Type | Notes |
|---|---|---|
| Run mode | buttons | Independent \| Split ("Each input is processed separately into its own output") |
| Advanced: Temperature | range slider | default 1; ALL providers |
| Advanced: Google Search grounding | checkbox | **Google models only** |

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

#### Text model Advanced params by provider
| Provider | Temperature | Google Search |
|---|---|---|
| Google (Gemini) | ✓ | ✓ |
| OpenAI (GPT/o1/o3) | ✓ | — |
| Anthropic (Claude) | ✓ | — |
| xAI (Grok) | ✓ | — |
| ByteDance (Seed) | ✓ | — |

#### Validation
- "Generate step must have a non-empty prompt"
- "Pipeline has N lineage start steps: [names]. Only one lineage step can start without another upstream."
- Warning: "This step has inputs available but doesn't reference them — output won't use upstream data"

---

### ACTION

**Dropdown:** Action — "Connect to an external app"  
**Default step label:** Combine  
**Panel sub-label:** Action / Lineage lane  
**Description:** "Choose an app action and map upstream data into its fields."

#### Action configuration flow
1. **Choose App** — search Pipedream catalogue (1000s of apps)
2. **Choose Action** — per-app list of available actions (e.g. Slack: Send Message to Channel, Upload File, Update Message, etc.)
3. **Connect Account** — "Connect [App]" button (OAuth/credentials) OR "configure without one"
4. **Fill Fields** — per-action required and optional props exposed as labelled inputs; references accepted inline (`@step`, `@step.field`)
5. **Test action** button

#### Slack example fields (Send Message to Channel)
| Field | Type | Required |
|---|---|---|
| Slack account | OAuth connection | Yes (or skip) |
| Channel | combobox/text | Yes |
| Text | text | Yes (usually) |
| Add app to channel automatically? | checkbox | No |
| Optional: Send as mrkdwn | toggle | No |
| Optional: Send as User | toggle | No |
| Optional: Schedule message | toggle | No |
| Optional: Reply to Thread | toggle | No |
| Optional: Customize Bot Settings | toggle | No |
| + more optional props | — | — |

#### Action Advanced section
| Field | Type | Notes |
|---|---|---|
| Label | text | editable, default "Combine" |
| Run behavior | combobox | Manual review (default) \| Auto advance |
| Card response | combobox | Text (default) \| Image \| Video |
| Field path | text | placeholder: "Leave empty to render the whole JSON response"; hint: `@step.field` |

Inline reference hint: "Type inline references directly in any text field above."  
Examples: `@step`, `@step.field`

- **Execute action step** button (becomes "Run when ready" once configured)
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
| Steps to combine | checklist | checkbox \| step name \| (type tag) |

- "Pick 2 or more steps to combine into one output."
- **Run Merge** button (grayed until ≥2 selected)
- Card: "Merged content appears here"

**Validation:** "Concatenate step needs at least 2 source steps"

> Note: Internally "Concatenate" — differs from dropdown label "Merge".

---

### SOURCE

**Dropdown:** Source — "Variable intel — changes each deployment"  
**Default step label:** Source N  
**Panel sub-label:** Input / Lineage lane  
**Description:** "Define the resources this step provides to the rest of the pipeline."

**Mode toggle:** User Provided | AI Generate

#### User Provided sub-types

| Sub-type | Internal slot name | Configure action | Notes |
|---|---|---|---|
| File | — | file upload | drag/drop or file picker |
| Image | — | file upload | drag/drop or file picker |
| Text | — | inline text | plain text input |
| Feed Item | feed_item | "Configure feed" | links to Intel Feeds; reference: `@feed_item` |
| Connect App | external_action | "Connect app" + Pipedream catalogue | same app list as Action node; validation requires provider "pipedream" |
| Code Sandbox | sandbox_code | "Configure code" → full modal | JS or Python, auto dependency manifest |

#### Code Sandbox modal
- Language: JavaScript (Node 24) | Python (3.13)
- Runtime: text field (e.g. "node24")
- Code editor: exports `main()` — must return `{ textContent, rawData }` or both
- Default code: `export async function main() { return { textContent: 'Hello from JavaScript' } }`
- Dependency Manifest: auto-generated package.json; "Regenerate" button; manual edit supported
- Env Access allowlist: checkbox per stored key; manual comma-separated textbox (placeholder: `OPENAI_API_KEY, SLACK_BOT_TOKEN`)
- Test Results section: "Run the current draft without saving"
- Logs section
- Actions: Cancel | Run Test | Save Changes

#### AI Generate sub-types
| Sub-type | Notes |
|---|---|
| Text | generates text value at deploy time |
| Image | generates image value at deploy time |

Common: "+ Add description" button | "Change type" button

**Batch input:** "Use batch input" toggle — "Create one lane per uploaded image and reference it with a dedicated batch token."

- Canvas card: "empty" badge until configured; "Configure sources…" button
- Per-source: "Click to rename" | "Click to copy reference" | "+ Add description" | Destroy
- **Validation:** "Input step must have at least one resource"
- **Validation:** "sandbox code requires valid code configuration"
- **Validation:** "external action requires provider pipedream" + "is missing sourceKey, appSlug, componentKey"

---

## @ LINKING

Trigger: type `@` in Generate prompt editor or inline in any Action text field.

| Display name | Token |
|---|---|
| Trigger | `@prep_trigger` |
| Generate [step] | `@card_group_generate` |

**Formats:**
- `@prep_trigger` — trigger/entry node  
- `@card_group_generate` — generate step  
- `@step` — generic (action fields)  
- `@step.field` — dot-notation field access

**Works in:** Generate prompt editor (dropdown UI) | Action text fields (inline) | Action number/bool/JSON fields (inline, no dropdown)

---

## MODELS

### Text

| Provider | Models | Default |
|---|---|---|
| Google | Gemini 3.1 Pro Preview, Gemini 3 Pro Preview, Gemini 3 Flash Preview | Gemini 3 Flash Preview |
| OpenAI | GPT-5.4, GPT-5.2, GPT-5.2 Pro, GPT-5.2 Codex, GPT-5 Mini, GPT-4.1, GPT-4.1 Mini, GPT-4.1 Nano, GPT-4o, GPT-4o Mini, o3-mini, o1, o1-mini, o1-pro, GPT-4 Turbo | — |
| Anthropic | Claude Opus 4.6, Claude Sonnet 4.6, Claude Opus 4.5, Claude Sonnet 4.5 | — |
| xAI | Grok 4.20, Grok 4.20 Reasoning, Grok 4.1 Fast, Grok 4.1 Fast Reasoning, Grok 3, Grok 3 Fast, Grok 3 Mini, Grok 3 Mini Fast, Grok 2, Grok 2 Vision | — |
| ByteDance | Seed 1.8, Seed 1.6, Seed 1.6 Flash | — |

### Image

| Provider | Models | Default |
|---|---|---|
| Google | Gemini 3.1 Flash Image Preview, Gemini 3 Pro Image | Gemini 3.1 Flash Image Preview |
| OpenAI | GPT Image 1.5 | — |
| xAI | Grok Imagine, Grok Imagine Pro | — |
| ByteDance | Seedream 4.5, Seedream 4.0 | — |
| Recraft | Recraft V4, Recraft V4 Pro, Recraft V4 SVG | — |

### Video

| Provider | Models | Default |
|---|---|---|
| Google | Veo 3.1, Veo 2 | Veo 3.1 |
| OpenAI | Sora 2, Sora 2 Pro | — |
| xAI | Grok Video | — |
| Kling | Kling 3.0, Kling 3.0 Pro, Kling O3, Kling O3 Pro, Kling 2.6, Kling 2.6 Pro, Kling 2.5 Pro | — |
| ByteDance | Seedance 1.5 Pro, Seedance 1.0 Pro, Seedance 1.0 Pro Fast | — |

---

## TRIGGER CONFIG

Same UI via: Start node → "Configure trigger" **OR** Pipeline settings → Automation tab.

**Sections:**
1. Trigger Automation — overview + Enable automation toggle
2. Source Setup — Choose App (Pipedream) | Choose Trigger | Trigger Settings
3. Test Trigger — Run sample event | payload preview
4. Recent Deliveries

**To enable:** Publish first + all Action steps on Auto advance.

---

## STATE SIGNALS

| Signal | Indicator |
|---|---|
| Canvas loaded | Cards render; advisor bar at bottom |
| Node configured | Output type badge updates; error count decrements; "Changes save automatically." |
| Publish-ready | Error badge gone; Publish active; Run Manually enabled |
| Error | Red badge: "N validation errors — fix to publish"; per-node "!N" indicator |

**Error messages:**
- `"Generate step must have a non-empty prompt"`
- `"Pipeline has N lineage start steps — only one can start without upstream."`
- `"Action step must have non-empty sourceKey, appSlug, and componentKey"`
- `"Concatenate step needs at least 2 source steps"`
- `"Input step must have at least one resource"`
- `"Connected source step is not referenced in the prompt"`
- `"sandbox code requires valid code configuration"`
- `"external action requires provider pipedream"`
- `"external action is missing sourceKey, appSlug, componentKey"`

---

## SURPRISES & NOTES

1. All new steps default to name **"Combine"** (both Action and Merge).
2. Model labels include forward-looking versions (GPT-5.4, Claude 4.6, Grok 4.20).
3. **Recraft** for SVG image generation.
4. **Kling** has 7 video variants — most expansive video roster.
5. Source → **Code Sandbox**: full JS/Python sandbox with dependency manifest and env allowlist.
6. Merge internally called **"Concatenate"** — differs from dropdown label.
7. @ tokens: `prep_trigger`, `card_group_generate` — internal IDs, not step names.
8. **Google Search grounding** only available for Google/Gemini text models.
9. Image Advanced: **Thinking Level (Minimal/High)** — model reasoning toggle.
10. Video Advanced: explicit **Generate with audio** + **Duration (4/6/8s)** toggles.
11. Pipeline type badge = **"Automation"**.
12. **Assets depot** is populated only by pipeline run outputs.
13. **Prompts library** uses `{{prompt}}` placeholder — not `@` references.
14. **Feeds** support Google Merchant Center XML and generic JSON feeds.
15. **Connect App** (Source sub-type) = identical to Action app catalogue (Pipedream).
16. Action → "configure without one" lets you lay out fields pre-auth — useful for pipeline design.

---

## REMAINING GAPS

- Post-Publish versioning (v1, v2…) UI not seen
- Feed Item field-mapping config (which feed fields map to which slot) not explored
- Connect App Source — what the run output looks like / how it differs from Action node
- Profile menu contents not explored

---

*Recon v2: 2026-03-25 | Workspace: Displate (waligorskim)*
