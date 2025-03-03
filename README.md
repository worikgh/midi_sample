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

`MidiSampleQzn3tMidi` 

## Jack Port

`MidiSampleQzn3tJack:output`
