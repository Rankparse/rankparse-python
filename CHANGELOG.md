# Changelog

## 0.2.0 - 2026-11-23

- Added: `site_platform(domain)` (sync and async clients) for `GET /v1/site-platform`. It reads the home page once, live, and returns the single platform the site runs on (WordPress, Wix, Shopify, Squarespace, Webflow and so on), any `other_platforms`, and commerce `add_ons` such as WooCommerce. 1 credit, half the price of `tech_stack()`. A page that matches no platform returns `platform: None` and is charged; an unreadable site raises a 503 error and is not charged.

## 0.1.1

- Fixed: `tech_stack(domain)` now sends `?domain=` (was `?url=`), matching the live API.
- Fixed: `batch(domains)` now sends `{"domains": [...]}` and returns the standard response envelope. Previous versions sent `{"requests": [...]}` and expected a `{"results": [...], "total_credits_used": ...}` shape that the live API never returned — `batch()` was non-functional in 0.1.0.
