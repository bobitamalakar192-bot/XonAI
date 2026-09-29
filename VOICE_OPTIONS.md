# XonAI AI Voice Options

XonAI Voice Teacher now supports selectable AI TTS voices instead of relying on the device/browser voice by default.

## Voice selector
- Male-style: Cedar, Echo, Onyx
- Female-style: Marin, Coral, Shimmer
- Neutral-style: Alloy

The labels describe the presentation style only; they are not claims that a voice belongs to a real person.

## Production configuration
Set `TTS_PROVIDER=openai` and configure `OPENAI_API_KEY`. The backend uses `/api/speech/synthesize`. If cloud TTS is unavailable, the frontend can fall back to the browser speech engine.

OpenAI's current Audio API documents these built-in TTS voices, including Cedar, Echo, Onyx, Marin, Coral, Shimmer and Alloy.
