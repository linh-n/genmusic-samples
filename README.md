# genmusic-samples

Audio samples for [genmusic](https://github.com/linh-n/genmusic). Loaded at runtime via CDN — the genmusic library itself stays tiny.

## Usage

```js
import { GenMusic } from 'genmusic';

// Default: loads from this repo via jsDelivr CDN
const engine = new GenMusic({ seed: 42 });

// Custom sample host:
const engine = new GenMusic({
  seed: 42,
  samplesUrl: 'https://your-cdn.com/samples'
});
```

## Instruments

| Instrument | Samples | Velocities | Size | License |
|---|---|---|---|---|
| **piano** | 30 notes × 16 velocities = 480 | 16 layers | ~85MB | Public Domain |

More instruments coming (guitar, bass, drums).

## File Structure

Each instrument has a `manifest.json` describing its contents:

```
piano/
  manifest.json
  A0v1.mp3
  A0v2.mp3
  ...
  C8v16.mp3
```

### Manifest Schema

```json
{
  "name": "Human-readable name",
  "type": "chromatic",
  "notes": ["A0", "C1", ...],
  "velocities": [1, 2, ...16],
  "filePattern": "{note}v{velocity}.mp3"
}
```

For percussion (drums), `type` is `"kit"` and `notes` is replaced by `pieces`:

```json
{
  "type": "kit",
  "pieces": ["kick", "snare", "hihat-closed", ...],
  "velocities": [1, 2, ...],
  "filePattern": "{piece}v{velocity}.mp3"
}
```

## Naming Convention

- Notes: `C`, `Cs`, `D`, `Ds`, `E`, `F`, `Fs`, `G`, `Gs`, `A`, `As`, `B` (sharps as `s`)
- Octave: `0`-`8`
- Velocity: `v1` (softest) to `v16` (loudest)

## License

Each instrument's license is in its `manifest.json`. All included samples are free/open source.
