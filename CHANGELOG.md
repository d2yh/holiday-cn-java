# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.0] - 2025-07-17

### Added
- Initial release of holiday-cn-java
- `HolidayFetcher` class for fetching and caching Chinese holiday data
- `HolidayInfo` data model compatible with holiday-cn format
- Support for periodic automatic updates
- Local file-based caching with configurable expiration
- Support for multiple remote sources
- Comprehensive unit tests
- Maven build configuration
- Documentation in English and Chinese
- MIT License with proper attribution to holiday-cn

### Features
- Fetch holiday data from remote URLs
- Cache data locally with configurable duration
- Parse JSON data in holiday-cn format
- Query holidays by date or year
- Scheduled periodic updates
- Proper logging with Logback

---

## Versioning

### Version Format
- MAJOR: Breaking changes
- MINOR: New features, backward compatible
- PATCH: Bug fixes

### Compatibility
- Minimum Java version: 1.8
- Maven version: 3.6+

## Attribution

This project data format and inspiration come from [holiday-cn](https://github.com/NateScarlet/holiday-cn).
