<div align="center">

# AI Photo IQ

**A native macOS app that turns any photo library into a structured, searchable catalog — powered by AI vision.**

![platform](https://img.shields.io/badge/platform-macOS%2026%2B-lightgrey)
![language](https://img.shields.io/badge/Swift-6-orange)
![ui](https://img.shields.io/badge/UI-SwiftUI-blue)
![ai](https://img.shields.io/badge/AI-Claude%20Vision-purple)
![status](https://img.shields.io/badge/status-beta-yellow)

</div>

---

## What it does

Point AI Photo IQ at your Apple Photos library (or a folder in S3), define the fields you care about — say, *Invoice Number*, *Carrier*, *Shipping Address*, *Weight* — and let Claude Vision read every image and fill in the blanks. Review the proposed values in a spreadsheet-style catalog, correct anything it got wrong, then export the whole catalog as a PDF report or CSV.

Originally built to solve a very specific shipping-photo problem, AI Photo IQ generalized into a **user-defined metadata extraction tool**: if you can describe a field in a sentence, the app can extract it from an image.

## Highlights

- **Bring your own schema.** Add, rename, reorder, or delete the metadata fields you want — the AI prompt adapts dynamically.
- **Apple Photos read-only by design.** A dedicated policy layer, unit tests, and a shell audit script guarantee the app never mutates your photo library.
- **Two tiers of intelligence.** Free tier runs on-device via Apple Intelligence and SwiftData. Pro tier unlocks Claude vision, AWS S3 storage, and a MongoDB Atlas catalog.
- **Review before you commit.** Every AI-proposed value is editable in a catalog view before it's written to the database.
- **Export-first workflow.** One click produces a print-ready PDF (thumbnails + metadata) or a clean CSV.
- **Tab-based UX.** Instructions → Setup → Import → Browse → Process → Export → Cleanup. Deliberately linear.

## Stack

| Layer            | Tech                                                     |
| ---------------- | -------------------------------------------------------- |
| App              | Swift 6, SwiftUI, `@Observable` + `@MainActor` app model |
| Local storage    | SwiftData, Keychain for secrets                          |
| Cloud storage    | AWS S3 (photos), MongoDB Atlas (catalog)                 |
| AI               | Anthropic Claude (Vision), Apple Intelligence on-device  |
| Testing          | Swift Testing (`@Suite` / `@Test`)                       |
| Platform         | macOS 26 (Tahoe) and later                               |

## Status

**Beta, approaching v1.** The V1 schema-pivot is complete, freemium tiering (Phase 1 & 2) is merged, and the App Store submission PRD is drafted. Core workflows have unit coverage; no force-unwraps in production paths.

## Why the source is private

This repo is a public-facing description of a working product. The implementation (AWS credentials handling, prompt engineering, catalog schema, freemium gating) lives in a private repository. If you're a collaborator, recruiter, or fellow builder who'd like a deeper look — reach out below.

## Coming soon to this repo

- [ ] Hero screenshot of the catalog view
- [ ] Short demo GIF of the import → AI-extract → review flow
- [ ] Architecture diagram (SwiftData vs. cloud tier)
- [ ] Link to launch post / write-up

## Contact

**Mark Porter** — [@marklovestech](https://github.com/marklovestech) · <mark@bonnieandmark.com>
