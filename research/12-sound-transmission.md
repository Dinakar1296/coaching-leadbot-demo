# Sound Transmission: Deep Research + 30-Day Plan

> What sound is, how it travels through air, water, solids and wires, how the ear hears it, how technology captures and transmits it, how buildings shape it, and what spiritual traditions say about sound. Physics, traditional beliefs and unproven "sound healing" claims are kept separate. The Python example was run and checked.
>
> **Verification note:** this session's web-search allowance ran out before this guide was written. The physics here is long-established textbook material. Numbers such as noise limits and health thresholds come from well-known official rules (CPCB, WHO, NIOSH) and were **not re-checked live**. Confirm them before relying on them legally.

---

## Part 1: Everything You Need to Know

### 1.1 What sound is

**Sound is a mechanical wave: a travelling pattern of pressure changes (compressions and rarefactions) in a medium.** Molecules don't travel with the sound; they vibrate back and forth and pass the energy on, like a Mexican wave in a stadium.

- In air and liquids, sound is a **longitudinal wave** (vibration along the direction of travel).
- Solids can also carry **transverse (shear) waves**, like earthquake S-waves.
- **Sound needs a medium.** It cannot travel through a vacuum; Robert Boyle showed in the 1660s that a bell in a jar goes silent as the air is pumped out. **Space is silent**. (NASA's "sounds of space" are *sonifications*: other data, such as radio or plasma waves, converted into audio.)

### 1.2 The key properties

| Property | Meaning | Human-scale values |
|---|---|---|
| **Frequency (f)** | Vibrations per second, in hertz (Hz). Heard as **pitch** | Human hearing ~**20 Hz to 20,000 Hz** (the top end drops with age, often to ~12 to 15 kHz in adults) |
| **Wavelength (λ)** | Distance between compressions | λ = v / f. A 440 Hz note in air: 343 / 440 ≈ **0.78 m** |
| **Amplitude** | Size of the pressure change. Heard as **loudness** | Measured in decibels |
| **Speed (v)** | How fast the wave travels | Depends on the medium (see 1.3) |
| **Timbre** | The mix of overtones (harmonics) | Why a flute and a violin playing the same note sound different |

**Decibels (dB)** are a **logarithmic** scale: +10 dB = **10 times** the intensity (and roughly "twice as loud" to the ear); +20 dB = 100 times; +3 dB = double the energy.

| Sound | Approx. level |
|---|---|
| Threshold of hearing | 0 dB |
| Whisper | 20 to 30 dB |
| Normal conversation | ~60 dB |
| Busy traffic | ~80 to 85 dB |
| Motorbike, loud DJ event | ~95 to 110 dB |
| Firecracker close up, rock concert front row | ~120 to 140 dB (pain and risk of instant damage) |

**Hearing safety:**
- Occupational guidance (e.g. the US NIOSH recommendation) is **85 dBA for up to 8 hours**. Each +3 dB **halves** the safe time (88 dB = 4 h, 91 dB = 2 h, 100 dB = 15 minutes).
- WHO's safe-listening guidance for personal audio is about **80 dB for up to 40 hours a week** for adults.
- **Noise-induced hearing loss is permanent.** Use the "60/60" rule for earphones: at most 60% volume for 60 minutes at a time.

**Infrasound and ultrasound:**
- **Infrasound** (below 20 Hz) comes from elephants, whales, earthquakes, volcanoes and wind turbines. It can travel very far.
- **Ultrasound** (above 20 kHz) is used by bats and dolphins (echolocation), **medical ultrasound imaging** (typically 2 to 15 MHz), cleaning baths and industrial flaw detection.

### 1.3 How fast sound travels

| Medium | Speed (approx.) |
|---|---|
| Air at 0°C | 331 m/s |
| **Air at 20°C** | **343 m/s** (~1,235 km/h). Rule of thumb: v ≈ 331 + 0.6 × T(°C) |
| Mars atmosphere (near the surface) | ~240 m/s; Perseverance's microphones (2021 onward) found that high-pitched sounds there travel slightly faster than low-pitched ones |
| Water | ~1,480 m/s (about 4.3 times faster than air) |
| Wood | ~3,000 to 4,000 m/s (along the grain) |
| Steel | ~5,900 m/s |
| Diamond | ~12,000 m/s |

Sound travels faster in stiffer materials. **Thunder rule:** count the seconds between the lightning and the thunder and divide by 3 for the distance in km.

### 1.4 How sound behaves

| Behaviour | What happens | Everyday example |
|---|---|---|
| **Reflection** | Bounces off surfaces | **Echo**: needs a reflecting surface at least ~17 m away for a distinct echo (a 0.1-second delay); sonar |
| **Absorption** | Soft, porous materials soak up energy | Curtains, carpets and acoustic foam quieten a room |
| **Refraction** | Bends when speed changes (e.g. with temperature) | Sound carries farther on cool nights when warm air sits above cool air |
| **Diffraction** | Bends around obstacles | You hear people around a corner (long wavelengths bend more, so you hear the bass of distant music) |
| **Interference** | Waves add or cancel | **Noise-cancelling headphones** play an "anti-noise" wave that cancels incoming sound |
| **Resonance** | An object vibrates strongly at its natural frequency | A singer shattering a glass; guitar bodies; the Tacoma Narrows bridge (1940) was actually wind-driven aeroelastic flutter, a related phenomenon |
| **Doppler effect** | Pitch rises as a source approaches and falls as it leaves | Ambulance sirens; used in radar and medical blood-flow ultrasound |
| **Sonic boom** | A source moving faster than sound (Mach 1) creates a shock wave | Fighter jets, a bullwhip's crack |

### 1.5 How we hear

1. **Outer ear** (pinna, ear canal) funnels sound to the **eardrum**.
2. **Middle ear**: three tiny bones, the **malleus, incus and stapes** (the stapes is the smallest bone in the body), amplify the vibration about 20 times and pass it to the oval window. The **Eustachian tube** balances pressure (it's why ears "pop" in planes).
3. **Inner ear**: the snail-shaped **cochlea** is filled with fluid. The **basilar membrane** vibrates at different places for different pitches (high pitch near the base, low near the tip). About **15,000 to 16,000 hair cells** turn movement into nerve signals. **Hair cells don't regrow** in humans, which is why hearing loss is permanent.
4. **Auditory nerve → brainstem → auditory cortex:** the brain works out pitch, loudness and direction (from the tiny time and loudness differences between the two ears).

**Voice:** air from the lungs vibrates the **vocal folds** in the larynx (typically ~85 to 180 Hz for adult men and ~165 to 255 Hz for women). The throat, mouth and nose shape the sound into vowels (**formants**).

### 1.6 Sound through wires and air: transmission technology

| Year | Invention | How it works |
|---|---|---|
| Ancient | Speaking tubes, drums, conch shells, bells | Direct acoustic signalling over distance |
| 1876 | **Telephone** (Alexander Graham Bell; Elisha Gray filed the same day) | A microphone turns sound into a varying electric current; a receiver turns it back |
| 1877 | **Phonograph** (Thomas Edison) | Sound vibrations cut into a groove; played back by a needle |
| 1895 | **Jagadish Chandra Bose** demonstrates millimetre-wave (microwave) radio signals in Kolkata | Pioneering radio/microwave research; his mercury coherer design fed into early radio receivers |
| 1895 to 1901 | **Radio** (Guglielmo Marconi; transatlantic signal in 1901) | Sound modulates a radio wave: **AM** changes its strength, **FM** changes its frequency |
| 1920s to 30s | Sound films, loudspeakers | Moving-coil speakers push air with a cone |
| 1948 | Claude Shannon's information theory | The maths of sending signals through noisy channels |
| 1980s | Digital audio (CD, 1982) | Sound is **sampled** and stored as numbers |
| 1990s to now | MP3, mobile networks, VoIP (WhatsApp calls), Bluetooth audio, streaming | Compressed digital audio sent in packets |

**Analogue vs digital:**
- A **microphone** turns pressure changes into a voltage. Types:
  - **Dynamic** (a coil in a magnet)
  - **Condenser** (a charged plate)
  - **MEMS** (tiny silicon ones in every phone)
- **Digitising** (see [03-binary-computing.md](03-binary-computing.md)):
  - **Sampling:** measure the voltage many times per second. The **Nyquist theorem** says you must sample at more than **twice the highest frequency**, so **44,100 samples/second** captures up to ~22 kHz.
  - **Quantisation:** store each sample as a number (16-bit = 65,536 levels).
- **Compression:** **lossless** (FLAC) keeps everything. **Lossy** (MP3, AAC, Opus) removes sounds the ear is less likely to notice (psychoacoustic masking), cutting file size about 10 times.
- **Wireless audio:** Bluetooth codecs (SBC, AAC, aptX, LDAC, and the newer LC3 for LE Audio).
- **A loudspeaker** reverses the microphone: current moves a coil, the coil moves a cone, and the cone pushes air.

**Other ways to transmit sound:**
- **Bone conduction:** vibrations through the skull directly to the cochlea (used in some headphones and hearing aids).
- **Underwater acoustics and SONAR:** sound travels far in water. The **SOFAR channel** (a layer about 1 km deep) lets whale calls and low-frequency sounds cross whole oceans. Navies use sonar; the Indian Navy's submarines depend on it.
- **Seismic waves:** "sound" through rock (see [11-planets-structure.md](11-planets-structure.md)).
- **Light to sound:** laser microphones read window vibrations. The **photoacoustic effect** (Bell's 1880 "photophone" sent sound on a beam of light).
- **Cochlear implants** turn sound into electrical signals that stimulate the auditory nerve directly, restoring hearing for many deaf people.
- **Acoustic levitation:** standing ultrasound waves can hold tiny beads or droplets in mid-air (real lab technology).

### 1.7 Sound in buildings (architectural acoustics)

- **Reverberation time (RT60):** the time for sound to fade by 60 dB. **Sabine's formula:** RT60 ≈ 0.161 × V / A (V = room volume in m³, A = total absorption).
  - A 10 × 8 × 3 m classroom (240 m³) with 40 m² of absorption ≈ **0.97 seconds**.
  - Good targets: ~0.4 to 0.6 s for classrooms and offices; ~1.5 to 2.2 s for concert halls.
- **Designing for sound:** absorbers (panels, curtains), diffusers (uneven surfaces), room shape (avoid parallel walls and domes that focus sound), and isolation (double walls, air gaps, sealed doors).
- **Famous Indian acoustic heritage:**
  - **Gol Gumbaz** (Vijayapura/Bijapur, Karnataka, 1656): its huge dome has a **whispering gallery** where a whisper travels around the wall and is heard clearly on the other side.
  - **Vittala Temple, Hampi** (16th century): the **"musical pillars"** produce musical tones when tapped. They have been studied acoustically.
  - **Golconda Fort** (Hyderabad): a clap at the entrance gate is famously said to be audible at the hilltop pavilion, a well-known acoustic signalling design.
- **Elsewhere:** the Greek theatre at **Epidaurus** (4th century BCE) carries voices to 14,000 seats; St Paul's Cathedral whispering gallery (London).

### 1.8 Music and the physics of sound

- **An octave** doubles the frequency (A4 = 440 Hz, A5 = 880 Hz).
- **Harmonics:** a string vibrates at a fundamental frequency plus multiples (2f, 3f, ...), creating timbre.
- **Western 12-tone equal temperament:** each semitone is a factor of 2^(1/12) ≈ 1.0595.
- **Indian classical music:** seven **swaras** (Sa Re Ga Ma Pa Dha Ni), and the theory of **22 shrutis** (microtonal intervals) described in the *Natyashastra*. The **tanpura** creates a rich drone full of overtones.
- **C.V. Raman** (Nobel Prize in Physics 1930 for the Raman effect in light) also researched Indian instruments. He showed the **mridangam and tabla** produce unusually **harmonic overtones**, which is rare for drums, because of the loaded black patch (*syahi*) on the drumhead.

### 1.9 Sound in spiritual traditions (beliefs)

| Tradition | Idea |
|---|---|
| **Hindu philosophy** | **Nada Brahma** ("the universe is sound"). **Om (Aum)** as the primordial sound (*Mandukya Upanishad*). **Shabda** (word/sound) is a valid source of knowledge in several darshanas. **Sphota** theory (Bhartrhari, ~5th century): meaning bursts forth as a whole from sound |
| **Mantra practice** | Repetition of sacred sounds for concentration and devotion. **Vedic chanting** (with its precise pitch-accent system) was recognised by UNESCO in 2003 (inscribed 2008) as Intangible Cultural Heritage of Humanity |
| **Sikhism** | **Shabad kirtan** (sung hymns of the Guru Granth Sahib); **Naad** |
| **Buddhism** | Chanting and bells; Tibetan singing bowls |
| **Pythagoras** | "Music of the spheres": planetary orbits in harmonic ratios (a philosophical idea, not physical sound) |
| **Sufism** | **Sama** (listening to music as spiritual practice) |

**What research supports:** music and chanting can lower stress, heart rate and blood pressure, and improve mood. Group singing improves social bonding. Music therapy helps in some conditions (e.g. dementia, stroke rehabilitation, pain).

### 1.10 Myths and unproven claims

| Claim | Reality |
|---|---|
| **"432 Hz tuning is naturally healing / 'in tune with the universe'"** | No scientific evidence. Tuning standards are conventions (A = 440 Hz was standardised internationally in the 20th century) |
| **"Solfeggio frequencies (528 Hz, etc.) repair DNA"** | No evidence |
| **"NASA recorded 'Om' from the Sun"** | A viral hoax. NASA/ESA have made sonifications of solar oscillation data, but they are converted data, not a chant |
| **"Binaural beats cure anxiety, ADHD or boost IQ"** | Small and inconsistent effects in studies; no cures |
| **"Sound can levitate stones like ancient builders did"** | Acoustic levitation only moves tiny, light objects in labs |
| **"You can hear explosions in space"** | Films only. Space is silent |
| **"Brown note" (infrasound makes people lose bowel control)** | Not supported (tested, e.g. by *MythBusters*) |

### 1.11 Noise pollution rules in India

The **Noise Pollution (Regulation and Control) Rules, 2000** (under the Environment Protection Act) set ambient limits in dB(A), day (6 am to 10 pm) / night:

| Zone | Day | Night |
|---|---|---|
| Industrial | 75 | 70 |
| Commercial | 65 | 55 |
| Residential | 55 | 45 |
| **Silence zone** (within 100 m of hospitals, schools and courts) | 50 | 40 |

Loudspeakers and public address systems generally need permission and are **not allowed between 10 pm and 6 am** (except in closed spaces, and limited exemptions for festivals). Complaints go to the local police or the State Pollution Control Board.

### 1.12 Education and careers
- **Acoustics / audio engineering:** physics, electronics or mechanical engineering, then specialisation (IITs; the CSIR-National Physical Laboratory in Delhi keeps India's acoustic standards).
- **Audiology and speech-language pathology:** BASLP degree, e.g. AIISH Mysuru (All India Institute of Speech and Hearing).
- **Sound engineering and music production:** FTII Pune, SRFTI Kolkata, private institutes.
- **Sonar and underwater acoustics:** DRDO's NPOL Kochi (Naval Physical and Oceanographic Laboratory).

---

## Part 2: 30-Day Plan

About **45 minutes a day**. Install the free **phyphox** app (by RWTH Aachen University), which turns your phone into a sound lab (frequency, amplitude, spectrum, Doppler, speed of sound).

### Week 1: What sound is

| Day | Learn | Do |
|---|---|---|
| 1 | Sound as a pressure wave (1.1) | Stretch a balloon over a bowl, sprinkle salt, and make a loud sound nearby: watch the salt jump |
| 2 | Longitudinal waves | Make compressions with a slinky |
| 3 | Frequency and pitch (1.2) | Use phyphox "Audio Spectrum." Hum low and high and read the frequencies |
| 4 | Your hearing range | Play an online hearing test sweep (low volume!). Note your highest audible frequency |
| 5 | Decibels | Use phyphox or a sound-meter app to measure 10 places (room, road, kitchen, temple, market). Make a table |
| 6 | Hearing safety | Check your earphone habits. Apply the 60/60 rule |
| 7 | **Review** | Explain why there's no sound in space |

### Week 2: Speed and behaviour

| Day | Learn | Do |
|---|---|---|
| 8 | Speed of sound (1.3) | **Echo experiment:** stand ~50 m from a big wall, clap, and time echoes with a friend or with phyphox "Acoustic Stopwatch." Speed = 2 × distance / time |
| 9 | Sound in solids | Put your ear on a table and tap the far end. Compare with listening through air |
| 10 | Reflection and absorption (1.4) | Clap in a bathroom, a bedroom and outdoors. Notice the difference |
| 11 | Interference | Two phones playing the same tone: walk around and find loud and quiet spots |
| 12 | Resonance | Run a wet finger around a wine glass rim. Change the water level and the pitch changes |
| 13 | Doppler effect | Record a passing vehicle's horn. See the frequency drop in phyphox |
| 14 | **Review** | Thunder rule: next storm, estimate the lightning distance |

### Week 3: The ear, voice and technology

| Day | Learn | Do |
|---|---|---|
| 15 | How the ear works (1.5) | Draw and label the ear |
| 16 | Voice and formants | Record yourself saying "ee," "ah," "oo" and compare the spectra |
| 17 | Tin-can telephone | Build one with 10+ m of string (keep it taut). Try cotton vs nylon string |
| 18 | Telephone and radio history (1.6) | Read about J.C. Bose's 1895 demonstration |
| 19 | Microphones and speakers | Take apart an old earphone or speaker (safely). Find the magnet and coil |
| 20 | Digital audio: sampling, Nyquist | Run the Python tone generator below. Change 440 to 880 and hear the octave |
| 21 | **Review** | Compress a WAV file to MP3 at 64 kbps and 320 kbps and compare the quality |

**Python: make a sound from numbers (tested)**
```python
import math, struct, wave

RATE = 44100          # samples per second (CD quality)
FREQ = 440.0          # A4, the standard tuning note
SECONDS = 2

with wave.open("tone_440.wav", "wb") as w:
    w.setnchannels(1)
    w.setsampwidth(2)     # 16-bit samples
    w.setframerate(RATE)
    for i in range(RATE * SECONDS):
        sample = int(32767 * 0.5 * math.sin(2 * math.pi * FREQ * i / RATE))
        w.writeframes(struct.pack("<h", sample))

print("samples written:", RATE * SECONDS)          # 88200
print("bytes of audio:", RATE * SECONDS * 2)       # 176400
print("wavelength in air at 20°C:", round(343 / FREQ, 3), "m")   # 0.78 m
```

### Week 4: Buildings, music, traditions, critical thinking

| Day | Learn | Do |
|---|---|---|
| 22 | Room acoustics, Sabine's formula (1.7) | Measure your room and estimate its RT60 |
| 23 | Indian acoustic heritage | Read about Gol Gumbaz and the Hampi musical pillars. Visit one if you can |
| 24 | Music physics (1.8) | Measure a guitar or veena string's frequency. Halve its length (press at the 12th fret) and check the octave |
| 25 | C.V. Raman and the tabla/mridangam | Read about his work on harmonic drums |
| 26 | Nada Brahma, Om, mantra (1.9) | 10 minutes of Om chanting. Note your breathing and heart rate before and after |
| 27 | Sonar and underwater sound | Put your head underwater in a bathtub or pool and knock two stones together |
| 28 | Myths (1.10) | Check 3 "sound healing" claims online. Label each as evidence / belief / unproven |
| 29 | Noise rules (1.11) | Measure noise near a hospital or school and compare with the silence-zone limit |
| 30 | **Final project** | A short report or video: "How sound travels from my voice to a friend's ear on a WhatsApp call," covering every step (air, microphone, digitisation, packets, radio, speaker, ear) |

---

## Part 3: Resources

**Books**
- *The Physics of Sound*, Richard Berg and David Stork
- *This Is Your Brain on Music*, Daniel Levitin
- *The Science of Sound*, Thomas Rossing
- *Master Handbook of Acoustics*, F. Alton Everest (room acoustics)
- *Sound: A Very Short Introduction*, Mike Goldsmith
- *Nada Brahma: The World Is Sound*, Joachim-Ernst Berendt

**Tools and channels**
- phyphox app (free); Audacity (free audio editor with spectrum analysis)
- YouTube: Physics Girl (sound episodes), Veritasium, Minute Physics, Smarter Every Day (slow-motion sound)
- NASA Perseverance Mars audio recordings (mars.nasa.gov)

---

## Further reading (reference sources; not re-verified live in this session)

- Kinsler, Frey et al., *Fundamentals of Acoustics* (textbook)
- CPCB / MoEFCC: The Noise Pollution (Regulation and Control) Rules, 2000, cpcb.nic.in
- WHO: *Safe listening* guidance and the Make Listening Safe initiative, who.int
- NIOSH (1998): Criteria for a Recommended Standard: Occupational Noise Exposure
- Maurice, S. et al. (2022), "In situ recording of Mars soundscape," *Nature* 605, 653 to 658
- Raman, C.V. (1934 to 35), papers on the musical drums of India, *Proceedings of the Indian Academy of Sciences*
- UNESCO: Tradition of Vedic Chanting (Intangible Cultural Heritage list)
- Python tone example verified locally with Python 3
