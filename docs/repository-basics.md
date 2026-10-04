# Repository foundations

File handling conventions live in the project directory and work independently of a particular editor, AI tool, or hosting platform.

| File | Purpose |
| --- | --- |
| `.gitignore` | Exclude machine-specific materials, environment configuration, common credentials, editor state, logs, and operating system files |
| `.editorconfig` | Define UTF-8, final newlines, and LF by default; use two-space indentation for JSON and YAML |
| `.gitattributes` | Normalize text line endings in Git and preserve images and office documents as binary content |

## Local and shared materials

- `.local/` holds personal network settings, tool paths, machine configuration, and notes. The entire directory stays outside Git.
- Root-level `scratch/`, `tmp/`, `temp/`, and `logs/` directories hold temporary output. Nested directories with these names are not excluded wholesale by those root-level rules.
- `.env` files and variants are ignored by default. Examples ending in `.example`, `.sample`, or `.template` can be shared, but must use placeholder values and still require content review.
- Local VS Code files are ignored; `.vscode/extensions.json` can be shared as an extension recommendation. Review and explicitly allow any additional shared editor configuration.
- Documentation, task records, dependency lockfiles, PDFs, images, and office documents remain trackable. Log files are ignored by default; put lasting validation conclusions in task records and retain necessary sanitized evidence in an appropriate document format.

Ignore rules affect untracked files. They do not remove previously committed materials or replace checks for secrets and sensitive content. Check that rule changes do not hide shared files, and do not force-add the local workspace.

## Text and binary files

Text uses UTF-8 and LF by default. Windows `.bat` and `.cmd` scripts use CRLF in working copies. Markdown may retain trailing spaces that express line breaks; other text trims excess trailing whitespace.

Binary attributes preserve content and disable ordinary text diffs and automatic merging; they do not exclude files. Review normalization of tracked files separately rather than automatically rewriting existing content or history.

EditorConfig behavior depends on editor support. People and AI assistants should follow the conventions even without a supporting editor. Add actual dependency and build outputs, and development commands, once the technology stack is selected.

## Local checks

Run these commands from the repository directory:

```sh
git status --short --ignored
git check-ignore -v .local/AGENTS.md .env
git check-attr text eol diff merge -- README.md docs/example.pdf
git diff --check
```

`git check-ignore` returns exit code 1 for files that are not ignored; this is expected. Use `--no-index` to inspect rules for sample paths when needed. Actual content and tracking state still determine whether a file can be shared.

These commands inspect local rules without network access, commits, or pushes.
