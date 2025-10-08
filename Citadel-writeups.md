# 8. Selected Ambient Work
## Description
The symphonic adventure does not end here. On the next floor, a single song keeps echoing through the floor, repeating in a haunting loop. Amid the sound, you find a note left by a past candidate. It hints that the song holds a secret message, hidden in plain sight, much like how Aphex Twin concealed his face within his music with the help of spectrograms.

To move forward, you must find the message hidden in this sound.

Note: Separate the words in the flag with _ and make it UPPERCASE. Example: citadel{S3L3CT3D_AMB13NT_W0RK}

## Solve
Upon opening the WAV file, a few seconds into the music, Morse code starts playing and it plays throughout the rest of the audio.

The Morse code audio isn't easily decodable by online tools due to the audio being a bit distorted but on opening the audio and viewing its spectrogram in a program such as Audacity or Sonic Visualiser, the flag format citadel{ is visible at the 1:00 mark and the closing } at 1:12. This indicates the flag is the Morse code in between these timestamps.

The spectrogram gives a clear view of the flag now which is .----   .-.. ----- ...- ...--   .---- -.. -- or 1 L0V3 1DM

The rest of the Morse code around the flag isn't really important as mentioned in the instructions.

Flag: citadel{1_L0V3_1DM}

# 10. Rotting in the deep
## Description
The floor is quiet, almost unnervingly so – like the Citadel has paused to take your measure. A soft ring of presence settles around the chamber, the kind that marks a true landing: from here, it will ask for more and, in return, grant more. Etched into its surface is a sequence of numbers, worn and faint, as if time itself is eating them away. A whisper from the echoes guides you:

The message lies beneath the surface. Push it three steps forward in the cycle of life, and only then will the words emerge from the void.

## Solve
Flag is converted to an integer and each digit is shifted by 3. Reversing the process gets the flag.
```
from Crypto.Util.number import *
ct = '6895840967002953721051398351211751734500850509315790892845302801984496338433523326225010635779036738800318'
flag = ''
for digit in ct:
    flag += str((int(digit)-3)%10)

print(long_to_bytes(int(flag)))
```
flag: citadel{br0_r34lly_unr0tt3d_m3_b4ck_t0_l1f3}

# 12. Schlagenheim
## Description
Your quest continues, but you feel something odd about this room. The only artifact on this floor is a corrupted file held in the hands of a jet-black statue, frozen in the pose of a band mid-performance. The passcode to the next floor is hidden within this piece of music, but it can’t be played, as if the wrong extension has scrambled it.

You must take the corrupted file and repair it to reveal the true code that will unlock the door forward.

## Solve
The given file has the extension set as .wav but opening it in a hex editor to view its bytes, you notice that it has magic bytes that say M1D1 which hints towards it being a MIDI file (along with hints from challenge name & description).

The magic bytes in the header that say M1D1 have to be changed to MThd as that is the file header for a MIDI file.

After making the modifications, saving it and opening it in a software that can visualize MIDI such as Audacity, the flag is shown.

Flag: citadel{8lackM1D1wa5c00l}
