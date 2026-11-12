<p align="center">
  <img src="assets/logo.png" alt="Catalio" width="128" height="128">
</p>

# Catalio MCP

Connect AI agents to [Catalio](https://catalio.ai) through Catalio's hosted [Model Context Protocol](https://modelcontextprotocol.io/) server.

Catalio is an AI platform that pulls institutional knowledge out of legacy systems and enterprise platforms and turns it into a **living specification**: features, requirements, policies, journeys, and the rules that govern them. Connect a repository, API, or metadata export, and Catalio brings in every field, endpoint, rule, and job with an AI summary. It then reverse-engineers the specification and keeps it current as the software changes. Teams use it to plan initiatives, run gap analysis between what a legacy system does and what its replacement needs, and trace delivery back to the specification. Learn more in the [Catalio docs](https://catalio.ai/docs).

This repository is the Cursor Marketplace plugin for the Catalio MCP server. It also holds the shared logo and listing copy for other MCP clients.

| | |
| --- | --- |
| Server URL | `https://catalio.ai/mcp?v=2` |
| Transport | Streamable HTTP (remote, hosted by Catalio) |
| Auth | OAuth with your Catalio account (Auth0 at `auth.catalio.ai`), dynamic client registration |

## What agents can do

The server exposes 167 tools. Grouped by area:

| Area | Tools | What agents can do |
| --- | ---: | --- |
| Initiatives, scope, and delivery stages | 22 | Create and track initiatives, manage their scope, move them through planning → approval → build → release → retro, run gap analysis, and read planned issues and builds |
| Requirements, use cases, and tests | 32 | Create, read, update, link, flag, and grade requirements; manage use cases, test cases, and test results |
| Applications, versions, and architecture pages | 17 | Register applications and versions, record detected capabilities, features, processes, and entities, and write architecture diagram pages |
| Capabilities, features, components, processes, and policies | 20 | Maintain the catalog of capabilities (with maturity assessments), features, components, processes, business rules, and policies |
| Personas, jobs to be done, and journeys | 20 | Manage personas and JTBDs, capture user journeys step by step, compute friction impact, and compare legacy vs. target journeys |
| Questions and decisions | 17 | Track open and blocking questions; record decisions, link them to entities, supersede them, and export ADRs |
| Extract scans and candidates | 8 | Start and poll Extract scans and triage the candidates they surface |
| Change proposals | 7 | Create, review, dismiss, restore, and mark change proposals applied |
| Issue links (Linear, GitHub, Jira, Azure DevOps) | 7 | Link external tracker issues to requirements, initiatives, and applications |
| Pages and artifacts | 9 | Write, search, and update Catalio pages (runbooks, playbooks, architecture notes) and attach artifacts |
| Repositories and build sandbox | 5 | Onboard repositories, work with branches in a task sandbox, and fetch product context for pull request review |
| Organizations and utilities | 3 | List and switch Catalio organizations, and batch several write calls into one |

The hosted server is the source of truth for tool names and schemas. Your client lists the current set when it connects.

<details>
<summary>Full tool list</summary>

**Initiatives, scope, and delivery stages** (22): `advance_to_approval`, `advance_to_build`, `advance_to_release`, `advance_to_retro`, `analyze_implementation_gaps`, `archive_initiative`, `connect_entity`, `create_initiative`, `disconnect_entity`, `find_builds`, `get_initiative`, `get_next_build_queue_item`, `list_initiative_scope`, `list_initiatives`, `list_planned_issues`, `revert_to_approval`, `revert_to_planning`, `run_gap_analysis`, `start_discovery_session`, `update_discovery_phase`, `update_initiative`, `update_scope_item`

**Requirements, use cases, and tests** (32): `create_requirement`, `create_test_case`, `create_test_result`, `create_use_case`, `delete_requirement`, `flag_requirement`, `flag_use_case`, `get_happy_path_use_case`, `get_requirement`, `grade_distribution`, `link_requirement`, `link_use_case`, `list_component_requirements`, `list_policy_requirements`, `list_process_requirements`, `list_requirement_components`, `list_requirement_personas`, `list_requirement_policies`, `list_requirements`, `list_requirements_filtered`, `list_test_cases`, `list_test_results_by_test_case`, `list_use_cases`, `list_use_cases_by_requirement`, `regrade_requirement`, `set_component_requirement_status`, `set_use_case_primary_requirement`, `show_requirement_card`, `unlink_requirement`, `update_requirement`, `update_test_case`, `update_use_case`

**Applications, versions, and architecture pages** (17): `create_application`, `create_application_capability`, `create_application_entity`, `create_application_feature`, `create_application_process`, `create_application_type_tag`, `create_application_version`, `delete_application_version`, `get_application_version`, `link_components_to_application`, `list_application_versions`, `list_applications`, `list_components_for_application`, `list_diagram_prompts`, `update_application`, `update_application_version`, `write_diagram_page`

**Capabilities, features, components, processes, and policies** (20): `create_business_rule`, `create_capability`, `create_capability_assessment`, `create_component`, `create_feature`, `create_policy`, `create_process`, `delete_capability_assessment`, `list_capabilities`, `list_capability_assessments`, `list_components`, `list_features`, `list_policies`, `list_processes`, `merge_feature`, `update_capability`, `update_capability_assessment`, `update_component`, `update_policy`, `update_process`

**Personas, jobs to be done, and journeys** (20): `add_journey_step`, `complete_journey`, `compute_journey_impact`, `create_comparison`, `create_journey`, `create_jtbd`, `create_persona`, `delete_persona`, `get_comparison`, `get_journey_summary`, `get_jtbd`, `list_comparisons`, `list_journey_steps`, `list_journeys`, `list_jtbds`, `list_personas`, `update_comparison`, `update_journey_step`, `update_jtbd`, `update_persona`

**Questions and decisions** (17): `create_decision`, `create_question`, `defer_question`, `delete_question`, `export_decision_adr`, `link_decision`, `list_decisions_by_initiative`, `list_decisions_for_entity`, `list_open_blocker_questions`, `list_questions`, `reopen_question`, `resolve_question`, `show_decision_card`, `supersede_decision`, `unlink_decision`, `update_decision`, `update_question`

**Extract scans and candidates** (8): `approve_process_candidate`, `dismiss_process_candidate`, `get_extract_status`, `list_extract_candidates`, `record_extract_scan_head`, `start_extract_scan`, `triage_candidate`, `undismiss_process_candidate`

**Change proposals** (7): `create_change_proposal`, `delete_change_proposal`, `dismiss_change_proposal`, `list_change_proposals`, `mark_change_proposal_applied`, `restore_change_proposal`, `update_change_proposal`

**Issue links (Linear, GitHub, Jira, Azure DevOps)** (7): `create_issue_link`, `delete_issue_link`, `get_issue_link`, `list_application_issue_links`, `list_initiative_issue_links`, `list_issue_links`, `set_issue_link_initiative`

**Pages and artifacts** (9): `create_artifact`, `create_page`, `get_artifact`, `get_page`, `list_artifacts_by_parent`, `list_pages`, `search_pages`, `update_page`, `write_requested_page`

**Repositories and build sandbox** (5): `add_repository`, `fetch_branch`, `get_pr_context`, `publish_branch`, `start_repository_onboarding`

**Organizations and utilities** (3): `batch`, `list_my_organizations`, `set_active_organization`

</details>

## Install

### Cursor

**From the marketplace:** open **Cursor Settings → Plugins**, search for **Catalio**, and select **Install**. Then complete the Catalio sign-in prompt.

**Manually:** add this to `~/.cursor/mcp.json` (all projects) or `.cursor/mcp.json` (one project):

```json
{
  "mcpServers": {
    "catalio": {
      "type": "http",
      "url": "https://catalio.ai/mcp?v=2"
    }
  }
}
```

Cursor opens the Catalio sign-in page the first time the server connects.

### ChatGPT

Custom MCP servers are available on ChatGPT web. Business, Enterprise, and Edu workspaces get full read and write access. Workspace admins may need to allow custom MCP servers first.

1. Open **Plugins** in ChatGPT on the web.
2. Select the plus button, then **Add custom MCP server**.
3. Name it `Catalio` and enter the server URL `https://catalio.ai/mcp?v=2`.
4. Choose **OAuth** for authentication.
5. Accept the risk warning and select **Create as a plugin**, then sign in with your Catalio account.
6. Install the plugin, then select it with `@Catalio` in a conversation.

### Claude

1. In Claude, open **Settings → Connectors**.
2. Select **Add custom connector**.
3. Enter `Catalio` as the name and `https://catalio.ai/mcp?v=2` as the URL.
4. Select **Connect** and sign in with your Catalio account.

On Team and Enterprise plans, an owner may need to add the connector for the organization first.

### Other MCP clients

Any client that supports remote Streamable HTTP servers with OAuth can connect:

- **URL:** `https://catalio.ai/mcp?v=2`
- **Auth:** OAuth. The client discovers the authorization server from the MCP endpoint and registers itself through dynamic client registration. You don't need a client ID, secret, or API key.

For clients that only support stdio, use a remote-to-stdio bridge such as [`mcp-remote`](https://www.npmjs.com/package/mcp-remote):

```json
{
  "mcpServers": {
    "catalio": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://catalio.ai/mcp?v=2"]
    }
  }
}
```

## Sign-in and privacy

- You need a Catalio account. The first time you connect, your client opens Catalio's sign-in page at `auth.catalio.ai`. There are no API keys to create or store.
- Each tool call runs as the signed-in user, inside that user's active Catalio organization, and can never exceed that user's permissions. If you belong to more than one organization, `list_my_organizations` and `set_active_organization` show and switch the active one.
- Write tools change data in your Catalio organization. Most clients ask you to confirm a tool call before it runs.
- Catalio hosts the server. This plugin only contains configuration and does not run local code.
- Removing the connector from your client disconnects that client.
- With the stdio setup, `mcp-remote` stores its sign-in tokens in `~/.mcp-auth` (or `MCP_REMOTE_CONFIG_DIR`). Removing the connector does not delete them. Delete that directory to remove the stored tokens from this device.
- See Catalio's [Privacy Policy](https://catalio.ai/privacy) and [Terms of Service](https://catalio.ai/terms).

## Repository contents

| Path | Purpose |
| --- | --- |
| `.cursor-plugin/plugin.json` | Cursor plugin manifest |
| `mcp.json` | MCP server definition (`https://catalio.ai/mcp?v=2`) |
| `assets/logo.png` | Square Catalio mark, 512×512, for marketplace listings |
| `assets/logo-wordmark.png` | Catalio wordmark |

## Support

- Website: https://catalio.ai
- Docs: https://catalio.ai/docs

## License

MIT. See [LICENSE](LICENSE). The Catalio name and logo are not covered by the MIT license.
