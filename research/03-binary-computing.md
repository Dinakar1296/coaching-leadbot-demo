# Talking to Computers in Binary: Deep Research + 30-Day Plan

> From "what is a bit" to writing machine code, building logic circuits and sending your own binary messages between devices. The Python, x86 and RISC-V examples were run and their outputs checked; an independent review also compiled the Arduino sketch and ran the RISC-V program in RARS.
>
> **Tools you need:** a computer with **Python 3** (free). Everything else is free and runs in the browser: CircuitVerse, Wokwi, Compiler Explorer. An Arduino board (about ₹500 to ₹1,500) is optional.

---

## Part 1: Everything You Need to Know

### 1.1 The big picture: how humans "talk" to computers

A computer only understands **electricity being on or off**. We write that as **1 and 0**: **binary**. Nobody types raw binary today (early computers like the 1975 Altair 8800 were programmed by flipping front-panel switches). Instead we talk through **layers**, and each layer translates down to the next:

```
You (words, clicks, taps)
   ↓
Applications (browser, WhatsApp, games)
   ↓
High-level languages (Python, JavaScript, Java)
   ↓  compiler / interpreter
Assembly language (human-readable CPU instructions)
   ↓  assembler
Machine code (binary instructions: 10110000 00000001 ...)
   ↓
CPU + memory (billions of transistor switches)
   ↓
Logic gates (AND, OR, NOT, NAND)
   ↓
Transistors (on/off switches)
   ↓
Electricity (voltage high = 1, low = 0)
```

**Communicating with a computer in binary** means understanding **every one of these layers**, then being able to work at the lowest ones directly: reading and writing binary data, machine code, and signals on wires.

### 1.2 Number systems

| System | Base | Digits | Example (thirteen) | Used for |
|---|---|---|---|---|
| **Decimal** | 10 | 0 to 9 | 13 | Humans |
| **Binary** | 2 | 0, 1 | 1101 | Computers |
| **Hexadecimal** | 16 | 0 to 9, A to F | D | Compact binary (1 hex digit = 4 bits) |
| **Octal** | 8 | 0 to 7 | 15 | Unix file permissions (chmod 755) |

**Place values in binary** (right to left, each is double the previous):

```
Position:  7    6    5    4    3    2    1    0
Value:    128   64   32   16   8    4    2    1
Bits:      0    1    0    0    0    0    0    1    = 64 + 1 = 65
```

**Binary → decimal:** add up the place values where there is a 1.
`1101` = 8 + 4 + 0 + 1 = **13**

**Decimal → binary:** divide by 2 repeatedly, and write the remainders from bottom to top.
```
13 ÷ 2 = 6 remainder 1
 6 ÷ 2 = 3 remainder 0
 3 ÷ 2 = 1 remainder 1
 1 ÷ 2 = 0 remainder 1   → read upward: 1101
```

**Binary ↔ hex:** group bits in 4s.
```
1111 1111 = F F = 0xFF = 255
0100 0001 = 4 1 = 0x41 = 65
```

**Hex digits:** 0=0000, 1=0001, 2=0010, 3=0011, 4=0100, 5=0101, 6=0110, 7=0111, 8=1000, 9=1001, A=1010, B=1011, C=1100, D=1101, E=1110, F=1111. Memorise this table.

**Try in Python:**
```python
print(bin(13), hex(255), int('1011', 2), int('FF', 16))
# 0b1101 0xff 11 255
print(format(65, '08b'))
# 01000001
```

### 1.3 Units of data

| Unit | Size | Notes |
|---|---|---|
| **Bit** | 1 binary digit (0 or 1) | Smallest unit |
| **Nibble** | 4 bits | One hex digit |
| **Byte** | 8 bits | 256 possible values (0 to 255). One ASCII character |
| **Word** | 16, 32 or 64 bits | Depends on the CPU. Modern PCs and phones are 64-bit |
| **Kilobyte (kB) / Kibibyte (KiB)** | 1,000 bytes / 1,024 bytes | Storage makers use 1,000; operating systems often use 1,024 |
| **Megabyte / Gigabyte / Terabyte** | 10^6 / 10^9 / 10^12 bytes | Same 1,000 vs 1,024 difference |

