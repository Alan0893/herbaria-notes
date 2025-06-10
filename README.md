## Repository Overview
**se-symbiota** is the main working repository containing a merged codebase from version `3.0.9` that was upgraded to 3.2.4. The system includes five key features that have all been consolidated into the main branch. 

## Repository Structure

### Main Repositories
- **se-symbiota** : primary working repository
- **se-symbiota-private** : contains private/sensitive components (versions `3.0.0`, `3.0.9`, `3.2.4-local-dev`, `3.2.4-int`)
- **se-symbiota-reference-only** : legacy codebase from version 3.0.9 for comparison and troubleshooting

## Branch/Environment Structure
- `3.2.4-local-dev` : local development environment (`se-symbiota-private`)
- `3.2.4-int` : shared/integration environment (`se-symbiota-private`)
- `s2023` : reference branch (`se-symbiota-reference-only`)

## Features
1. **Quick-entry** : rapid data entry functionality
2. **Batch** : batch processign capabilities
3. **Batch Ingestion** : converts folders of images into batches
4. **AI Transcription** : configurable AI model integration for automated transcription
5. **Containerization** : Docker/container deployment support

## Current Status & Issues

### Problems Identified
- Code originally written for version `3.0.9` but merged with `3.2.4`
- Requires testing to ensure compatibility after version merge
- Features haven't been tested together as an integrated system

### Workflow?
- Test all features in the main `se-symbiota` repository
- When bugs are found, fix them across all feature repositories
- Implement fixes in individual feature branches
- Test fixes within each feature branch before merging

## Core Directories

### Root Level
- `index.php` - main entry point/homepage for the portal
- `sitemap.php` - site navigation map

### Configuration (`config`)
- Core PHP classes that handle key functionality like:
  - `ImageProcessor.php` - image processing
  - `DwcArchiverCore.php` - Darwin Core Archive handling
  - `OccurenceDownload.php` - specimen record downloads
  - `SpecProcessorManager.php` - specimen data processing

### Collections Module (`collections`)
- Main module for specimen/collection management:
  - `admin` - administrative tools
  - `editor/` - collection data editing interfaces
  - `individual/` - individual specimen record display
  - `map/` - mapping functionality
  - `misc` - miscellaneous collection tools
  - `specprocessor/` - specimen data processing tools

### Web Interface Components
- `css` - stylesheets including Symbiota-specific styles
- `js` - JavaScript files
- `includes` - common PHP includes like:
  - `header.php` - page header template
  - `footer.php` - page footer template
  - `head.php` - HTML head content
  - etc.

### Content (`content`)
- `logs/` - application logs
- `dwca/` - Darwin Core Archive files
- `imglib/` - image library
- `lang/` - language translation files

### Other Directories
- `docs` - documentation files including installation guides
- `temp` - temporary file storage
- `api` - API related files
- `projects` - project management functionality
- `vendor` - third-party dependencies
