# Shark Tank Business Evaluator — MCP Server

A local, bilingual MCP server that makes the public Shark Tank business-evaluation skill available to compatible AI clients through a prompt, a prompt-building tool, and Markdown resources.

## What it does

- Provides the prompt **evaluate_business_idea** for idea, pitch, investment-proposal, founder-pitch, existing-business, and opportunity reviews.
- Provides the tool **prepare_business_review** for clients that discover tools more reliably than prompts. It builds a complete review brief for the connected model.
- Exposes the skill and its financial, market-research, and investor-lens references as read-only resources.
- Supports Arabic, English, or a bilingual answer.

The server does not call an LLM, browse the web, or calculate a verdict by itself. It supplies the evaluation framework and user brief to the host AI model, which performs the analysis using its available capabilities. The server uses local stdio transport and does not send the brief to a remote service or write it to disk.

## Requirements

- Node.js 20 or newer
- An MCP-compatible client

## Run from a local checkout

~~~sh
npm install
npm start
~~~

The package exposes a command named shark-tank-mcp-server. Once the package is published, a standard stdio MCP client can start it with:

~~~sh
npx -y @osama101979-afk/shark-tank-mcp-server
~~~

A generic client configuration looks like:

~~~json
{
  "mcpServers": {
    "shark-tank-business-evaluator": {
      "command": "npx",
      "args": ["-y", "@osama101979-afk/shark-tank-mcp-server"]
    }
  }
}
~~~

Client setup screens and configuration locations differ. Use the client's MCP server setup instructions.

## Available resources

- shark-tank://skill/core
- shark-tank://skill/financial-review
- shark-tank://skill/market-research
- shark-tank://skill/investor-lenses

## Publish to the official MCP Registry

The package metadata includes a matching mcpName and registry server.json. The official registry flow requires an installable package to be published first. After publishing this scoped npm package:

~~~sh
mcp-publisher login github
mcp-publisher validate
mcp-publisher publish
~~~

The registry publisher uses GitHub-based namespace authentication for io.github.osama101979-afk/. Publishing the npm package and registering the server require the owner's own npm/GitHub authentication.

## Rights and attribution

This project has no open-source license. Public visibility does not grant permission to reuse or redistribute the skill content. Investor lenses are analytical inferences based on publicly documented backgrounds, not claims about private thoughts, endorsement, or affiliation with any television program or investor.

The public skill source is https://github.com/osama101979-afk/shark-tank-skill-public.
