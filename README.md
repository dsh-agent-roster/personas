# Personas

**English** | [简体中文](README.zh.md)

An [Agent Roster](https://github.com/dsh-agent-roster/dsh-agent-roster) archive of **single personas**:
each roster has no members and carries one `captain.persona`. Apply one to an existing session and the
session works as that persona — no team is created, no members are spawned.

| Roster | What it makes the session do |
|---|---|
| `code-reviewer` | Review only: rank risks by "can this break production", every finding carries a file/line, a command output, or a call chain |
| `architect` | Constraints first, then two or three options with their costs, what is explicitly out of scope, and the rollback path |
| `debugger` | Reproduce before changing anything, one hypothesis at a time, smallest fix, closing evidence (command + before/after output) |

## Not a migration

Unlike the other archives in this organisation, these texts are **written for this project**; they are not
copied from an upstream repository. The single-agent system prompts we looked at upstream (SWE-agent's
`system_template`, OpenHands' Jinja template, gemini-cli's TypeScript prompt builders) are either one
sentence of framing or fragments with template variables — extracting them verbatim produces a thinner
persona than writing one.

## Usage

```bash
npx --yes @stofone/dsh-agent-roster@latest validate --dir .     # 3 personas, 0 members each
```

Subscribe to `dsh-agent-roster/personas` in the plugin panel's Library tab, then use "Apply" on a session.
Requires the plugin **>= 1.33.0** (that is the release that allows `members: []`).

## Structure

```
space.yaml
rosters/{id}/roster.yaml        members: [] + captain.persona
rosters/{id}/personas/self.md   the persona text itself
dist/{id}-1.0.0.json            compiled artifact
```
