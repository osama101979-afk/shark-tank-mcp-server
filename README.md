# Shark Tank Business Evaluator — MCP Server

A local, bilingual MCP server that makes the public Shark Tank-inspired business-evaluation skill available to compatible AI clients through a prompt, a prompt-building tool, and Markdown resources.

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

The package exposes a command named **shark-tank-mcp-server**. After the npm package is published, a standard stdio MCP client can start it with:

~~~sh
npx -y @osama101979/shark-tank-mcp-server
~~~

A generic client configuration looks like:

~~~json
{
  "mcpServers": {
    "shark-tank-business-evaluator": {
      "command": "npx",
      "args": ["-y", "@osama101979/shark-tank-mcp-server"]
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

## First publication

The package is scoped to the npm account **osama101979**. From the repository root, publish the first version using that account:

~~~sh
npm login
npm publish --access public
~~~

The public package name is **@osama101979/shark-tank-mcp-server**. Do not share npm passwords, one-time codes, or access tokens.

## Publish to the official MCP Registry

Publish the npm package first. Then, from the repository's **Actions** tab, run the **Publish to MCP Registry** workflow. It uses GitHub OIDC authentication, validates server.json, and submits the server to the official Registry.

To publish manually instead, install the official **mcp-publisher** CLI from the [MCP Registry releases](https://github.com/modelcontextprotocol/registry/releases), then run from the repository root:

~~~sh
mcp-publisher login github
mcp-publisher validate
mcp-publisher publish
~~~

The Registry entry uses the **io.github.osama101979-afk/** namespace. npm and the MCP Registry are separate publications.

## Rights and attribution

This project has no open-source license. Public visibility does not grant permission to reuse or redistribute the skill content. Investor lenses are analytical inferences based on publicly documented backgrounds, not claims about private thoughts, endorsement, or affiliation with any television program or investor.

The public skill source is https://github.com/osama101979-afk/shark-tank-skill-public.
