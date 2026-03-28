# Session Playbook

This playbook holds the detailed patterns that make the live browser session useful without becoming intrusive.

## 1. Reuse the Current Session Deliberately

Prefer the live Chrome DevTools session when the task depends on:

- Signed-in state
- Current cookies or app context
- An already selected Elements or Network target
- Existing app state that would be expensive to reproduce

Start by checking what is already open:

- `list_pages` to understand available pages
- `select_page` to move into the right one
- `take_snapshot` to inspect current structure before interacting

Use the user's existing page when their current state is the point of the task. Otherwise, create or select your own working page so you do not disturb their main tab.

If the live browser session is expected but unavailable:

- say clearly that you do not currently have the live browser session
- fall back to a public-web or Playwright path only if that still serves the goal
- explain that a clean fallback browser is not equivalent to the user's current signed-in session

## 2. Tab Hygiene

### Prefer non-destructive behavior

- Do not close pages you did not open.
- Do not reload the user's page just because it is convenient.
- Do not bring pages to the front unless the task or user requires it.
- If experimentation may be disruptive, open a separate page and keep the original intact.

### When to use the active page

Use the active page directly when:

- The user explicitly wants you to continue from their current debugging state.
- The relevant request or element is already selected.
- Reproducing the state elsewhere would lose the point of the task.

## 3. DOM-First Extraction

Prefer structured evidence over screenshots:

1. `take_snapshot` for the accessible page structure and selected-element context
2. `evaluate_script` for data, state, attributes, computed values, and DOM traversal
3. Network and console tools when the answer may not be visible in the DOM
4. `take_screenshot` only when rendered pixels actually matter

### Good DOM-first cases

- Hidden text already mounted in the DOM
- Link targets and image sources
- Data attributes, ARIA state, classes, and inline styles
- Video metadata like `currentTime`, `duration`, and pause state
- Values inside open shadow roots or same-origin page structures reachable from script

### When DOM-first may fail

- Cross-origin iframes or inaccessible embedded contexts
- Canvas-only or screenshot-only content
- Visual bugs where the pixels matter more than the markup

If the DOM route stalls, switch to a more suitable layer instead of forcing OCR or repeated snapshots.

### Site-generated links beat guessed URLs

If the page already exposes a link, image URL, or media URL:

- prefer the exact site-generated URL
- preserve the query string and other context unless you know they are optional
- treat "manually simplified" URLs as suspect if the site starts returning misleading errors

## 4. GUI vs Programmatic Interaction

There are two main interaction styles:

- Programmatic: direct DOM reads and writes through `evaluate_script`, fast navigation, and structured extraction
- GUI-like: `click`, `fill`, `hover`, keyboard input, scrolling, and screenshots that behave more like a user

Prefer programmatic work when:

- The data already exists in the page
- You need reliable extraction rather than user simulation
- Direct DOM access is simpler than replaying UI steps

Prefer GUI-style interaction when:

- A real user gesture matters
- The site reacts poorly to direct DOM manipulation
- The page needs scrolling, expansion, hovering, or upload interactions to reveal the real state

If a site resists one mode, switch rather than retrying the same tactic.

If the UI looks like a blocker, first ask whether it really blocks the data. Sometimes the content is already present in the DOM or network layer and the visible interaction is only a presentation detail.

## 5. Lazy Loading, Hidden Data, and Media

### Lazy-loaded pages

- Scroll before concluding content is missing
- Re-snapshot after major state changes
- Look for content URLs, placeholders, or hydration data before resorting to screenshots
- Treat "empty" or "not found" UI states carefully when the route or parameters may be wrong

### Images and media

- Prefer extracting image and media URLs from the DOM or page scripts
- Use screenshots when the rendered image itself is the subject
- If a file URL is public and directly downloadable, prefer a raw fetch over full-page screenshot analysis

### Video sampling

Use `evaluate_script` on the relevant `<video>` element to:

- Inspect `currentTime`, `duration`, and playback state
- Seek to a target timestamp when the page allows it
- Pause on a representative frame

Then capture the rendered frame with `take_screenshot` if visual analysis is needed.

## 6. Login Handling

The live browser session is valuable because the user may already be signed in.

### Default rule

Try to access the target through the live browser session first. If the data is available, keep going without making login a separate task.

### When to pause and ask

Pause only when:

- The needed content is clearly blocked by authentication
- The current live session does not already grant access
- Logging in inside the user's real Chrome would unlock the task

In that case, ask the user to log in in Chrome and continue after they confirm. Do not default to reproducing the login flow in an isolated browser unless the user asked for that.

## 7. DevTools Handoff

### Selected element workflow

- Start with `take_snapshot`
- Use `evaluate_script` for nearby DOM state, computed values, or targeted extraction
- Use interaction tools only after understanding the current structure

### Selected network request workflow

- Start with `get_network_request` without `reqid`
- Inspect status, headers, payloads, and failure text
- Broaden to `list_network_requests` only if the surrounding traffic matters

## 8. Public-Source Verification

When the task is about truth, not interaction:

- Prefer primary sources over copied reporting
- Use `web` for discovery and citations
- Attach to the live browser session only when the source is dynamic, authenticated, or otherwise inaccessible from the public-web path

The browser is not automatically more authoritative than the public-web path. Use the right layer for the claim you need to support.

## 9. Troubleshooting Fallbacks

If the live browser session approach is blocked:

- Check whether the target actually needs the live browser session
- Check whether a cheaper processed read or raw fetch path can answer the question first
- Consider whether a public `web` path is sufficient after all
- Use Playwright if the task wants a separate clean browser context
- Mention `--autoConnect` or `--browser-url` only if the issue is truly about session attachment or Chrome DevTools MCP configuration

## 10. Parallel Research

When several targets are independent:

- batch `web` lookups before reaching for agents
- keep each browser investigation in its own page context
- if the user explicitly asked for parallel agent work, frame each delegated task around the goal and success condition instead of hard-coding the tool layer too early

Do not split work that depends on one evolving page state.
