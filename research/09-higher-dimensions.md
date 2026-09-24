# Higher Dimensions: Deep Research + 30-Day Plan

> What a "dimension" means in maths, in physics, and in spiritual traditions. These are **three different uses of the same word**. The maths is proven, the physics of extra dimensions is **unconfirmed theory**, and the spiritual "higher planes" are **beliefs**, not measurements. Every Python example here was run and its output checked.

---

## Part 1: Everything You Need to Know

### 1.1 What is a dimension?

A dimension is **an independent direction you can move in**, or equivalently, **how many numbers you need to specify a position**.

| Dimension | Object | Numbers needed | Example |
|---|---|---|---|
| **0D** | Point | 0 | A dot |
| **1D** | Line | 1 (x) | A position on a number line or a railway track |
| **2D** | Plane | 2 (x, y) | A map (latitude, longitude) |
| **3D** | Space | 3 (x, y, z) | Where a bird is in the air |
| **4D spacetime** | Space + time | 4 (x, y, z, t) | "Meet me at the café, 2nd floor, at 5 pm" |
| **4D space** | Hyperspace | 4 (x, y, z, w) | A fourth spatial direction at right angles to all three we know. **Not observed**; purely mathematical so far |

### 1.2 Seeing the fourth dimension (the maths)

**The pattern of cubes.** Each shape is made by dragging the previous one along a new direction:

```
point → (drag) → line → (drag) → square → (drag) → cube → (drag) → tesseract (4D hypercube)
```

The number of each part of an n-dimensional cube is `2^(n-k) × C(n, k)`:

```python
from math import comb

names = ["vertices", "edges", "squares", "cubes", "tesseracts"]
for n in range(5):
    parts = [f"{2 ** (n - k) * comb(n, k)} {names[k]}" for k in range(n + 1)]
    print(f"{n}-cube:", ", ".join(parts))
```
Output:
```
0-cube: 1 vertices
1-cube: 2 vertices, 1 edges
2-cube: 4 vertices, 4 edges, 1 squares
3-cube: 8 vertices, 12 edges, 6 squares, 1 cubes
4-cube: 16 vertices, 32 edges, 24 squares, 8 cubes, 1 tesseracts
```
A **tesseract** (the word was coined by Charles Howard Hinton in 1888) has **16 corners, 32 edges, 24 square faces and 8 cubic "cells."**

**Three ways humans "see" 4D:**
1. **Projections (shadows).** A 3D cube casts a 2D shadow; a 4D tesseract casts a 3D "shadow" (the famous cube-inside-a-cube picture), which we then draw in 2D.
2. **Slices.** In Edwin Abbott's novella ***Flatland* (1884)**, a sphere passing through a 2D world appears to its inhabitants as a dot that grows into a circle and shrinks away. A 4D object passing through our 3D world would appear as a 3D shape that appears, changes size and vanishes.
3. **Unfolding (nets).** A cube unfolds into 6 squares (a cross shape); a tesseract unfolds into 8 cubes (Salvador Dalí painted this in *Corpus Hypercubus*, 1954).

**Compute a tesseract's shadow (tested):**
```python
import itertools, math

# 16 corners of a tesseract: every combination of -1 and +1 in 4 coordinates
points = list(itertools.product([-1, 1], repeat=4))
# edges join corners that differ in exactly one coordinate
edges = [(a, b) for a, b in itertools.combinations(range(16), 2)
         if sum(x != y for x, y in zip(points[a], points[b])) == 1]
print(len(points), "vertices,", len(edges), "edges")   # 16 vertices, 32 edges

def rotate_xw(p, angle):
    x, y, z, w = p
    c, s = math.cos(angle), math.sin(angle)
    return (c * x - s * w, y, z, s * x + c * w)

def project(p, d=3.0):
    # perspective projection 4D -> 3D -> 2D, like a shadow of a shadow
    x, y, z, w = p
    k = d / (d - w)
    x3, y3, z3 = x * k, y * k, z * k
    k2 = d / (d - z3)
    return round(x3 * k2, 2), round(y3 * k2, 2)

for p in points[:4]:
    print(p, "->", project(rotate_xw(p, math.radians(30))))
```
Draw the 32 edges with matplotlib and change the angle in a loop to watch the tesseract "turn inside out." That's a rotation in a plane (x-w) that doesn't exist in 3D.

