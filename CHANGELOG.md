# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/)
and this project adheres to [Semantic Versioning](http://semver.org/).

## [Unreleased]

### Added

### Changed

### Fixed

## [15.4.0] - 2026-10-19

### Added

- Added support for MS SQL 2025.
- Added support for PostgreSQL 19.

### Changed

- Updated library dependencies. To use [Windows authentication](https://pgcodekeeper.readthedocs.io/en/latest/windowsauth.html#id2) you need to update [DDL](https://github.com/microsoft/mssql-jdbc/releases/tag/v13.6.1).

### Fixed

- Fixed an error when reading partitions from a PostgreSQL dump.

### Removed

- Removed support for PostgreSQL versions below 15.

### Security

- Increased version of lz4-java library due to CVE-2026-106453 and CVE-2026-106452.

## [15.3.0] - 2026-08-10

### Added

- Added generation of a migration script taking into account the PostgreSQL version when the `Use current database version syntax to generate migration script` setting is enabled.

### Security

- Increased versions of org.apache.httpcomponents libraries due to CVE-2026-64607, CVE-2026-54399, CVE-2026-54428.

## [15.2.0] - 2026-08-10

### Fixed

- Fixed false differences when comparing library objects with the "ignore privileges" option enabled.

## [15.1.0] - 2026-07-30

### Added

- Added support for changing table and column compression settings via `ALTER TABLE` commands instead of recreating objects when the Greenplum 7 syntax is enabled.

### Changed

- Disabled dependency analysis for objects that could not be parsed correctly, reducing the number of irrelevant errors displayed to the user.

### Fixed

- Fixed a parsing error for the `ALTER SEQUENCE ... SET LOGGED/UNLOGGED` command for regular sequences in PostgreSQL.
- Fixed an error in the order of PostgreSQL `ALTER TABLE ... OWNER TO` and `ALTER SEQUENCE ... OWNER TO` commands by moving the latter to the end of the migration script.

### Security

- Increased version of lz4-java library due to CVE-2026-59949.

## [15.0.0] - 2026-07-14

### Changed

- Updated library dependencies.

## [14.7.0] - 2026-06-30

### Changed

- Improved parser rules for working with JSON formats in ClikHouse.

### Fixed

- Fixed errors when working with .pgcodekeeperdependencies files.

## [14.6.0] - 2026-06-18

### Changed

- Improved work with temporary files.

### Fixed

- Fixed full project update to clean only the project's own directories.
- Fixed adding library objects to a project during export.
- Fixed code generation for index when altering in CONCURRENTLY mode.
- Fixed migration script generation when changing a generated column in PostgreSQL.

### Security

- Increased version of logback due to CVE-2026-1225.

## [14.5.0] - 2026-06-02

### Added

- Added support for new syntax for tables for Greenplum 7.
- Added `--structure-file` parameter for parse mode, which allows specifying the path to a properties file with directory layout overrides for project export.

### Changed

- Fixed parser errors for PostgreSQL.

### Security

- Increased version of JDBC driver for PostgreSQL due to CVE-2026-42198.

## [14.4.1] - 2026-05-06

### Fixed

- Fixed a bug when working with Arenadata DB 7.4.0 and higher.

## [14.4.0] - 2026-05-05

### Changed

- Improved code generation when changing an index on partitioned tables PostgreSQL.
- Improved the error message text when connecting to the database.

## [14.3.0] - 2026-04-15

### Added

- Added `--additional-dependencies` parameter, which allows you to specify the path to a file with additional dependencies.
- Added `--simplify-not-null` parameter to simplify reading of NOT NULL constraints via JDBC for PostgreSQL 18+.

## [14.2.0] - 2026-04-07

### Added

- Added localization of missing lines.
- Added `--use-actual-syntax` parameter. When specified, the syntax relevant to the current database version is used (there are currently no syntax changes, but these will be added later). By default, the syntax specific to the minimum supported version is used.

### Changed

- Reduced the number of line breaks and indents added when formatting code.

## [14.1.1] - 2026-03-25

### Changed

- Disabled loading of the OVERRIDES directory for libraries to restore the behavior typical before version 14.0.0.

### Fixed

- Fixed incorrect error on parallel database load failure.

## [14.1.0] - 2026-03-18

### Added

- Added the `--parallel-load` parameter. When specified, databases are loaded in parallel; by default, loading is performed sequentially.
- Added the `--disable-auto-load` parameter. When specified, automatic loading of auxiliary project files is disabled (.pgcodekeeperignore, .pgcodekeeperignoreschema, .dependencies).

### Changed

- Updated the JUnit library version from 5.x to version 6.
- The .dependencies file is now automatically read when loading a project.

### Fixed

- Fixed a bug when parsing the connection string for MS SQL.
- Fixed a migration script generation error with the Print DROP before CREATE option.
- Fixed a bug in the generation of the migration script when data migration when recreating tables with serial-type fields for PostgreSQL.
- Fixed a bug with searching for dependencies for the LATERAL function in PostgreSQL.
- Fixed a bug with automatic object code formatting.

## [14.0.0] - 2026-02-25

### Added

- Added comments processing for NOT NULL constraints in PostgreSQL.
- Added argument `--cluster-name` for adding in migration script ON CLUSTER syntax to ClickHouse (experimentally).
- Added search for .pgcodekeeperignore and .pgcodekeeperignoreschema files during project read. This avoids using the `--ignore-list (-I)` and `--ignore-schema` options with project files.

### Changed

- Improved readability of `--help` help: options are sorted alphabetically.
- Improved parser rules for ClickHouse.
- Improved function analyze in PostgreSQL.

### Fixed

- Fixed default name generation for CONSTRAINT and SEQUENCE objects in PostgreSQL.
- Fixed logic for normalizing views for ClickHouse.
- Fixed parser errors for partitioned tables in MS SQL.
- Fixed a false difference for the STATISTICS object in MS SQL.
- Fixed reading of column length and precision for binary, datetime2, datetimeoffset, and time types in MS SQL database.
- Fixed creating tables with NOT NULL constraints in PostgreSQL.

### Removed

- Removed `--mode verify` and `--mode insert` modes.

### Security

- Updated the version of the clickhouse-jdbc driver due to CVE-2025-66566 and CVE-2025-12183. All connections to ClickHouse must now include the required `password` parameter.

## [13.1.0] - 2025-11-18

### Changed

- Updated library dependencies. To use [Windows authentication](https://pgcodekeeper.readthedocs.io/en/latest/windowsauth.html#id2) you need to update [DDL](https://github.com/microsoft/mssql-jdbc/releases/tag/v13.2.1).

### Fixed

- Fixed an error when reading functions from the ClickHouse database.
- Fixed a false difference between STATISTICS in PostgreSQL.

## [13.0.0] - 2025-11-12

### Changed

- Improved parser rules for ClickHouse.
- Improved migration script generation for tables and indexes with options in MS SQL.
- Added the IS JSON parser rule for PostgreSQL.

### Fixed

- Fixed CTE formatting in ClickHouse.
- Fixed an error comparing tables when the column order is ignored setting is enabled.
- Fixed bug in generating the migration script when adding a column to Log family tables in ClickHouse.
- Fixed a false difference between NOT NULL constraints with the default name in PostgreSQL.
- Fixed adding ONLY for columns in partitioned tables in PostgreSQL.
- Fixed reading of EXTERNAL TABLES in Greenplum 7.

## [12.0.0] - 2025-10-15

### Added

- Added support for PostgreSQL 18.
- Added formatting of the SELECT part of VIEW objects when reading from the database for ClickHouse.

### Changed

### Fixed

- Fixed code generation for columns with Nullable values in ClickHouse.

### Removed

- Removed support for MS SQL versions below 2017.
- Removed support for PostgreSQL versions below 14.
- Removed deprecated `--parse`, `--graph`, `--insert` parameters.

## [11.2.0] - 2025-09-23

### Added

- Added analysis of functions returning the RECORD type.

### Changed

- All localized messages have been brought into a unified style.

### Fixed

- Fixed encoding of text output to console.
- Fixed reading logic when xml file is missing.
- Fixed a race condition when loading a library from an archive.
- Fixed parser rule for floating point constants for MS SQL.

## [11.0.0] - 2025-08-28

### Changed

- The CLI version has been separated from a [main repository](https://github.com/pgcodekeeper/pgcodekeeper).

### Fixed

- Fixed parser rule for PostgreSQL.
- Fixed code generation error when changing views in MS SQL
- Fixed bug with ignoring column order in PostgreSQL and MS SQL constraints.
- Fixed a bug with the settings when saving objects to a project.
- Fixed false differences when ignoring table column order.

[Unreleased]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v15.4.0...HEAD
[15.4.0]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v15.3.0...v15.4.0
[15.3.0]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v15.2.0...v15.3.0
[15.2.0]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v15.1.0...v15.2.0
[15.1.0]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v15.0.0...v15.1.0
[15.0.0]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v14.7.0...v15.0.0
[14.7.0]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v14.6.0...v14.7.0
[14.6.0]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v14.5.0...v14.6.0
[14.5.0]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v14.4.1...v14.5.0
[14.4.1]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v14.4.0...v14.4.1
[14.4.0]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v14.3.0...v14.4.0
[14.3.0]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v14.2.0...v14.3.0
[14.2.0]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v14.1.1...v14.2.0
[14.1.1]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v14.1.0...v14.1.1
[14.1.0]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v14.0.0...v14.1.0
[14.0.0]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v13.1.0...v14.0.0
[13.1.0]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v13.0.0...v13.1.0
[13.0.0]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v12.0.0...v13.0.0
[12.0.0]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v11.2.0...v12.0.0
[11.2.0]: https://github.com/pgcodekeeper/pgcodekeeper-cli/compare/v11.0.0...v11.2.0
[11.0.0]: https://github.com/pgcodekeeper/pgcodekeeper-cli/releases/tag/v11.0.0
