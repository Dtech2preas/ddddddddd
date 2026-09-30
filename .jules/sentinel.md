## 2024-05-24 - Document Object Property XSS fix
**Vulnerability:** innerHTML and template literal XSS
**Learning:** Found potential XSS in `doc.title` and `doc.body.innerHTML` handling, which is used to build the final HTML document in `worker.js` and `index.html`.
**Prevention:** Sanitize the input or use DOM APIs safely.
## 2024-05-24 - SSRF in Worker Fetch
**Vulnerability:** The worker fetches `targetUrl` directly without validating the protocol. An attacker could pass `file:///` or other schemas.
**Learning:** Always validate the URL protocol to restrict `fetch` to `http:` and `https:`.
**Prevention:** Add a `URL` parse and check `urlObj.protocol === 'http:' || urlObj.protocol === 'https:'`.