**Beautiful facts from higher-dimensional geometry:**
- 3D has **5** regular solids (the Platonic solids); 4D has **6** regular polytopes (including the 24-cell and 600-cell); every dimension from 5 up has only **3**.
- In high dimensions, almost all of a sphere's volume sits in a thin shell near its surface, and random directions are almost always nearly at right angles. This is the "**curse of dimensionality**" in data science.
- **Fractal dimensions** can be fractions: the Koch snowflake curve has dimension about **1.26**; the coastline of Britain is about 1.25.
- **Infinite-dimensional spaces** (Hilbert spaces) are the mathematical home of quantum mechanics.
- **AI uses thousands of dimensions:** words and images are turned into vectors (embeddings) with hundreds to thousands of numbers each, and "meaning" becomes direction and distance in that space.

### 1.3 Time as the fourth dimension (proven physics)

- **Einstein's special relativity (1905):** space and time are linked; moving clocks tick slower, and nothing with mass reaches light speed.
- **Hermann Minkowski (1908):** combined them into **4D spacetime**.
- **General relativity (1915):** gravity is the **curvature of spacetime** caused by mass and energy.
- **Confirmed by:**
  - GPS satellites, which must correct for relativity by about **38 microseconds per day** or positions drift by kilometres
  - The bending of starlight (1919 eclipse)
  - **Gravitational waves** (LIGO, first detected 2015, announced 2016)
  - Black hole images (Event Horizon Telescope, 2019 and 2022)

### 1.4 Extra spatial dimensions in physics (theory, not yet evidence)

| Idea | Year | Dimensions | Claim |
|---|---|---|---|
| **Kaluza-Klein theory** | Theodor Kaluza 1921, Oskar Klein 1926 | 5 | A tiny, curled-up 5th dimension could unify gravity and electromagnetism |
| **String theory** | 1970s to 80s | **10** | Particles are vibrating strings; the maths only works in 10 dimensions, 6 of them curled up (compactified, e.g. on Calabi-Yau shapes) |
| **M-theory** | Edward Witten, 1995 | **11** | Unifies five string theories |
| **Large extra dimensions (ADD)** | Arkani-Hamed, Dimopoulos, Dvali, 1998 | 4 + n | Extra dimensions as big as a millimetre could explain why gravity is so weak |
| **Warped extra dimension (Randall-Sundrum)** | 1999 | 5 | Our universe is a "brane" in a curved higher space |
| **Holographic principle / AdS-CFT** | Juan Maldacena, 1997 | Varies | A gravity theory in a volume can be exactly equivalent to a theory without gravity on its boundary: one fewer dimension |

**Why we don't see extra dimensions:** they'd be curled up far smaller than we can probe, or we're stuck on a "brane" that only gravity can leave.

**What experiments have found (status in 2026): no evidence of extra dimensions yet.**
- **Large Hadron Collider (CERN):** no Kaluza-Klein particles and no microscopic black holes. This pushes limits above the TeV scale.
- **Short-range gravity tests:** the Eöt-Wash group (University of Washington) confirmed Newton's inverse-square law down to **52 micrometres (2020)**, ruling out large extra dimensions bigger than about **40 micrometres** (in the simplest models).
- **Gravitational waves** from the 2017 neutron-star merger (GW170817) showed no sign of gravity "leaking" into extra dimensions over cosmic distances.
- String theory is mathematically rich but has **not made a confirmed, testable prediction**. Many physicists (Peter Woit, Lee Smolin, Sabine Hossenfelder) criticise it for this.

### 1.5 "Higher dimensions" in spiritual and esoteric traditions (beliefs)

These use "dimension" or "plane" to mean **levels of existence or consciousness**, not measurable directions in space. They are matters of faith, philosophy and inner experience, not physics.

