# MIDI Sample Player

A lightweight tool to play audio samples in response to MIDI input events.

## Features

- Play audio samples triggered by MIDI notes
- Simple JSON configuration
- Low-latency audio via JACK

## Requirements

- [JACK Audio Connection Kit](https://jackaudio.org/) (typically on Linux systems)
- Rust tool-chain (for building from source)

## Installation

```bash
cargo install --git https://github.com/worikgh/midi_sample.git
cd midi_sample
cargo build --release
```

## Configuration

Create a JSON config file (config.json) specifying your samples and their corresponding MIDI notes:

```json
{
  "samples_descr": [
	{
	  "path": "/path/to/sample1.wav",
	  "note": 60
	},
	{
	  "path": "/path/to/sample2.wav",
	  "note": 62
	}
  ]
}
```

## Usage

```bash
target/release/midi_sample /path/to/config.json
```

The program will:

	Create a MIDI input port named MidiSampleQzn3tMidi

	Create a JACK audio output port named MidiSampleQzn3tJack:output

Connect your MIDI controller to the input port and the audio output to your speakers/mixer.

## Technical Details

The configuration uses these Rust structures:

```rust
struct SampleDescr {
	path: String,  // Path to audio sample file
	note: u8,      // MIDI note number (0-127)
}

struct Config {
	samples_descr: Vec<SampleDescr>,  // Collection of sample mappings
}
```

## Supported Audio Formats

Any format supported by the [`symphonia`](https://docs.rs/symphonia/latest/symphonia/) crate.

From that website:

### Container Formats

The following container formats are supported.

* AIFF
* CAF
* ISO/MP4
* MKV/WebM
* OGG
* Wave

### Codecs

The following codecs are supported.

* AAC-LC
* ADPCM
* ALAC
* FLAC
* MP1
* MP2
* MP3
* PCM
* Vorbis

