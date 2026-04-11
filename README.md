# Pilot

[Pilot](http://wiki.xxiivv.com/Pilot) is a **UDP synthesizer** designed to be controlled externally. It was created as a companion application to the livecoding environment [ORCA](https://hundredrabbits.itch.io/orca). 

## Install & Run

You can download [builds](https://hundredrabbits.itch.io/pilot) for **OSX, Windows and Linux**, or if you wish to build it yourself, follow these steps:

```
git clone https://github.com/hundredrabbits/Pilot.git
cd Pilot/desktop/
npm install
npm start
```

<img src='https://raw.githubusercontent.com/hundredrabbits/Pilot/master/resources/preview.jpg' width="600"/>

## Commands

Pilot has 16 voices and 8 effects. Commands can be entered directly with the input bar, or through UDP via the port `49161`. You can send multiple commands at once by using the `;` character. For example, `03C;13E` will play a `C3` and `E3` chord.

### Channel

- 0 to 5 is **A**mplitude **M**odulation (poly)
- 6 to 9 is **F**requency **M**odulation (poly)
- 10 to 11 is a single oscillator, a filter and two envelopes (mono)
- 12 to 14 is a single oscillator with an amplitude envelope and frequency ramp to emulate membrane (mono)

#### Drums

The last voice (F) features a sample player with 116 drum sounds from the Roland TR-808, 
with courtecy of [Michael Fischer](https://github.com/tidalcycles/sounds-tr808-fischer) .

- BASS DRUMS (C0 - C2) - 25 samples
- SNARES (C#2 - C#4) - 25 samples
- CYMBALS (D4 - D6) - 25 samples
- TOMS: LOW, MID, HI (D#6 - F7) - 15 samples
- CONGAS: LOW, MID, HI (F#7 - G#8) - 15 samples
- HI-HATS SECTION (A8 - D9) - [ 1 Closed, 5 Open]
- ONE-SHOTS (D#9 - G9) - [Cowbell, Clave, Clap, Maracas, Rimshot]

To use your own sample set, add audio files to the [media](desktop/sources/media) folder and edit [mapping.json](desktop/sources/mapping.json) to your needs.  

#### Play

The Play commands allows you to play synth notes.

| Command  | Channel | Octave | Note | Velocity | Length |
| :-       | :-:     | :-:    | :-:  | :-:      | :-:    |
| `04C`    | 0       | 4      | C    | _64_     | _1/16_ |
| `04Cf`   | 0       | 4      | C    | 127      | _1/16_ |
| `04Cff`  | 0       | 4      | C    | 127      | 1bar   |

#### Settings

The Settings commands allow you to change the sound of the synth. The settings command format is a **channel** value between `0-G`, a 3 characters long **name**, followed by four values between `0-G`. The possible waveforms are `si`, `2i`, `4i`, `8i`, `tr`, `2r`, `4r`, `8r`, `sq`, `2q`, `4q` `8q`, `sw`, `2w`, `4w` and `8w`.

| Command     | Channel | Name         | Info |
| :-          | :-      | :-           | :-   |                    
| `0ENV056f`  | 0       | Envelope     | Set **Attack**:0.00, **Decay**:0.33, **Sustain**:0.40 and **Release**:1.00 |
| `1OSCsisq`  | 1       | Oscilloscope | Set **Osc1**:Sine, **Osc2**:Square |

### Global

#### Effects

The Effects are applied to all channels. The effect command format is a 3 characters long **name**, followed by one value between `0-G` for **wet** and **depth**.

| Command     | Channel | Operation  | Info |
| :-          | :-      | :-         | :-   |
| `BITff`     | All     | Bitcrusher | ..   |
| `DISff`     | All     | Distortion | ..   |
| `WAHff`     | All     | AutoWah | ..   |
| `CHEff`     | All     | Chebyshev | ..   |
| `FEEff`     | All     | Feedback   | ..   |
| `DELff`     | All     | Ping Pong Delay   | ..   |
| `TREff`     | All     | Tremolo   | ..   |
| `REVff`     | All     | Reverb     | ..   |
| `PHAff`     | All     | Pashor     | ..   |
| `VIBff`     | All     | Vibrato     | ..   |
| `CHOff`     | All     | Chorus     | ..   |
| `STEff`     | All     | StereoWidener     | ..   |
| `EQUff`     | All     | EQ3     | ..   |
| `COMff`     | All     | Compressor     | ..   |
| `VOLff`     | All     | Volume     | ..   |
| `LIMff`     | All     | Limiter     | ..   |

#### Masters

`EQU0`, `COM0`, `VOL0`, `LIM0`, 0-z to set levels, reset for initial values.

dB metering ![#f03c15](https://placehold.co/15x15/f03c15/f03c15.png) `-6`
 ![#ffff00](https://placehold.co/15x15/ffff00/ffff00.png) `-18`
  ![#00ff00](https://placehold.co/15x15/00ff00/00ff00.png) `-48`
  ![#f0f0f0](https://placehold.co/15x15/f0f0f0/f0f0f0.png) `no  signal`

#### Special

- `bpm140`, sets the BPM to `140`. This command is designed to apply to effects like feedback.
- `renv`, randomizes envelopes.
- `rosc`, randomizes oscillators.
- `refx`, randomizes effects.
- `reset`, reset all.

## Record

Press **cmd/ctrl+r** to record, and press it again to stop.

## Convert OGG to MP3

Just use ffmpeg.

```
~/Documents/ffmpeg -i last.{ogg,mp3}  
```

<img src='https://raw.githubusercontent.com/hundredrabbits/Pilot/master/resources/device.jpg' width="600"/>

## Extras

- This application supports the [Ecosystem Theme](https://github.com/hundredrabbits/Themes).
- Support this project through [Patreon](https://www.patreon.com/hundredrabbits).
- See the [License](LICENSE.md) file for license rights and limitations (MIT).
- Pull Requests are welcome!