**How many values fit in n bits?** 2^n. 8 bits = 256, 16 bits = 65,536, 32 bits ≈ 4.3 billion, 64 bits ≈ 18.4 quintillion.

### 1.4 Negative numbers, fractions and byte order

**Two's complement** (how every modern computer stores negative integers): to get **-x**, flip all the bits of x and add 1.
```
 5 = 00000101
flip → 11111010
 +1  → 11111011 = -5 (in 8 bits)
```
The top bit is the sign (1 = negative). An 8-bit signed number ranges from -128 to 127. Going past the top wraps around: this is **overflow** (127 + 1 = -128 in an 8-bit register), a classic source of bugs. (In C, signed overflow is undefined behaviour; Python integers never overflow.)

**Floating point (IEEE 754):** stores fractions as **sign + exponent + mantissa** (scientific notation in binary). 32-bit "float" has 1 sign bit, 8 exponent bits, 23 mantissa bits. Many decimals can't be stored exactly in binary, which is why:
```python
print(0.1 + 0.2)   # 0.30000000000000004
```
Never compare money with floats. Use integers (paise) or decimal types.

**Endianness (byte order):** the number 1 stored in 4 bytes:
- **Big-endian** (network order, "most significant byte first"): `00 00 00 01`
- **Little-endian** (x86 and most ARM PCs and phones): `01 00 00 00`

```python
import struct
print(struct.pack('>I', 1).hex())  # 00000001  (big-endian)
print(struct.pack('<I', 1).hex())  # 01000000  (little-endian)
```

### 1.5 Binary arithmetic and bitwise operations

**Addition** works like decimal with carries: 0+0=0, 0+1=1, 1+1=10 (write 0, carry 1), 1+1+1=11.
```
  0110  (6)
+ 0111  (7)
= 1101  (13)
```

**Bitwise operators** (the tools of low-level programming):

| Operator | Python | Rule | 1100 op 1010 |
|---|---|---|---|
| AND | `&` | 1 only if both are 1 | `1000` |
| OR | `\|` | 1 if either is 1 | `1110` |
| XOR | `^` | 1 if they differ | `0110` |
| NOT | `~` | Flip every bit (in Python, use `~x & 0xFF` for a byte; plain `~1` gives `-2`) | |
| Left shift | `<<` | Move bits left (×2 each) | `5 << 1` = 10 |
| Right shift | `>>` | Move bits right (÷2 each) | `20 >> 2` = 5 |

**Uses:** **masks** (check if bit 3 is set: `x & 0b1000`), **flags** (store 8 on/off settings in one byte), fast multiply/divide by 2, **XOR** in encryption and checksums, **graphics** and colour channels.

### 1.6 Encoding text: how letters become binary

**ASCII** (1963, 7 bits, 128 characters): English letters, digits, punctuation and control codes.

| Character | Decimal | Hex | Binary |
|---|---|---|---|
| `A` | 65 | 41 | 01000001 |
| `a` | 97 | 61 | 01100001 |
| `0` | 48 | 30 | 00110000 |
| Space | 32 | 20 | 00100000 |
| Newline `\n` | 10 | 0A | 00001010 |

Tricks: uppercase and lowercase differ by one bit (32, bit 5). Digit `'7'` is 48 + 7.

**Unicode** gives every character in every language a number (a **code point**), written U+XXXX: `A` = U+0041, `₹` = U+20B9, Devanagari `न` = U+0928, 😀 = U+1F600. Unicode 17.0 (2025) covers about 160,000 characters, including every Indian script.

**UTF-8** (the encoding used by about 98% of websites) stores code points in **1 to 4 bytes**:

| Code point range | Bytes | Bit pattern |
|---|---|---|
| U+0000 to U+007F | 1 | `0xxxxxxx` (same as ASCII) |
| U+0080 to U+07FF | 2 | `110xxxxx 10xxxxxx` |
| U+0800 to U+FFFF | 3 | `1110xxxx 10xxxxxx 10xxxxxx` |
| U+10000 to U+10FFFF | 4 | `11110xxx 10xxxxxx 10xxxxxx 10xxxxxx` |

**Real examples (checked in Python):**
```
A   U+0041  → 41           → 01000001
₹   U+20B9  → E2 82 B9     → 11100010 10000010 10111001
न   U+0928  → E0 A4 A8     → 11100000 10100100 10101000
😀  U+1F600 → F0 9F 98 80  → 11110000 10011111 10011000 10000000
```

