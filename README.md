# mcp-simple-arxiv

An MCP server that provides access to arXiv papers through their API.

## Features

This server allows LLM clients (like Claude Desktop) to:
- Search for scientific papers on arXiv by title and abstract content
- Get paper metadata and abstracts
- Access links to available paper formats (PDF/HTML)

The server implements proper rate limiting according to arXiv's API guidelines (max 1 request every 3 seconds).

## Installation

```bash
pip install mcp-simple-arxiv
```

## Usage with Claude Desktop

Add this configuration to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "arxiv": {
      "command": "mcp-simple-arxiv"
    }
  }
}
```

After restarting Claude Desktop, the following capabilities will be available:

### Searching Papers

You can ask Claude to search for papers using queries like:
```
Can you search arXiv for recent papers about large language models?
```

The search will return basic information about matching papers including:
- Paper title
- Authors
- arXiv ID
- Publication date

### Getting Paper Details

Once you have a paper ID, you can ask for more details:
```
Can you show me the details for paper 2103.08220?
```

This will return:
- Full paper title
- Authors
- Publication and update dates
- Journal reference (if available)
- Paper abstract
- Links to available formats (PDF/HTML)

## Development

To install for development:
```bash
git clone https://github.com/andybrandt/mcp-simple-arxiv
cd mcp-simple-arxiv
pip install -e .
```

### arXiv API Guidelines

This server follows arXiv API usage guidelines:
- Rate limiting to max 1 request per 3 seconds
- Single connection at a time
- Proper error handling and retry logic

## License

MIT