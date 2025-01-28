This file defines the context schemas for each source type.

1. **Website Content (Static Pages)**
For sources like roadmap.logos.co, Waku website, Status website, etc.:
- Use a web crawler (e.g., Playwright, Selenium, or Scrapy)
- Implement metadata extraction for source URLs and timestamps
- Structure recommendations:
  ```python
  {
    "content": "...",
    "url": "...",
    "timestamp": "...",
    "project": "waku/status/logos",
    "type": "website_content"
  }
  ```

2. **Documentation (Technical)**
For contributor handbooks, operator documentation:
- Use document parsers specific to format (PDF, Markdown, etc.)
- Maintain heading hierarchy for context
- Structure recommendations:
  ```python
  {
    "content": "...",
    "source_file": "...",
    "section": "...",
    "hierarchy": ["heading1", "heading2", "heading3"],
    "project": "...",
    "type": "documentation"
  }
  ```

3. **Discord Messages**
For Discord channel content:
- Implement Discord API integration
- Bundle related messages as conversations
- Structure recommendations:
  ```python
  {
    "content": "...",
    "channel": "...",
    "timestamp": "...",
    "thread_id": "...",
    "message_type": "standup/github/general",
    "project": "...",
    "type": "discord"
  }
  ```

4. **Blog Posts**
For sources like Waku blogs:
- Implement RSS feed parsing if available
- Extract article metadata
- Structure recommendations:
  ```python
  {
    "content": "...",
    "title": "...",
    "publish_date": "...",
    "author": "...",
    "url": "...",
    "project": "...",
    "type": "blog"
  }
  ```

5. **GitHub Repositories**
For technical repositories:
- Use GitHub API
- Focus on README files, documentation folders
- Structure recommendations:
  ```python
  {
    "content": "...",
    "repo": "...",
    "file_path": "...",
    "commit_hash": "...",
    "last_updated": "...",
    "project": "...",
    "type": "github"
  }
  ```

6. **Notion Content**
For Notion weeklies and documentation:
- Use Notion API
- Maintain page hierarchy
- Structure recommendations:
  ```python
  {
    "content": "...",
    "page_id": "...",
    "parent_page": "...",
    "last_edited": "...",
    "project": "...",
    "type": "notion"
  }
  ```

General Recommendations:

1. **Chunking Strategy**:
- Use semantic chunking where possible
- Maintain context windows of 512-1024 tokens
- Preserve metadata across chunks

2. **Update Frequency**:
- Implement different update schedules based on source:
  - Discord: Real-time or hourly
  - Websites: Daily
  - Documentation: On git commits
  - Blogs: Daily check for new content

3. **Error Handling**:
```python
try:
    # Ingestion logic
except Exception as e:
    logging.error(f"Failed to ingest {source}: {str(e)}")
    notify_admin(f"Ingestion failure for {source}")
```

4. **Validation Pipeline**:
```python
def validate_chunk(chunk):
    assert "content" in chunk
    assert "source" in chunk
    assert "timestamp" in chunk
    assert "project" in chunk
    assert "type" in chunk
```