| Tradition | "Higher" levels |
|---|---|
| **Hindu cosmology** | **14 lokas** (7 upper, 7 lower), see [15-upper-and-lower-realms.md](15-upper-and-lower-realms.md). **Pancha kosha** (five sheaths of a person: physical, vital, mental, wisdom, bliss) in the *Taittiriya Upanishad* |
| **Buddhism** | Three realms: desire realm, form realm, formless realm (31 planes of existence in Theravada) |
| **Theosophy** (Blavatsky, 1875 onward) | Seven planes: physical, astral, mental, buddhic, atmic, monadic, divine. Popularised the "astral plane" |
| **Kabbalah** | Ten **sefirot** and four worlds (Atziluth, Beriah, Yetzirah, Assiah) |
| **Charles Hinton, 19th century** | Believed learning to visualise 4D could expand consciousness |
| **New Age "3D → 5D ascension"** | Modern belief that humanity is shifting to a "fifth-dimensional" consciousness. **No evidence**; it borrows physics words without their meaning |

### 1.6 Claims that are unproven or misuse physics

| Claim | Reality |
|---|---|
| "String theory proves spiritual dimensions" | No. String theory's extra dimensions are tiny geometric spaces in equations, unobserved, and say nothing about consciousness |
| "Ghosts / UFOs come from other dimensions" | No evidence |
| "Quantum physics proves consciousness exists in 5D" | A misuse of quantum language; no such result exists |
| "The Mandela effect shows we've shifted between parallel dimensions" | Explained by ordinary memory errors |
| "Tesseract portals" | Fiction (e.g. films like *Interstellar*, which consulted physicist Kip Thorne on the black hole but used the tesseract artistically) |
| The "multiverse" | A real scientific **hypothesis** in several forms (inflationary, many-worlds interpretation, string landscape), but **untested and possibly untestable**. Treat it as speculation |

### 1.7 Education paths
- **Maths:** linear algebra, topology, differential geometry (B.Sc./M.Sc. Mathematics; IISc, IITs, CMI, ISI, TIFR).
- **Physics:** special and general relativity, quantum field theory, string theory (M.Sc. Physics, then a Ph.D.; ICTS Bengaluru, HRI Prayagraj, IMSc Chennai and TIFR are strong in string theory; Ashoke Sen of HRI is a world-leading string theorist).
- **Data science / AI:** high-dimensional statistics, machine learning.

---

## Part 2: 30-Day Plan

About **45 to 60 minutes a day**. You need school-level algebra. Install Python 3 and matplotlib (`pip install matplotlib`).

### Week 1: Building intuition

| Day | Learn | Do |
|---|---|---|
| 1 | What a dimension is (1.1) | List 10 things you describe with 1, 2, 3 and 4 numbers |
| 2 | Read *Flatland* Part 1 (free on Project Gutenberg) | Write how a 2D being would experience a sphere passing through |
| 3 | *Flatland* Part 2 | Watch Carl Sagan's *Cosmos* segment on Flatland and the 4th dimension (on YouTube) |
| 4 | Point → line → square → cube → tesseract (1.2) | Draw each on paper, dragging the previous shape |
| 5 | Counting parts of n-cubes | Run the n-cube code. Predict the 5-cube counts before running it with `range(6)` |
| 6 | Unfolding: cube nets and tesseract nets | Make a paper cube from a net. Look at Dalí's *Corpus Hypercubus* |
| 7 | **Review** | Explain the tesseract to someone in 3 minutes |

### Week 2: Coding and geometry

| Day | Learn | Do |
|---|---|---|
| 8 | Coordinates and vectors in n dimensions | Calculate the distance between (0,0,0,0) and (1,1,1,1). It's 2 |
| 9 | Projections | Run the tesseract code |
| 10 | Rotations in 4D (6 planes of rotation: xy, xz, xw, yz, yw, zw) | Extend the code with matplotlib to draw all 32 edges |
| 11 | Animate the rotation | Make a loop that saves frames as the angle changes |
| 12 | Regular polytopes (5 → 6 → 3) | Look up the 24-cell and 600-cell. Why does 4D have one more? |
| 13 | High-dimensional weirdness | In Python, generate random points in a 100-D cube and measure how far they are from the centre |
| 14 | **Review** | Show your animation to someone |

### Week 3: Spacetime and physics

