# Sound-Out v0.1.1 - macOS Audio Output Manager

A command-line tool for macOS that allows you to manage audio output devices for applications.

## Features

- List all available audio output devices
- List running applications 
- Set the default audio output device (requires SwitchAudioSource)
- Basic structure for per-application audio routing (requires advanced techniques)

## Installation

1. Build from source:
   ```bash
   cargo build --release
   ```
   
2. The binary will be available at `target/release/sound-out`

3. For device switching functionality, install SwitchAudioSource:
   ```bash
   brew install switchaudio-osx
   ```

## Usage

### List available audio devices
```bash
./sound-out list-devices
```

### List running applications
```bash
./sound-out list-apps
```

### Set default audio output device
```bash
./sound-out set-default "AirPods"
# or by ID
./sound-out set-default "1"
```

### Set audio output for specific application
```bash
./sound-out set-app-output "Music" "AirPods"
```

Note: Per-application audio routing requires advanced Core Audio techniques and is not fully implemented in this demo.

## Technical Notes

This tool demonstrates several approaches to audio management on macOS:

1. **Device Enumeration**: Uses `system_profiler` to get audio device information
2. **Device Switching**: Relies on the `SwitchAudioSource` utility for reliable device switching
3. **Application Audio Routing**: Would require:
   - Audio Hijacking (special permissions required)
   - Aggregate device creation
   - Audio Unit processing
   - Private Core Audio APIs

## Limitations

- Application-specific audio redirection requires advanced techniques beyond the scope of this demo
- Some features require additional tools (SwitchAudioSource)
- Root privileges may be required for certain operations

## Development

This project uses Rust and is designed to work on macOS only. The main dependencies are:

- `clap` for command-line argument parsing
- `anyhow` for error handling
- `serde_json` for parsing system profiler output

## Future Enhancements

- Full per-application audio routing implementation
- GUI interface
- Audio profiles/presets
- Real-time audio monitoring
- Integration with macOS notification system