# Images

Screenshots and diagrams referenced by repo docs. Organized by section.

## Layout

```
images/
├── journey/         (screenshots for Journey/ pages)
└── resources/       (screenshots for Resources/ pages)
```

## Expected Files

These filenames are already referenced (or pre-referenced) in the docs. Drop the actual PNG into the listed path and the markdown will render correctly.

### Journey

- `journey/step1-personalizations-settings.png` - Microsoft 365 Copilot Personalizations settings screen, showing the **Save memory** toggle and the **Custom Instructions** field. Used in [Journey Step 1](../Journey/01-personalize-copilot.md).
- `journey/step1-frontier-enrollment.png` - Microsoft Admin Center, Copilot > Settings > Frontier enrollment screen. Used in [Journey Step 1](../Journey/01-personalize-copilot.md).
- `journey/step3-skill-loaded-slash.png` - Cowork chat input showing the `/` slash-command suggestion list with a custom skill visible. Used in [Journey Step 3](../Journey/03-build-custom-skills.md).

### Resources

(Empty for now. Add screenshots that support reference docs as needed.)

## Rules When Adding Images

**Format:**
- PNG for UI screenshots (sharp text)
- JPG for photos
- SVG for diagrams

**Size:**
- Keep each file under ~500 KB. Compress with [tinypng.com](https://tinypng.com) or [squoosh.app](https://squoosh.app) before committing.
- If a screenshot is very wide, constrain its display width in markdown using HTML: `<img src="../images/journey/example.png" width="700">`.

**Naming:**
- Descriptive kebab-case
- Prefixed by section if helpful: `step1-...`, `step3-...`, `resources-...`

**PII scrub before commit:**
- Email addresses (top-right user chip, To: fields, sender names)
- Manager and direct report names (org view, calendar invites)
- Tenant name and company domain
- Real document names in file lists
- Notification badges with sender names

Use Greenshot, ShareX, the built-in Snipping Tool, or Preview to redact before saving.

**Alt text:**
- Always include alt text in the markdown image syntax. Describes what the image shows for screen readers and people whose images failed to load.

## Adding a New Image

1. Capture the screenshot. Crop tight to the relevant UI element.
2. Redact any PII.
3. Compress to under 500 KB.
4. Save into the right subfolder with a descriptive name.
5. Update the relevant doc to replace the placeholder block with:
   ```markdown
   ![Descriptive alt text](../images/<section>/<file>.png)
   ```
6. Add an entry to this README under "Expected Files" if it is a new filename.
7. Commit. One image per commit is easier to review.
