# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.0] - 2026-07-17

### Added
- `HolidayConfig` — `.properties` configuration system with defaults and user override
- `OffDayStrategy` interface with two implementations:
  - `WeekendOnlyStrategy` (Strategy A): weekends as off-days
  - `FestivalStrategy` (Strategy B): weekends + Spring Festival + National Day with weekend deferral
- `LunarCalendar` — lookup-table-based lunar calendar utility (2000-2050)
- `HolidayFetcher.addWorkDays(LocalDate, int)` — calculate date after N working days
- `HolidayFetcher.isWorkDay(LocalDate)` — check if a date is a working day
- `HolidayFetcher.hasDataForYear(int)` — check if data exists for a year
- `HolidayInfo.isWeekendDay(LocalDate)` — static weekend check utility
- Multi-level data loading: data directory → classpath → remote URL
- Per-year JSON files in data directory with `holiday-meta.json` metadata
- Full English and Chinese README documentation
- 53 unit tests covering all features

### Changed
- `HolidayFetcher` refactored to use `HolidayConfig` for all settings
- Default cache duration changed from 24h to 10 days (14400 minutes)
- `getHoliday()` and `getHolidaysByYear()` now fall back to strategy when no data exists
- Data directory replaces single cache file approach
- `pom.xml` version bumped to `1.0.0`

### Compatibility
- Minimum Java version: 1.8
