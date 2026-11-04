# WeChat Layout Studio

English | [中文](README.md)

A Skill and browser editing component for structuring WeChat Official Account articles and producing HTML layouts. Maintained by **Jackie0310**. The original Chinese product name is 公众号智排工作室.

## Included

- A `SKILL.md`, agent metadata, and structure/layout references for compatible assistant hosts.
- Plain JavaScript and CSS: Markdown/plain-text structure recognition, six preset themes, block editing and ordering, heading numbering, template capture, HTML preview and export.
- Rich-text clipboard support and HTML compatibility checks. Verify the actual paste result in the WeChat editor.
- Optional compatible chat-completion requests with local rule fallback. Local formatting is not AI proofreading or online fact checking.

This is not a complete backend or an automatic publishing service. It does not fetch the contents of input URLs. Review inferred headings, people and conclusions manually.

## Try locally without an API key

Use a modern desktop browser. The following static-server command requires Python 3. There are no npm/pip runtime dependencies, lockfiles or build steps in the supplied source.

1. Download and extract the repository, then enter its root directory.
2. Run:

   ```sh
   python -m http.server 8000 --bind 127.0.0.1
   ```

3. Visit `http://127.0.0.1:8000/examples/`, enter your article, select a preset and click the primary formatting button. Leaving the API key empty uses local rules.
4. Edit blocks and inspect the preview before copying or downloading HTML. The example supplies only basic host styles and the required modal container.

Skill installation depends on the host product. No WorkBuddy one-click installation command has been verified. The included `agents/openai.yaml` does not establish compatibility with every host. See [integration instructions](references/integration.md) for embedding the component.

## AI and data limitations

- On **HTTP localhost / 127.0.0.1**, the code posts `{endpoint, apiKey, payload}` to `/api/chat-completions`. The Python static server does not implement it; no proxy backend is included.
- On other origins, the code attempts a direct request to the configured Endpoint. Availability depends on the service, model, CORS and browser environment. Existing default Endpoint/model values are configuration, not availability guarantees. No external or paid AI request was tested.
- AI requests transmit the stage's input article/intermediate data to the configured service; the localhost proxy also receives the API key. Use only trusted hosts and services, and never embed long-lived keys in public pages.
- Keys use origin-scoped `sessionStorage`. Articles, templates, settings and results use `localStorage`. Neither is encrypted storage, and same-origin scripts can read it. Debug exports contain article/template content; review them before sharing.
- Imported HTML receives basic filtering, not a security sandbox for untrusted input. Only import trusted templates. Remote images, links and styles may make external requests. Use a trusted local environment or a hardened host.

## Verification

```sh
node --check assets/editor/wechat-editor.js
```

With the static server running, visit `http://127.0.0.1:8000/assets/editor/wechat-editor-tests.html` for the original seven A–G acceptance checks. See [verification records](docs/VERIFICATION.md) for actual results and scope. These checks do not establish uniform rendering across WeChat clients, template licensing, or AI accuracy.

Release preparation retains the layout core. Only two source strings change: an unsupported performance claim in the built-in sample is replaced by explicit demonstration text, and an error message no longer points to an absent launcher. No real user articles, customer data, credentials, image files or font files are bundled. Synthetic acceptance-test text and labeled demonstration text remain.

## Repository contents

`SKILL.md`, `agents/`, `assets/editor/`, `references/`, `examples/index.html`, `docs/VERIFICATION.md`, `PROVENANCE.md`, `CONTRIBUTING.md`, `CHANGELOG.md`, and `LICENSE`.

## License and contributions

This release uses the [MIT License](LICENSE), copyright 2026 Jackie0310. On 2026-11-04 the maintainer confirmed the right to relicense and authorized public distribution. The original archive had a restrictive commercial license; this confirmation is not independent proof of the complete authorship chain. See [provenance and unresolved checks](PROVENANCE.md). Imported content and platform trademarks are not licensed by this project.

See [CONTRIBUTING.md](CONTRIBUTING.md). This project is not an official WeChat/Tencent product and implies no platform endorsement.