**Write a message in binary and read it back:**
```python
msg = "Hi"
bits = ' '.join(format(b, '08b') for b in msg.encode('utf-8'))
print(bits)                                        # 01001000 01101001
print(bytes(int(x, 2) for x in bits.split()).decode('utf-8'))   # Hi
```

### 1.7 Encoding everything else

| Data | How it becomes binary |
|---|---|
| **Images** | A grid of **pixels**. Each pixel is usually 3 bytes: **Red, Green, Blue**, 0 to 255 each (24-bit colour = 16.7 million colours). Pure red = `FF 00 00`. A 1920×1080 image = about 6.2 MB uncompressed. PNG/JPEG compress it |
| **Sound** | **Sampling:** measure the air-pressure wave many times a second. CD quality = **44,100 samples per second, 16 bits per sample**, 2 channels. MP3/AAC compress it |
| **Video** | Many images per second (24 to 60 fps) + sound, heavily compressed (H.264, H.265, AV1) |
| **Instructions** | Machine code (see 1.9) |
| **Files** | Every file is just bytes. Many start with a **"magic number"** that identifies the type: PNG = `89 50 4E 47`, PDF = `25 50 44 46` ("%PDF"), ZIP/DOCX/APK = `50 4B` ("PK"), ELF Linux programs = `7F 45 4C 46` |

