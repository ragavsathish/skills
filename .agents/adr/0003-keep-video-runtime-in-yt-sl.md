# Keep the video runtime in yt-sl

`extract-video-slides` is the agent-facing workflow, while [`yt-sl`](https://github.com/ragavsathish/yt-sl) owns executable acquisition, caption handling, slide recovery, OCR, evidence generation, and subject-skill compilation. The skill contains instructions and metadata only; reusable Wasm modules stay under `yt-sl/components`. This keeps one runtime implementation while preserving a discoverable agent workflow.
