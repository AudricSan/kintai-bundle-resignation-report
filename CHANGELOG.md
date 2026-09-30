# Changelog

Tous les changements notables de ce bundle sont documentés dans ce fichier.

Le format suit [Keep a Changelog](https://keepachangelog.com/fr/1.0.0/).
Le schéma de version (X.Y.Z, canaux alpha/beta/main) est décrit dans
`.github/workflows/release.yml`.

## [Unreleased]

### Changed

- Compatibilité avec la Content-Security-Policy stricte de Kintai (`script-src 'self' 'nonce-…'`, sans `'unsafe-inline'`) : les 7 attributs d'événements inline des vues (`onclick=`/`onchange=`/`onsubmit=`/`oninput=`) sont remplacés par des attributs `data-*` (`data-on-click`, `data-submit-on-change`, `data-confirm`… gérés par `csp-actions.js` du Core) et le `<script>` inline porte désormais le nonce de la requête (`csp_nonce()`, gardé par `function_exists` pour ne pas planter sur un Core plus ancien). Sans ce changement, les boutons, sélecteurs et confirmations de ces vues ne font plus rien sous la nouvelle politique, sans aucune erreur visible. **Nécessite Kintai Core 0.3.0 ou plus** (`kintai_core.min`), version qui introduit `csp-actions.js` et la CSP à nonce. `tests.yml` échoue désormais si un handler inline, un lien `javascript:` ou un `<script>` sans nonce réapparaît dans `Views/` ou `src/`.

### Changed

- Aucun changement fonctionnel — bump de version pour aligner ce bundle sur la ligne 1.1.0 commune à tous les bundles officiels.
- Le CSS du PDF (`pdf-resignation-report.css`) et le JS de la modale de suppression (`resignation-report-delete-modal.js`) vivaient dans Kintai Core. Ils vivent maintenant dans `public/css/pdf-resignation-report.css`/`public/js/resignation-report-delete-modal.js`, fournis par ce bundle via `Bundle::loadAssetsFrom()`/`bundle_asset()`/`bundle_asset_path()` — corrige au passage le même bug latent de `dirname()` que `daily-report`. `pdf-export-table.css` (export PDF global, partagé avec `staff/users-export-pdf.php` du Core) reste inchangé, non migré. **Nécessite** `kintai_core.min: "0.2.0"`.

## [1.0.0] - 2026-09-19

### Added

- Extraction initiale depuis Kintai (`src/Bundles/ResignationReport`).
