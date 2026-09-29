# Changelog

Tous les changements notables de ce bundle sont documentés dans ce fichier.

Le format suit [Keep a Changelog](https://keepachangelog.com/fr/1.0.0/).
Le schéma de version (X.Y.Z, canaux alpha/beta/main) est décrit dans
`.github/workflows/release.yml`.

## [Unreleased]

### Changed

- Aucun changement fonctionnel — bump de version pour aligner ce bundle sur la ligne 1.1.0 commune à tous les bundles officiels.
- Le CSS du PDF (`pdf-resignation-report.css`) et le JS de la modale de suppression (`resignation-report-delete-modal.js`) vivaient dans Kintai Core. Ils vivent maintenant dans `public/css/pdf-resignation-report.css`/`public/js/resignation-report-delete-modal.js`, fournis par ce bundle via `Bundle::loadAssetsFrom()`/`bundle_asset()`/`bundle_asset_path()` — corrige au passage le même bug latent de `dirname()` que `daily-report`. `pdf-export-table.css` (export PDF global, partagé avec `staff/users-export-pdf.php` du Core) reste inchangé, non migré. **Nécessite** `kintai_core.min: "0.2.0"`.

## [1.0.0] - 2026-09-19

### Added

- Extraction initiale depuis Kintai (`src/Bundles/ResignationReport`).
