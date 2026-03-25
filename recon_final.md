# AD ARMY RECON REPORT
<!-- Generated: 2026-03-26 | Source: ad.army | Pipeline: Unnamed Pipeline -->

## WORKSPACE

- Name: Displate
- Credit indicator: "98" (was 100; top-right of global top bar, inside a green circle button, tabular-nums font)

## TOP BAR (left → right, exact labels)

[Ad Army logo] → D avatar → "Displate" (workspace name + chevron) → ⚙ (workspace settings) → home icon → inbox icon → ✦ (featured/starred) → feed/activity icon → [tab: "Unnamed Project"] → [tab: "Unnamed Pipeline" ×] → + (new tab) → "98" credit indicator (green circle) → ? help → M (user avatar)

## SIDEBAR (exact labels)

Left sidebar (when on dashboard):
- "All Operations" (heading + badge count "2")
- "All operatives" (filter dropdown)
- "Recent" (filter)
- CLASS section:
  - "Pipelines"
    - "Studio"
      - "New Pipeline"
        - "New Studio"
          - "New sector"

          ## PIPELINE CANVAS

          Canvas sub-header: `< Pipelines | Unnamed Pipeline | draft | ● Automation | ⚙ | Reset test | [4 errors — fix to publish]`
          Context source bar: `+ Add context source | Brand assets, guidelines, or references shared with every step`
          Bottom hint bar (yellow): `Engage steps are independent. Connect them to chain outputs.`

          Nodes visible (left → right):
          - ENTRY — Start (special trigger entry card)
          - 1 — Generate (text)
          - 2 — Generate 2 (video)
          - 3 — Combine (action)
          - 4 — Combine (concatenate)
          - 5 — Source 2 (external_action)

          ## NODE TYPES

          ### Trigger (ENTRY / Start)

          - Panel tabs: none (opens as right-side panel from "Configure trigger" button)
          - Panel title: "Trigger Automation"
          - Panel description: "Connect one live event source and keep each delivery observable. Choose an app, connect its trigger, and test one sample event before turning it on."
          - Status fields: "Automation Status: Not configured", "Trigger: Not connected yet", "Last delivery: Never", "Last run outcome: No runs yet"
          - Buttons: "Enable automation", "Save draft"
          - Labels: "Choose App", "Choose Trigger", "Trigger Settings", "Test Trigger"
          - App picker: searchable list (0CodeKit, 15Five, 1CRM, 2Captcha, 2Chat, 2markdown, 302.AI, 360NRS, 46elks, 4Dem OAuth, 8x8 Connect, Ablefy, ...)
          - Special behaviour: Entry node is always present; "Automation ready" / "Configure trigger" mode; "Run Manually" button separate from trigger setup

          ### Source (Input)

          - Panel tabs: "Input" | "Lineage lane"
          - Panel title: "Source 2 — Input"
          - Panel description: "Define the resources this step provides to the rest of the pipeline."
          - Sub-types observed: external_action (Pipedream-backed)
          - Field structure: key name (e.g. "external_action"), display label ("External Action"), @ reference format: `@prep_source2.external_action`
          - "Add description" button for each output field
          - App picker: same large app catalogue as Trigger (Pipedream-based)
          - @ reference format: `@prep_source2.<fieldKey>`

          ### Generate

          - Panel tabs: "Generate" | "Lineage lane"
          - Panel description: "Compose the prompt, connect sources, and tune the model output."
          - Output types (toggle buttons): Text | Image | Video
          - Fields:
            - Data sources (expand/collapse with count badge "0/1 connected" / "Connect all")
              - Prompt (contenteditable ProseMirror field, placeholder: "Type @ to insert a linked source. Press Enter for a line break.")
                - PROMPT section: "Choose prompt" dropdown
                  - Processing mode: "Independent" | "Split" (Split = "Each input is processed separately into its own output")
                    - Model selector button (shows current model name)
                      - Parallelism selector: x1 | x2 | x3 | x4
                        - ▶Advanced section (collapsible)
                        - Advanced params (non-Google models, e.g. xAI Grok):
                          - Temperature (slider, default 1)
                          - Advanced params (Google models, e.g. Gemini):
                            - Temperature (slider, default 1)
                              - Google Search grounding (checkbox)
                              - Retest/Test Step button

                              ### Generate — Video variant (output type: Video)

                              - Model shown: "Veo 3.1" (Google)
                              - Extra field: Aspect ratio selector: 1:1 | 16:9 | 9:16 | 4:3 | 3:4
                              - Parallelism: x1 | x2 | x3 | x4

                              ### Merge / Concatenate (Combine - concatenate sub-type)

                              - Panel tabs: "Concatenate" | "Lineage lane"
                              - Panel description: "Assemble lineage text from earlier steps into one output."
                              - Fields:
                                - Label
                                  - "Steps to combine" — pick 2 or more steps (checkbox list: Trigger (input), Generate (generate), Generate 2 (generate), Combine (action))
                                    - Note: "Select at least 2 steps to combine."
                                    - Buttons: "Run Merge" (disabled until 2+ steps selected)
                                    - Behaviour: Merge requires min 2 source steps; only 1 connected source detected by default

                                    ### Action (Combine - action sub-type)

                                    - Panel tabs: "Action" | "Lineage lane"
                                    - Panel description: "Choose an app action and map upstream data into its fields."
                                    - Fields/Labels:
                                      - App Connection (shows connected app e.g. "slack_v2")
                                        - Action selector (shows action name e.g. "Send Message to Channel")
                                          - Connect account button
                                            - "Fill fields" (field mapper with @step.field references)
                                              - @step and @step.field reference hints
                                                - Label
                                                  - Run behavior: "Manual review" | "Auto advance"
                                                    - Card response: Text | Image | Video
                                                    - Buttons: "Test action", "Execute action step"
                                                    - Flow: app → action → connect account → fill fields → test action

                                                    ## @ LINKING

                                                    - Syntax format: `@<prep|step>_<stepName>.<fieldKey>` (e.g. `@prep_trigger`, `@prep_source2.external_action`)
                                                    - Trigger step appears as: "Trigger" → `@prep_trigger`
                                                    - Dropdown triggered by typing `@` in ProseMirror prompt fields
                                                    - Dropdown format per item: display name on top, `@reference_path` in monospace below
                                                    - Which nodes appear as options: Trigger output (confirmed); likely all upstream connected steps
                                                    - Which fields support @: Prompt field (Generate), Fill fields (Action), likely any reference-enabled text field
                                                    - The note "2 inputs available. Type @ to reference them." appears when sources are connected

                                                    ## CONTEXT SOURCE TYPES (exact labels + descriptions)

                                                    Popup title: "Add context source — Shared with every engage step"

                                                    | Label | Description |
                                                    |-------|-------------|
                                                    | Text | Brand voice, guidelines, copy |
                                                    | Image | Logos, assets, references |
                                                    | File | PDFs, docs, spreadsheets |
                                                    | Feed | RSS or data feed |
                                                    | App | Shopify, Slack, Notion... |

                                                    ## PIPELINE SETTINGS (Base Settings / Workspace Settings)

                                                    Opened via: ⚙ gear icon in global top bar OR pipeline sub-header gear icon (both lead to workspace/base settings)

                                                    Tab names: General | Squad | Recruitment | Env Vars

                                                    - General tab fields:
                                                      - Base Insignia (image upload, max 2MB, recommended 256×256px)
                                                        - Base Name (text input, current value: "Displate")
                                                          - Plan & Billing (shows: "free Plan — 1 active operative - Unlimited capacity" + "Upgrade" button)
                                                            - "Secure Changes" button

                                                            - Squad tab fields:
                                                              - Member list (shows "(you)" with email: mateusz.waligorski@displate.com)

                                                              - Recruitment tab fields:
                                                                - Email address (input, placeholder: "Email address")
                                                                  - Role selector (dropdown: Editor / Viewer / Admin, default: editor)
                                                                    - "Recruit" button
                                                                      - Pending invitations list (empty: "No pending recruitment orders")

                                                                      - Env Vars tab fields:
                                                                        - Section label: "Workspace Sandbox Env Vars"
                                                                          - Note: "Values are write-only after save. Pipeline vars override workspace vars with the same key at runtime."
                                                                            - KEY input (placeholder: "API_KEY")
                                                                              - VALUE input (placeholder: "Secret value", type: password)
                                                                                - "Save Secret" button
                                                                                  - Existing vars list (empty: "No base env vars configured.")

                                                                                  ## MODELS (grouped by provider)

                                                                                  ### Google
                                                                                  - Gemini 3.1 Pro Preview
                                                                                  - Gemini 3 Pro Preview
                                                                                  - Gemini 3 Flash Preview

                                                                                  ### OpenAI
                                                                                  - GPT-5.4
                                                                                  - GPT-5.2
                                                                                  - GPT-5.2 Pro
                                                                                  - GPT-5.2 Codex
                                                                                  - GPT-5 Mini
                                                                                  - GPT-4.1
                                                                                  - GPT-4.1 Mini
                                                                                  - GPT-4.1 Nano
                                                                                  - GPT-4o
                                                                                  - GPT-4o Mini
                                                                                  - o3-mini
                                                                                  - o1
                                                                                  - o1-mini
                                                                                  - o1-pro
                                                                                  - GPT-4 Turbo

                                                                                  ### Anthropic
                                                                                  - Claude Opus 4.6
                                                                                  - Claude Sonnet 4.6
                                                                                  - Claude Opus 4.5
                                                                                  - Claude Sonnet 4.5

                                                                                  ### xAI
                                                                                  - Grok 4.20
                                                                                  - Grok 4.20 Reasoning
                                                                                  - Grok 4.1 Fast
                                                                                  - Grok 4.1 Fast Reasoning
                                                                                  - Grok 3
                                                                                  - Grok 3 Fast
                                                                                  - Grok 3 Mini
                                                                                  - Grok 3 Mini Fast
                                                                                  - Grok 2
                                                                                  - Grok 2 Vision

                                                                                  ### ByteDance
                                                                                  - Seed 1.8
                                                                                  - Seed 1.6
                                                                                  - Seed 1.6 Flash

                                                                                  ### Video (Generate node, Video output type)
                                                                                  - Veo 3.1 (Google) — aspect ratios: 1:1, 16:9, 9:16, 4:3, 3:4

                                                                                  ## STATE SIGNALS

                                                                                  - Canvas loaded: green dot + "● Automation" badge in pipeline sub-header; hint bar at bottom "Engage steps are independent. Connect them to chain outputs."
                                                                                  - Node configured: green/teal pulse animation (class `pipeline-ready-pulse-active`) on Test button; "Retest" label when previously tested
                                                                                  - Node with errors: red badge "!1" or "!2" on top-right of node card; "Review" badge below node name
                                                                                  - Pipeline publish-ready: blocked by "4 errors — fix to publish" banner (red); publish button shows "errors — fix to publish" in top-right
                                                                                  - Error state: red banner at top of canvas listing each error with step name and description
                                                                                  - Draft status: "draft" orange badge next to pipeline name in sub-header
                                                                                  - Credit counter: starts at 100, decrements with AI test runs (each test call costs 1–2 credits)

                                                                                  ## SURPRISES

                                                                                  1. **Credit system visible**: "100" (then "98") credit counter in top bar inside a green circle — each Generate test costs credits; likely tied to AI model calls
                                                                                  2. **Workspace settings = pipeline settings**: Both the global ⚙ and the pipeline sub-header ⚙ open the same "Base Settings" modal — no separate pipeline-level config found
                                                                                  3. **"Lineage lane" tab** appears on Generate, Source, Action, Concatenate panels — separate view for pipeline lineage/data-flow visualization
                                                                                  4. **@ reference format uses "prep" prefix**: `@prep_trigger`, `@prep_source2.external_action` — not `@step_name` as might be expected
                                                                                  5. **xAI Grok Advanced = Temperature only**; Google Advanced = Temperature + "Google Search grounding" checkbox
                                                                                  6. **ByteDance/Seed models** included alongside OpenAI/Google/Anthropic/xAI
                                                                                  7. **Pipeline is called a "Pipeline" but workspace calls operations "Operations"** and items "Operatives"
                                                                                  8. **Combine node is used for both Merge (concatenate) AND Action** — same node label, different sub-types
                                                                                  9. **"Squad" tab** instead of "Team" — military naming convention throughout (Operatives, Recruitment, Squad, Base)
                                                                                  10. **Pipelines run against "Automation" mode** (live trigger) OR "Run Manually" — they're separate flows

                                                                                  ## GAPS

                                                                                  1. Video model dropdown didn't fully open — only confirmed "Veo 3.1"; additional video models unknown
                                                                                  2. Image output type models not verified (likely same text model list or different image-specific models)
                                                                                  3. Pipeline-level env vars (vs workspace env vars) — mentioned in note "Pipeline vars override workspace vars" but no UI to set pipeline-level vars found
                                                                                  4. "Lineage lane" tab content not deeply explored — appears to show data flow visualization
                                                                                  5. Full app catalogue size not counted (100s of apps via Pipedream integration)
                                                                                  6. Studio product not explored (separate from Pipelines)
                                                                                  7. Feed context source type details unknown (RSS/data feed config)
                                                                                  8. "Squad1" tab name in settings — the "1" suffix unclear (count badge? version?)
                                                                                  9. Trigger test flow not completed (would require connecting an actual app)
                                                                                  10. Whether "New sector" in sidebar creates a new organizational grouping — not tested
                                                                                  
