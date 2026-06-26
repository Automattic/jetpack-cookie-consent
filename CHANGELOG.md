# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.2.0-alpha] - unreleased

This is an alpha version! The changes listed here are not final.

### Added
- Add AGENTS.md with guidance for AI coding agents working in this package.
- Add the cookie-consent frontend Interactivity module (banner, modal, CCPA opt-out, consent logger, Tracks).
- Add the cookie-consent PHP backend: banner/CCPA controls, Interactivity module enqueue, and consent log REST controller.
- GDPR: Honor Global Privacy Control (GPC) as an opt-out signal, denying non-essential cookies (configurable via `gdpr_honors_gpc`).
- Initial version: scaffold the cookie-consent package.

### Changed
- Improve Jetpack Boost page-cache hit rates by excluding Cookie Consent geolocation cookies from the cache key and ensuring geolocation lookups aren’t cached.
- Set up mirror repository and autotagger for package publishing.
- Update package dependencies.

### Fixed
- CCPA: Make the auto-created "Your Privacy Choices" page removable. It is now created only once, is no longer locked from deletion, and the footer links for both the privacy-choices and Privacy Policy pages are hidden if their page is deleted.
- Set host-only cookies instead of deriving a cross-subdomain domain, which browsers reject on multi-level TLDs such as .co.uk and .com.br.

## 0.1.0-alpha - unreleased

- Initial version.

[0.2.0-alpha]: https://github.com/Automattic/jetpack-cookie-consent/compare/0.1.0-alpha...0.2.0-alpha
