# Pagecraft (pgc)

## Overview
The Pagecraft spell transforms web pages into well-formatted markdown documents using AI-powered content analysis and formatting. It's perfect for content curation, documentation, and research.

## Features
- AI-powered content extraction
- Multi-stage processing
- Intelligent formatting
- Quality validation
- Configurable output location

## Requirements
- OpenAI API key (set as `OPENAI_API_KEY` environment variable)
- Python packages: `click`, `beautifulsoup4`, `openai`, `requests`

## Installation
```bash
cast ponder pagecraft
```

## Usage
```bash
cast pgc <url>
```

## Process Stages
1. **Content Fetching**: Retrieves content from the provided URL
2. **Initial Draft**: Creates first markdown conversion
3. **Review**: AI reviews the conversion quality
4. **Improvement**: Enhances content based on review
5. **Final Review**: Provides quality score and final assessment

## Configuration
Set `SCRAPE_ARCHIVE_PATH` environment variable to specify a default save location:
```bash
export SCRAPE_ARCHIVE_PATH="/path/to/archive"
```

## Examples

### Basic Usage
```bash
cast pgc https://example.com/article
```

### With Custom Save Location
```bash
export SCRAPE_ARCHIVE_PATH="~/Documents/web_archives"
cast pgc https://example.com/technical-doc
```

## Output Structure
The generated markdown includes:
- Title
- Content sections
- Code blocks (if present)
- Lists and tables (if present)
- Images (referenced, not downloaded)

## Quality Metrics
The spell provides:
1. Initial review feedback
2. Improvement suggestions
3. Final quality score (1-10)
4. Formatting validation
5. Content completeness check

## Best Practices
- Ensure the URL is accessible
- Set `SCRAPE_ARCHIVE_PATH` for organized storage
- Review the final output for accuracy
- Check the quality score for validation
- Keep original URL for reference

## Common Use Cases
1. Documentation archival
2. Content research
3. Technical documentation
4. Blog post curation
5. Knowledge base creation

## Notes
- Requires internet connection
- Some websites may block content extraction
- Quality depends on source content structure
- AI processing may take a few moments
- Results are saved locally