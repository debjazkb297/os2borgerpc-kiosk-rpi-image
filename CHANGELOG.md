# Changelog

All notable changes to this project will be documented in this file.

## [2.0.2] - 2024-04-25

- [#123](https://github.com/os2display/display-client/pull/123)
  - Ensured real ip is logged in nginx.
- [#124](https://github.com/os2display/display-client/pull/124)
  - Changed to apply max-age 7d to all files and added cache busting to config.json and release.json.
  - Added "loginCheckTimeout", "configFetchInterval", "refreshTokenTimeout", "releaseTimestampIntervalTimeout" to config.json.
  - Simplified config.json.
- [#122](https://github.com/os2display/display-client/pull/122)
  - Added max-age and expires 1 hour to config.json and release.json.
- [#121](https://github.com/os2display/display-client/pull/120)
  - Add releaseVersion, releaseTimestamp and screenId searchParams when starting app.
