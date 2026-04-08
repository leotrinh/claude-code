# Workflow: Create Professional Slides with Claude + NotebookLM + Canva

> Generate beautiful, on-brand slide decks entirely with AI — no design skills required.

---

## Tools Overview

| Tool | Role |
|---|---|
| **Claude** | Analyze reference images → generate a detailed design prompt |
| **NotebookLM** | Research content + generate slides (Slides feature) |
| **Canva Pro** | Edit text and images using the Magic Layer feature |

---

## 4-Step Workflow

### Step 1 — Gather Ideas & Brand Assets

- Search **Pinterest** by brand name, product category, or slide topic
- Save slides whose style matches your brand or vision
- Collect: logo, color palette, fonts, layout references

> 💡 More reference images = AI understands your desired style more accurately

---

### Step 2 — Generate a Design Prompt with Claude

1. Upload your reference slide images to Claude (multiple images supported)
2. Ask Claude to generate a design prompt, for example:

```
Help me create an AI prompt so that from this prompt,
AI will generate slides that look exactly like these references in terms of:
color palette, layout, decorative style, font, font size...
to present about [your topic].

Requirements:
- Illustrations should be artistic / abstract in style
- Images must be sourced externally, not AI-generated from scratch
- Write the prompt in English
- Generate 15 slides
```

3. Review Claude's output → edit as needed:
   - Change the title
   - Adjust number of slides
   - Add or remove content sections

> 💡 **Why Claude over ChatGPT?**  
> Claude produces more precise, detailed prompts → noticeably better slide output

---

### Step 3 — Generate Slides with NotebookLM

#### 3a. Prepare your content

Go to [NotebookLM](https://notebooklm.google.com) → Create a new notebook → Add sources:

- Upload PDF, Word, or PowerPoint files
- Paste website or YouTube links
- Connect Google Drive documents
- Use the **Deep Research** feature to automatically gather content by topic

#### 3b. Generate slides — 2 methods

**Method 1: Generate directly in the chat**

```
Help me create a 15-slide deck about [topic],
covering [point 1], [point 2], [point 3],
following this design style: [paste your Claude design prompt here]
```

After AI returns the content outline → follow up with: **"Now generate the designed slides"**  
→ NotebookLM automatically triggers the Slides feature to render.

**Method 2: Use the SlideX button (recommended)**

1. Click the **SlideX** button in the left sidebar
2. Select mode: **Detail Deck**
3. Select length: **Default**
4. Paste the design prompt from Claude into the prompt field
5. Click **Generate** → wait 10–15 minutes

> ✅ Method 2 consistently produces better-looking results than Method 1

#### 3c. Export the file

NotebookLM supports two export formats:

| Format | Pros | Cons |
|---|---|---|
| **PDF** | Preserves design perfectly | Cannot edit content |
| **PowerPoint (.pptx)** | Great for presenting | Text/images still not directly editable |

→ Solution to this limitation: **use Canva in Step 4**

---

### Step 4 — Edit with Canva (Magic Layer)

#### Why this step is needed

PDF/PPT files from NotebookLM are not directly editable.  
Canva Pro's **Magic Layer** feature uses AI to automatically separate each element (text, images, color blocks) into individual layers for free editing.

#### Step-by-step

1. Open the PPT in Canva → select all pages → **Download as PNG**
2. Go back to Canva → **Upload** all the PNG images
3. Open each image → click **Edit** → select **Magic Layer**
4. Wait ~30 seconds for AI to separate the layers
5. You can now:
   - Edit / delete / replace text
   - Swap out images
   - Adjust colors and sizes of individual elements

> ⚠️ **Note:** Magic Layer may remove some shadow/3D effects → fix manually by adding borders or rounded corners as needed

---

## Requirements & Notes

- **Canva Pro** is required for the Magic Layer feature
- NotebookLM and Claude both have usable free tiers
- Vietnamese text renders without font errors in NotebookLM
- If AI generates incorrect product images → replace them manually in Canva

---

## Quick Summary

```
Pinterest (find reference slides)
    ↓
Claude (analyze references → generate design prompt)
    ↓
NotebookLM (research content + generate slides via SlideX)
    ↓
Export PNG → Upload to Canva Pro
    ↓
Magic Layer → edit freely
    ↓
✅ Finished slide deck
```
