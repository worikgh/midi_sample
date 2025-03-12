# MIDI Sample Player

## Configuration File

JSON format, array of `SampleDescr`.

Path to the sample and the MIDI note to trigger it

```rust
struct SampleDescr {
    path: String,
    note: u8,
}
struct Config {
    samples_descr: Vec<SampleDescr>,
}
```

## MIDI Port

A MIDI port named `MidiSampleQzn3tMidi` is created to receive MIDI signals.  Notes are looked up in the `SampleDescr`s and played when MIDI notesample arrives

## Jack Port

A Jack port named `MidiSampleQzn3tJack:output` is the output