**Look at raw bytes:**
```bash
printf 'Hi\n' | od -A x -t x1z
# 000000 48 69 0a     >Hi.<
```
(`od -t x1z` works on Linux. On a Mac use `xxd file` or `hexdump -C file`. On Windows, use PowerShell's `Format-Hex`.)

### 1.8 Logic gates: how hardware "thinks"

**Transistors** are tiny electronic switches. A modern phone chip has **billions** of them. Combining transistors makes **logic gates**:

| Gate | Output is 1 when | Symbol in code |
|---|---|---|
| **NOT** | Input is 0 | `~A` / `!A` |
| **AND** | Both inputs are 1 | `A & B` |
| **OR** | At least one input is 1 | `A \| B` |
| **XOR** | Inputs differ | `A ^ B` |
| **NAND** | NOT(AND). **Universal:** every other gate can be built from NAND alone | `~(A & B)` |
| **NOR** | NOT(OR). Also universal | `~(A \| B)` |

**Truth table example (XOR):**
```
A B | A XOR B
0 0 |   0
0 1 |   1
1 0 |   1
1 1 |   0
```

**Building up from gates:**
1. **Half adder:** adds 2 bits. `sum = A XOR B`, `carry = A AND B`.
2. **Full adder:** adds 2 bits + a carry-in (2 half adders + OR).
3. **Ripple-carry adder:** chain 8 full adders = an 8-bit adder.
4. **Multiplexer:** selects one of many inputs (a hardware "if").
5. **ALU (Arithmetic Logic Unit):** adder + logic gates + multiplexer = does add, subtract, AND, OR, compare.
6. **Flip-flops and latches:** gates wired in a loop that **remember** 1 bit. This is how memory and registers work.
7. **Registers → RAM → CPU:** add a clock and a control unit, and you have a computer.

**Boolean algebra rules you'll use:** A AND 1 = A, A OR 0 = A, A AND 0 = 0, A OR 1 = 1, A XOR A = 0, and **De Morgan's laws:** NOT(A AND B) = NOT A OR NOT B; NOT(A OR B) = NOT A AND NOT B.

### 1.9 The CPU and machine code

**Main parts of a CPU:**
- **Registers:** tiny, super-fast storage inside the CPU (e.g. 32 general registers in RISC-V, 16 in x86-64)
- **ALU:** does the maths and logic
- **Control unit:** decodes instructions and directs everything
- **Program Counter (PC):** holds the address of the next instruction
- **Cache (L1, L2, L3):** fast memory close to the CPU
- **Clock:** ticks billions of times a second (3 GHz = 3 billion cycles/second)

**The fetch-decode-execute cycle** (runs billions of times per second):
1. **Fetch** the instruction at the address in the PC from memory.
2. **Decode** the bits to work out the operation and operands.
3. **Execute** it (the ALU calculates, or memory is read or written).
4. **Update the PC** and repeat.

**Instruction Set Architectures (ISA):** the "vocabulary" of binary instructions a CPU understands.
- **x86-64:** Intel and AMD laptops and desktops. Variable-length instructions (1 to 15 bytes)
- **ARM (AArch64):** phones, Apple M-series Macs, Raspberry Pi. Fixed 32-bit instructions
- **RISC-V:** open-source, free ISA, great for learning. India's **SHAKTI** (IIT Madras) and **VEGA** (C-DAC) processors are RISC-V

**Real machine code, decoded (RISC-V):** `addi x1, x0, 5` (put 5 into register x1)
```
Binary: 000000000101 00000 000 00001 0010011
        |  imm = 5  | rs1 |f3 | rd  | opcode (ADDI)
        |           | =x0 |   | =x1 |
Hex:    0x00500093
```

**Real machine code (x86-64), checked with `gcc` and `objdump`:**
```
b8 01 00 00 00      mov $1, %eax      ; put 1 in register eax (note little-endian 1)
c3                  ret               ; return
90                  nop               ; do nothing
```

A C function compiled to x86-64 (`gcc -O2`):
```c
int add(int a, int b) { return a + b; }
```
```
8d 04 37     lea (%rdi,%rsi,1),%eax    ; eax = edi + esi (the low 32 bits)
c3           ret
```
Four bytes of binary. That's the whole function. (Many Linux distributions add a 4-byte `endbr64` security instruction at the start by default; compile with `-fcf-protection=none` to see just these 4 bytes.)

### 1.10 Assembly language

Assembly is **machine code with human-readable names**. One assembly line ≈ one machine instruction.

**RISC-V example: add numbers 1 to 10** (run it in the RARS simulator):
```asm
        li   t0, 0          # sum = 0
        li   t1, 1          # i = 1
        li   t2, 11         # limit
loop:   add  t0, t0, t1     # sum = sum + i
        addi t1, t1, 1      # i = i + 1
        blt  t1, t2, loop   # if i < 11, go to loop
        mv   a0, t0         # move result to a0
        li   a7, 1          # system call 1 = print integer
        ecall               # prints 55
        li   a7, 10         # system call 10 = exit
        ecall
```

**From your code to binary:**
```
C / C++ / Rust source  →  compiler  →  assembly  →  assembler  →  object file (machine code)
                                                       →  linker  →  executable (ELF on Linux, PE .exe on Windows, Mach-O on Mac)

Python                 →  compiled to bytecode, which the CPython interpreter runs
JavaScript             →  JIT compiler turns hot code into machine code while running
```
Try it: **Compiler Explorer (godbolt.org)** shows the assembly for any C, C++, Rust or Go code, live.

### 1.11 The operating system and hardware communication

- The **OS kernel** (Linux, Windows, macOS, Android) controls hardware and gives programs a safe way to use it through **system calls** (read a file, send a network packet, print text).
- **Device drivers** translate between the OS and specific hardware.
- **Interrupts:** hardware signals the CPU ("a key was pressed," "a packet arrived") so the CPU doesn't have to keep checking.
- **What happens when you press "A":** the keyboard detects the switch → sends a HID usage code over USB (the A key is `0x04`) → a USB controller interrupt → the driver turns it into a key event → the OS sends it to the active app → the app stores `0x61` ('a'), or `0x41` ('A') with Shift → the font engine turns it into pixels → the GPU sends pixels to the screen.

### 1.12 Communication between devices: sending bits over wires and air

#### Serial vs parallel
- **Parallel:** many bits at once on many wires (old printers, inside chips). Fast over short distances.
- **Serial:** one bit after another (UART on one wire; USB, Ethernet and PCIe on differential wire pairs, and Gigabit Ethernet uses 4 pairs at once). Almost all modern links are serial.

#### How bits travel as signals
- **Voltage levels:** e.g. 0 V = 0, 3.3 V or 5 V = 1 (TTL/CMOS logic).
- **Line codes:** NRZ (high = 1, low = 0), **Manchester** (a transition in the middle of each bit, used in old Ethernet), block codes such as 8b/10b, 64b/66b and 128b/130b (used in USB, Ethernet and PCIe) that keep the signal balanced and the clocks in sync.
- **Baud rate:** symbols per second (9600 baud ≈ 9600 bits/sec for simple serial; with start and stop bits that's about 960 bytes/sec of data).
- **Wireless:** bits are carried by changing a radio wave's **amplitude, frequency or phase** (ASK, FSK, PSK, QAM). Wi-Fi, Bluetooth, 4G/5G.
- **Light:** fibre optics (light on = 1, off = 0, or more complex schemes); infrared TV remotes.

#### Common hardware protocols

| Protocol | Wires | Speed | Used for | Key idea |
|---|---|---|---|---|
| **UART** (serial port) | TX, RX, GND | 9,600 to 115,200+ baud | Arduino ↔ PC, GPS modules, debugging | **Start bit (0) + 8 data bits + optional parity + stop bit (1)**. Both sides agree on the baud rate. No clock wire |
| **I2C** | SDA (data), SCL (clock) | 100 kHz to 3.4 MHz | Sensors, small displays | Many devices on 2 wires, each with a 7-bit address |
| **SPI** | MOSI, MISO, SCK, CS | Up to tens of MHz | SD cards, fast displays, flash chips | Full duplex, one chip-select wire per device |
| **USB** | D+, D-, power (+ more in USB 3/4) | 1.5 Mb/s to 80 Gb/s | Everything | Packets, host-controlled, differential signalling |
| **CAN bus** | CAN-H, CAN-L | Up to 1 Mb/s (CAN FD: more) | Cars, industrial machines | Robust, message priority |
| **Ethernet** | Twisted pairs / fibre | 10 Mb/s to 800 Gb/s | Wired networks | Frames with MAC addresses + CRC |

**UART frame for the letter "A" (0x41 = 01000001)**, sent least significant bit first:
```
idle  start  b0 b1 b2 b3 b4 b5 b6 b7  stop  idle
 1     0     1  0  0  0  0  0  1  0    1     1
```

#### Error detection (because noise flips bits)
- **Parity bit:** add 1 bit so the count of 1s is even (or odd). Detects a single flipped bit.
- **Checksum:** add up the data and send the sum. IP and TCP use a 16-bit ones'-complement sum of 16-bit words. A simple sum can't detect bytes that are swapped.
- **CRC (Cyclic Redundancy Check):** polynomial maths, catches most errors (Ethernet, ZIP, PNG). `zlib.crc32(b'Hi')` = `0x4d170e0e`.
- **Error-correcting codes** (Hamming, Reed-Solomon, LDPC): can **fix** errors, not just detect them (QR codes, CDs, Wi-Fi, 5G, space probes).

### 1.13 Networking: how computers talk across the world

**The TCP/IP model (4 layers):**

| Layer | Job | Examples |
|---|---|---|
| **Application** | What the data means | HTTP/HTTPS (web), DNS (names → IPs), SMTP (email), SSH, MQTT (IoT) |
| **Transport** | Reliable delivery between programs (ports) | **TCP** (reliable, ordered: web, email), **UDP** (fast, no guarantee: video calls, games, DNS) |
| **Internet** | Routing between networks (IP addresses) | **IPv4** (32-bit), **IPv6** (128-bit), ICMP (ping) |
| **Link** | Moving frames on one local network (MAC addresses) | Ethernet, Wi-Fi |

(The 7-layer **OSI model** splits these further: Physical, Data Link, Network, Transport, Session, Presentation, Application.)

**An IP address is just 32 bits:**
```
192.168.1.1 = 11000000.10101000.00000001.00000001
```
A **subnet mask** like 255.255.255.0 (`/24`) = 24 ones then 8 zeros: the first 24 bits identify the network, the last 8 the device.

**What happens when you open a website:** DNS turns the name into an IP → **TCP 3-way handshake** (SYN → SYN-ACK → ACK) → **TLS handshake** (encryption keys) → **HTTP request** → the server replies with HTML → the browser renders it. Every step is just bytes in packets with headers.

**Send binary between two programs (tested):**

`server.py`
```python
import socket

with socket.create_server(("127.0.0.1", 50007)) as srv:
    conn, addr = srv.accept()
    with conn:
        data = conn.recv(1024)
        print("raw bits:", " ".join(format(b, "08b") for b in data))
        print("decoded :", data.decode("utf-8"))
```

`client.py`
```python
import socket

with socket.create_connection(("127.0.0.1", 50007)) as s:
    s.sendall("Hello".encode("utf-8"))
```
Run the server in one terminal, then the client in another. (Port 50007 is used because macOS reserves port 5000 for AirPlay.) The server prints:
```
raw bits: 01001000 01100101 01101100 01101100 01101111
decoded : Hello
```

### 1.14 Design your own protocol (tested)

A protocol is just an agreement about **what the bits mean**. This one uses a start byte, a length, the payload, and a checksum:

```python
START = 0x7E

def make_frame(text):
    payload = text.encode("utf-8")
    checksum = sum(payload) % 256
    return bytes([START, len(payload)]) + payload + bytes([checksum])

def read_frame(frame):
    if frame[0] != START:
        raise ValueError("no start byte")
    length = frame[1]
    payload = frame[2:2 + length]
    if sum(payload) % 256 != frame[2 + length]:
        raise ValueError("checksum failed: data corrupted")
    return payload.decode("utf-8")

f = make_frame("Hi ₹")
print(" ".join(format(b, "08b") for b in f))
# 01111110 00000110 01001000 01101001 00100000 11100010 10000010 10111001 11101110
print(read_frame(f))      # Hi ₹

broken = bytearray(f)
broken[3] ^= 0b00000100   # flip one bit to simulate noise
read_frame(bytes(broken)) # ValueError: checksum failed: data corrupted
```
**Limits of this simple design:** a byte-sum can't detect swapped bytes, a corrupted length byte causes an `IndexError`, and a `0x7E` inside the payload isn't escaped. Real protocols fix these with CRCs and byte-stuffing (Day 29).

### 1.15 Hardware project: blink binary with an Arduino

Works on a real Arduino Uno or free in the **Wokwi** browser simulator. The built-in LED on pin 13 flashes each character's 8 bits (on = 1, off = 0), and the Serial Monitor prints them. This is **our own optical protocol** (start = light on, most significant bit first), not UART.

```cpp
const int LED = 13;
const int BIT_MS = 300;

void sendByte(byte b) {
  digitalWrite(LED, HIGH);          // start signal
  delay(BIT_MS);
  digitalWrite(LED, LOW);
  delay(BIT_MS);
  for (int i = 7; i >= 0; i--) {    // most significant bit first
    digitalWrite(LED, (b >> i) & 1);
    delay(BIT_MS);
  }
  digitalWrite(LED, LOW);
  delay(BIT_MS * 4);                // gap between characters
}

void setup() {
  pinMode(LED, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  const char *msg = "HI";
  for (int i = 0; msg[i] != '\0'; i++) {
    for (int b = 7; b >= 0; b--) Serial.print((msg[i] >> b) & 1);  // all 8 bits, with leading zeros
    Serial.println();
    sendByte(msg[i]);
  }
  delay(3000);
}
```
**Challenge:** add a light sensor (LDR) on a second Arduino to **receive** the flashes and decode them back to letters. You've just built optical communication.

### 1.16 Security basics at the binary level

- **Encryption** scrambles bits with a key (AES, ChaCha20). XOR is a building block: `data XOR key XOR key = data`.
- **Hashing** (SHA-256) turns any data into a fixed 256-bit fingerprint.
- **Buffer overflows:** writing past the end of memory can overwrite other data or code, a classic attack. That's why memory-safe languages (Rust, Python, Java) and protections (ASLR, stack canaries, the `endbr64` instruction you may see at the start of compiled functions) exist.
- **Reverse engineering** tools like Ghidra (free, NSA) turn machine code back into readable form. Use them only on software you own or have permission to analyse.

### 1.17 Where this leads (careers)
Embedded systems and IoT, firmware, computer architecture and **VLSI chip design** (India is building up chip design and fabs under the **India Semiconductor Mission**), networking, cybersecurity, operating systems, compilers, robotics, and space and satellite communication.

---

## Part 2: 30-Day Plan

About **1 to 1.5 hours per day**. Keep a notebook: write every conversion by hand first, then check it in Python.

### Week 1: Number systems and data

| Day | Topic | Practice |
|---|---|---|
| 1 | Why binary; the layers (1.1). Count 0 to 31 in binary | Write 0 to 31 in binary by hand. Learn to count to 31 on one hand (each finger = 1 bit) |
| 2 | Binary ↔ decimal (1.2) | Convert 20 numbers each way by hand, then check with `bin()` and `int(x, 2)` |
| 3 | Hexadecimal, and the 16-row hex table | Memorise the table. Convert 20 numbers between binary, hex and decimal |
| 4 | Bits, bytes, units, 2^n (1.3) | Work out: how many bytes is a 1-minute CD-quality song? A 1080p image? |
| 5 | Two's complement, overflow, floats, endianness (1.4) | Write -1, -5, -128 in 8-bit binary. Run the `0.1 + 0.2` and `struct` examples |
| 6 | Binary addition + bitwise ops (1.5) | 10 binary additions by hand. Write Python to check if a number is even using `& 1` |
| 7 | **Review + mini-project** | Write a Python number converter: input a number, print binary, hex, octal and 8-bit two's complement |

### Week 2: Encoding and logic

| Day | Topic | Practice |
|---|---|---|
| 8 | ASCII (1.6) | Write your name in binary by hand. Decode `01001000 01100101 01101100 01101100 01101111` |
| 9 | Unicode and UTF-8 | Encode `₹`, a letter from your mother tongue, and an emoji by hand using the UTF-8 table, then check in Python |
| 10 | Images, sound, files, magic numbers (1.7) | Open a PNG and a PDF with `od -A x -t x1z file | head` (Mac: `xxd file | head`; Windows: Format-Hex) and find the magic numbers |
| 11 | Logic gates + truth tables (1.8) | Create a free CircuitVerse account. Build NOT, AND, OR, XOR and test every input |
| 12 | Build all gates from NAND only | In CircuitVerse, build NOT, AND and OR using only NAND gates |
| 13 | Half adder → full adder → 4-bit adder | Build them in CircuitVerse. Add 0110 + 0111 and see 1101 |
| 14 | **Review:** memory from gates | Build an SR latch and a D flip-flop in CircuitVerse. Store 1 bit |

### Week 3: The CPU, machine code, assembly

| Day | Topic | Practice |
|---|---|---|
| 15 | CPU parts, fetch-decode-execute (1.9) | Draw the CPU diagram from memory. Watch a visual CPU simulation video |
| 16 | ISAs, RISC-V instruction encoding | Decode `0x00500093` by hand into fields (imm, rs1, funct3, rd, opcode). Encode `addi x2, x0, 10` |
| 17 | Assembly basics in **RARS** (Java) or an online RISC-V simulator | Run the "sum 1 to 10" program (1.10). Change it to sum 1 to 100 |
| 18 | Loops, branches, memory in assembly | Write assembly that finds the largest of 5 numbers stored in memory |
| 19 | Compilers: C → assembly → binary | Use **godbolt.org**: compile `add`, a loop and an `if` in C at -O0 and -O2 and compare |
| 20 | Executables, the OS, system calls, interrupts (1.11) | On Linux/WSL: compile a C file and run `objdump -d` on it. Find `ret` (`c3`) |
| 21 | **Review + mini-project** | Start **Nand2Tetris** Project 1 (build gates in its HDL). Continue it after the 30 days |

### Week 4: Communication between devices

| Day | Topic | Practice |
|---|---|---|
| 22 | Serial vs parallel, signals, line codes (1.12) | Draw the UART frame for "H" and "i" by hand (start, 8 bits LSB first, stop) |
| 23 | UART + Arduino in **Wokwi** (1.15) | Run the binary-blink sketch. Watch the LED and the Serial Monitor |
| 24 | I2C and SPI | In Wokwi, connect an I2C LCD or sensor to an Arduino and run the standard "I2C scanner" sketch (from the Arduino Wire library examples) to read its address |
| 25 | Error detection: parity, checksum, CRC | Write Python that adds an even-parity bit to each byte. Flip a bit and detect it |
| 26 | Networking: TCP/IP, IPs in binary, subnets (1.13) | Convert your IP and subnet mask to binary. Run `ping` and `traceroute` (`tracert` on Windows) |
| 27 | Sockets: send binary between programs | Run `server.py` and `client.py`. Modify them to send a number as 4 bytes with `struct` |
| 28 | Watch packets live | Install **Wireshark**, capture while running `curl http://example.com`, and filter `dns || tcp.flags.syn==1` to find the DNS query and the TCP handshake (browsers often hide these with HTTP/3 and secure DNS) |
| 29 | Your own protocol (1.14) | Extend the frame protocol: add a message type byte and CRC32 instead of the sum |
| 30 | **Final project** | Build a chat between two programs (or two Arduinos) using **your own binary protocol**, with framing and error detection. Explain every bit of one message on paper |

### Skill checklist
- [ ] Convert between binary, decimal and hex quickly in my head for 0 to 255
- [ ] Write any text as UTF-8 bytes and decode binary back to text
- [ ] Explain two's complement and why 0.1 + 0.2 ≠ 0.3
- [ ] Build an adder and a 1-bit memory from gates
- [ ] Decode a RISC-V instruction by hand
- [ ] Write and run a simple assembly program
- [ ] Explain the fetch-decode-execute cycle
- [ ] Draw a UART frame and explain I2C vs SPI
- [ ] Explain how a web page request travels (DNS, TCP, TLS, HTTP)
- [ ] Send binary data between two programs using my own protocol

---

## Part 3: Resources

**Courses (free)**
- **Nand2Tetris** (nand2tetris.org): build a computer from NAND gates up to Tetris. The best course on this topic
- **CS50** (Harvard, free on edX / cs50.harvard.edu): computer science foundations
- **NPTEL:** Digital Circuits, Computer Organization and Architecture, Computer Networks (IIT faculty, free)
- **CircuitVerse Interactive Book** (learn.circuitverse.org): digital logic from scratch

**Books**
- *Code: The Hidden Language of Computer Hardware and Software*, Charles Petzold (the perfect beginner book for exactly this topic)
- *The Elements of Computing Systems*, Nisan and Schocken (the Nand2Tetris book)
- *Digital Design and Computer Architecture: RISC-V Edition*, Harris and Harris
- *Computer Networking: A Top-Down Approach*, Kurose and Ross
- *But How Do It Know?*, J. Clark Scott (simple explanation of how a CPU works)

**Free tools**
- CircuitVerse (circuitverse.org): logic simulator, built by students in India
- Wokwi (wokwi.com): Arduino and ESP32 simulator, no account needed
- Compiler Explorer (godbolt.org): see the assembly for any code
- RARS: RISC-V assembler and simulator
- Wireshark (wireshark.org): see network packets
- Ghidra: reverse engineering (legal, ethical use only)
- Python 3 (python.org)

**YouTube**
- Ben Eater (builds an 8-bit computer on breadboards: the best visual explanation)
- Computerphile
- Crash Course Computer Science
- Sebastian Lague ("Exploring How Computers Work")
- Neso Academy (digital electronics, popular in India)

---

## Sources

- [RFC 3629: UTF-8, IETF](https://datatracker.ietf.org/doc/html/rfc3629)
- [RFC 20: ASCII format for Network Interchange, IETF](https://datatracker.ietf.org/doc/html/rfc20)
- [RFC 791: Internet Protocol (IPv4), IETF](https://datatracker.ietf.org/doc/html/rfc791)
- [RFC 9293: Transmission Control Protocol, IETF](https://datatracker.ietf.org/doc/html/rfc9293)
- [The RISC-V Instruction Set Manual, RISC-V International](https://riscv.org/technical/specifications/)
- [IEEE 754 floating point, Wikipedia](https://en.wikipedia.org/wiki/IEEE_754)
- [Two's complement, Wikipedia](https://en.wikipedia.org/wiki/Two%27s_complement)
- [Universal asynchronous receiver-transmitter (UART), Wikipedia](https://en.wikipedia.org/wiki/Universal_asynchronous_receiver-transmitter)
- [Nand2Tetris](https://www.nand2tetris.org/)
- [CircuitVerse](https://circuitverse.org/) and [CircuitVerse Interactive Book](https://learn.circuitverse.org/)
- [Wokwi Docs](https://docs.wokwi.com/)
- [RARS: RISC-V Assembler and Runtime Simulator, GitHub](https://github.com/TheThirdOne/rars)
- [Compiler Explorer](https://godbolt.org/)
- Machine code, UTF-8, framing and socket examples were verified locally with Python 3, GCC and objdump.
