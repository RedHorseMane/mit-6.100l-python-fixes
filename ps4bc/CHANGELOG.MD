# Changelog
All notable changes to this project will be documented in this file.  
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/)
and the project adheres to [Semantic Versioning](https://semver.org).

## [Unreleased]
<!-- Add new entries here as you make further fixes -->

## [1.0.0] - 2025-07-25
### Fixed
- Replaced the deprecated `unittest.makeSuite()` call with  
  `unittest.TestLoader().loadTestsFromTestCase()` to keep the test harness
  working on Python ≥ 3.11 and Python 3.13+.  