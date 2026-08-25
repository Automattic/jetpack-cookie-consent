# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.2.0-alpha] - unreleased

This is an alpha version! The changes listed here are not final.

### Security
- Secure the public consent-log write endpoint with per-IP rate limiting, URL/consent-type validation, and spoof-resistant IP detection.

### Added
- Add a config-driven core: init( $config ) with per-feature feature toggles and a declarative Config_Schema. Keep the jetpack_cookie_consent_config and jetpack_cookie_consent_log_retention_days filters as override points for code that does not own the init() call.
- Add AGENTS.md with guidance for AI coding agents working in this package.
- Add classic-theme fallback for required privacy/CCPA/manage-preferences links.
- Add the cookie-consent frontend Interactivity module (banner, modal, CCPA opt-out, consent logger, Tracks).
- Add the cookie-consent PHP backend: banner/CCPA controls, Interactivity module enqueue, and consent log REST controller.
- Document the public cookie consent lifecycle event and WP Consent API script-gating guidance.
- GDPR: Honor Global Privacy Control (GPC) as an opt-out signal, denying non-essential cookies (configurable via `gdpr_honors_gpc`).
- Geo: Add configurable provider and region settings.
- Honor features.geo=false: show the banner to all visitors without a geolocation lookup.
- Initial version: scaffold the cookie-consent package.
- Lifecycle: Add consumer-callable cleanup APIs for deactivation and uninstall.
- Register WP personal-data exporter and eraser for the consent log; rename the consent-log customer_id column to user_id.

### Changed
- Add a configurable consent category registry.
- Consent log: Add configurable IP address handling modes.
- Consent log: Record policy and banner versions.
- Docs: Restructure README to define the public API surface, an explicit internal (non-API) list, and a versioning/back-compat policy.
- Improve Jetpack Boost page-cache hit rates by excluding Cookie Consent geolocation cookies from the cache key and ensuring geolocation lookups aren’t cached.
- Make banner and CCPA copy configurable.
- Set up mirror repository and autotagger for package publishing.
- Update package dependencies.

### Removed
- Minimum supported PHP version is now 7.4.

### Fixed
- Banner: Hide policy links in the preferences modal when their URL is not configured, so the Cookie Policy and Privacy Policy links never render an empty link.
- CCPA: Make the auto-created "Your Privacy Choices" page removable. It is now created only once, is no longer locked from deletion, and the footer links for both the privacy-choices and Privacy Policy pages are hidden if their page is deleted.
- Consent banner: Gate Tracks loading on analytics consent.
- Consent log: send a REST nonce for logged-in visitors so the consent row records the real user ID instead of 0.
- Consent log: unhook the personal-data exporter/eraser filters on deactivation.
- Keep the classic-theme footer-links control hidden until needed so it no longer overlaps the consent banner.
- Make the consent banner, modal, and controls render consistently across classic and block themes, and expose their colors, spacing, and stacking order as CSS custom properties so the appearance can be customized via Additional CSS.
- Set host-only cookies instead of deriving a cross-subdomain domain, which browsers reject on multi-level TLDs such as .co.uk and .com.br.

## 0.1.0-alpha - unreleased

- Initial version.

[0.2.0-alpha]: https://github.com/Automattic/jetpack-cookie-consent/compare/0.1.0-alpha...0.2.0-alpha