| Day | Learn | Do |
|---|---|---|
| 15 | Special relativity basics (1.3) | Calculate time dilation for 90% of light speed: factor = 1/√(1 − 0.81) ≈ 2.29 |
| 16 | Spacetime diagrams (Minkowski) | Draw light cones for "past," "future," "elsewhere" |
| 17 | General relativity: curved spacetime | Do the rubber sheet demo with a bedsheet and balls (and learn its limits) |
| 18 | GPS and relativity | Read why GPS needs about 38 µs/day of correction |
| 19 | Kaluza-Klein and string theory (1.4) | Watch Brian Greene's *The Elegant Universe* (NOVA, free online) episode 1 |
| 20 | Experimental tests: LHC, Eöt-Wash, gravitational waves | Write why "no evidence yet" is an important result |
| 21 | **Review** | Summarise the difference between time as a dimension (proven) and extra space dimensions (unproven) |

### Week 4: Beyond physics: fractals, AI, traditions and critical thinking

| Day | Learn | Do |
|---|---|---|
| 22 | Fractal dimension | Code a Koch snowflake. Its dimension is log 4 / log 3 ≈ 1.26 |
| 23 | High-dimensional spaces in AI | Read an intro to word embeddings. Try a "king − man + woman ≈ queen" demo online |
| 24 | Holographic principle (1.4) | Read a popular article on AdS-CFT |
| 25 | Hindu and Buddhist "higher realms" (1.5) | Read about the pancha kosha in the *Taittiriya Upanishad* |
| 26 | Theosophy and Kabbalah | Compare their "planes" with the Hindu and Buddhist schemes in a table |
| 27 | Spotting misuse of physics (1.6) | Find 3 online claims about "higher dimensions" and label each: maths / physics theory / belief / pseudoscience |
| 28 | The multiverse debate | Read both sides (Max Tegmark vs Sabine Hossenfelder) |
| 29 | Consolidate | Write a 1-page essay: "What we know, what we suspect, what we believe about higher dimensions" |
| 30 | **Final project** | Share your tesseract animation + essay. Plan next steps (a linear algebra or relativity course) |

---

## Part 3: Resources

**Books**
- *Flatland: A Romance of Many Dimensions*, Edwin A. Abbott (1884, free on Project Gutenberg)
- *Hyperspace*, Michio Kaku (popular; Kaku is sometimes criticised for overselling speculation)
- *The Elegant Universe* and *The Fabric of the Cosmos*, Brian Greene
- *Warped Passages*, Lisa Randall
- *The Fourth Dimension*, Rudy Rucker
- *Not Even Wrong*, Peter Woit, and *Lost in Math*, Sabine Hossenfelder (critical views)
- *Spacetime Physics*, Taylor and Wheeler (a real textbook, accessible)

**Videos**
- 3Blue1Brown: *Thinking outside the 10-dimensional box*, and *Essence of Linear Algebra*
- Carl Sagan, *Cosmos*: Flatland segment
- NOVA *The Elegant Universe* (free on PBS)
- *Dimensions: a walk through mathematics* (free film, dimensions-math.org)

---

## Sources

- [SUPERSTRINGS! Extra Dimensions, UC Santa Barbara](https://web.physics.ucsb.edu/~strings/superstrings/extradim.htm)
- [The LHC's extra dimension, CERN Courier](https://cerncourier.com/a/the-lhcs-extra-dimension/)
- [Physics From Extra Dimensions, arXiv](https://arxiv.org/pdf/hep-ph/0011177)
- [Inverse Square Law tests, Eöt-Wash Group](https://www.npl.washington.edu/eotwash/inverse-square-law)
- [New Test of the Gravitational 1/r² Law at Separations down to 52 μm, PRL (2020)](https://www.researchgate.net/publication/339832119_New_Test_of_the_Gravitational_1r2_Law_at_Separations_down_to_52_mm)
- [Short-Range Tests of the Gravitational Inverse-Square Law, arXiv (2026)](https://arxiv.org/html/2605.18212v1)
- [Kaluza-Klein Partners, Matt Strassler](https://profmattstrassler.com/articles-and-posts/some-speculative-theoretical-ideas-for-the-lhc/extra-dimensions/how-to-look-for-signs-of-extra-dimensions/kaluza-klein-partners-why-step-2/)
- n-cube counts and tesseract projection code verified locally with Python 3
