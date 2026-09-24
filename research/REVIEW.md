# Review: Judgement, Fact-Check and Reality Check of the Guides

> **What this is:** an honest, critical review of everything in this folder.
>
> **How it was done:**
> - **Guides 01 to 05** were fact-checked line by line by **three independent reviewers** (separate AI agent sessions that did not write the guides and were told to assume errors). They used web search, local code execution, compilers and simulators.
> - Their findings were then **applied to the guides** (see the change log below).
> - **Guides 06 to 15** were written later in the same session, **after the session's web-search allowance ran out**. They were self-checked (numbers recomputed, code run, book titles audited) but **not independently fact-checked**. Each carries a "verification note."
>
> **Date of review:** 24 September 2026.
>
> **Probability-of-success figures below are judgement estimates** built on the stated assumptions and the few statistics quoted. They are not measurements, so treat them as rough odds.

---

## 1. Summary scorecard

| Guide | Issues found by independent review | Fixed | Accuracy after fixes (judgement) | Practical value | Biggest remaining risk |
|---|---|---|---|---|---|
| 01 Cooking | 20 (1 high, 5 medium, 14 low) | All high and medium; most low | High | High | You, in a hot kitchen: burns, knives, oil fires |
| 02 Boxing | 16 (0 high, 4 medium, 12 low) | All medium; most low | High | High (as a foundation) | Hand/wrist overuse; sparring too early after Day 30 |
| 03 Binary computing | 18 (0 high, 2 medium, 16 low) | All medium; most low | Very high (every code output reproduced) | High | Motivation: self-study completion rates are low |
| 04 Company in India | 34 (4 high, 12 medium, 18 low) | All high and medium; most low | Good, but the rules change monthly | High | Law and tax changes after September 2026 |
| 05 Exploration in India | 34 (1 high, 11 medium, 22 low) | All high and medium; most low | Good (85 to 90% correct before fixes) | Medium to high | Financial: most exploration finds nothing |
| README | 3 (1 medium, 2 low) | Yes (rewritten) | High | | |
| 06 to 15 (new) | Not independently reviewed | Self-checked | Probably good on stable science; **verify recent numbers** | Varies | Unverified details; see section 4 |

**Overall verdict:** the pack is a solid starting library. The independent review found **no fabricated laws or schemes** in guides 01 to 05, and all code outputs matched. It did find:
- **one dangerous piece of outdated safety advice** (oil fires), now fixed
- **one book that doesn't appear to exist**, now removed
- **several rules that changed in 2025 to 2026** that the first draft missed, now updated
- **30-day plans that were too optimistic** about how long government processes take, now re-sequenced

---

## 2. Change log: what the independent review corrected

### Cooking (01)
- **Oil fire (high severity):** removed the "damp cloth" advice, which fire services have withdrawn. It's now: turn off the heat if safe, slide on a metal lid or tray, never move the pan, and call 101/112.
- **Pressure cooker:** frothing dals (toor, moong) and soybeans must be filled to only **1/3**, not 1/2 (Hawkins guidance).
- **Rajma:** added the FDA's 30-minute boil, and that warm-but-not-boiling beans can be about **5x more toxic than raw**. Added the missing soak step before Day 14.
- **Eggs:** added a warning that pregnant people, children, older adults and the immunocompromised should eat fully set eggs.
- **Time budget:** days 21, 22, 28 and 30 need 2 to 4 hours, not 1 to 1.5.
- **Smaller fixes:**
  - the hot-weather threshold (32°C, not 35°C)
  - sulphites in the allergen list
  - the béchamel ratio
  - the LPG helpline **1906**
  - consistent storage times
  - the umami and caramelisation wording
  - the cooker-cake caution
  - the mustard-oil smoke caution
  - keema → mutton curry for braising
  - a weak source replaced

### Boxing (02)
- **Books:** *The Boxing Bible* by "Andy Dumas and Jeremy Laxton" **could not be found and was removed** (replaced with Andy Dumas's real *Successful Boxing*). Mark Hatmaker's book title was corrected.
- **Headgear:** it was one-sided and based on a gear-seller's blog. It now reflects the mixed research (it halves angular acceleration in lab tests and reduces cuts, but can't eliminate concussion risk) and says beginners should always wear headgear for sparring.
- **Partner drills:** they contradicted the "no head contact" rule. Now the partner jabs at a held pad, with gloves and mouthguards.
- **Training load:** heavy-bag work is limited to 3 to 4 days a week to protect beginners' hands.
- **Additions:** a PAR-Q health screen, heat-illness guidance, and the 2025 world champions (Jaismine Lamboria, Minakshi Hooda).
- **Smaller fixes:** the pivot direction, the boxer's fracture definition, women's pro round length, the NSNIS name, the timer setting, and no dumbbell punching.

### Binary computing (03)
- The **Arduino sketch** printed 7 bits (leading zeros dropped) while the LED showed 8. Now it prints all 8.
- The **socket example** used port 5000, which modern Macs reserve for AirPlay. Now it uses 50007 (re-tested: output unchanged).
- **Smaller fixes:**
  - Mac alternative to `od -t x1z`
  - Python's `~` behaviour
  - Python is interpreted (it isn't JIT-compiled)
  - USB keyboards send HID codes (A = 0x04 → 'a' = 0x61)
  - how the IP/TCP checksum really works
  - differential pairs in serial links
  - 800 Gb/s Ethernet
  - Unicode count (~160,000)
  - the `endbr64` note
  - an I2C scanner hint
  - Wireshark filter tips (HTTP/3 and secure DNS)
  - limits of the simple framing protocol

### Company in India (04)
- **DIR-3 KYC** moved to a **3-year cycle (by 30 June)** from 31 March 2026. The old "every year by 30 September" was wrong in three places.
- **The Startup India Seed Fund Scheme closed** to new applications on **31 May 2026**; it's no longer listed as available.
- **The 30-day plan was unrealistic:** it had the certificate of incorporation arriving 2 days after filing (it takes about 7 to 15 working days) and customers invoiced before **INC-20A** (illegal: a company can't start business until INC-20A is filed). The plan is re-sequenced.
- **Tax:**
  - MAT (cut to 14% and made final by the Finance Act 2026) means a tax holiday isn't zero tax.
  - The section 140 holiday needs a **company or LLP with turnover ≤ ₹100 crore**.
  - The approval statistic was attached to the wrong group (about 1.8% of all DPIIT startups hold the certificate; about half of applicants get it).
  - ESOP tax deferral applies only to startups holding the IMB certificate.
  - New TDS forms 138 and 140 replace 24Q and 26Q.
  - The 115BAA choice is irrevocable.
- **Other:**
  - The EPF wage ceiling rose to **₹25,000** (17 September 2026).
  - POSH Act compliance at 10+ workers was added.
  - Convertible notes are exempt from deposit rules only for DPIIT startups raising ₹25 lakh+ in one tranche.
  - State-specific GST thresholds were added (e.g. **Telangana: ₹20 lakh for goods**).
  - The DPIIT notification date was corrected (4 February 2026).
  - PAN + TAN ≈ ₹131.
  - *Traction* has 19 channels.

### Exploration in India (05)
- **The "50% reimbursement" of exploration costs is repayable** (within 10 years, once production starts). It was presented as if it were free money.
- **The offshore mineral auction was annulled** for lack of bidders (December 2025). The government has no near-term plan to revive it (April 2026).
- **Oil and gas OALP-X/XI deadlines** for deepwater bids moved to **15 November 2026**.
- The satellite-phone law is now the **Telecommunications Act, 2023** (the 1933 Act was repealed).
- **Indian** survey firms also need authorisation to research in India's EEZ or continental shelf; the draft said only foreigners did.
- **Google Earth Engine is free only for non-commercial use**; selling insights needs a paid licence.
- **The Ministry of Tourism operator recognition** needs ₹10 lakh of prior-year adventure turnover, so it isn't for year 1.
- **Drones:** the "2026 FPV/BVLOS frameworks" claim was unsupported and was replaced (a BVLOS framework is only planned; the draft Civil Drone Bill 2025 was added). Rule 44 insurance is mandatory.
- **The 30-day plan** had a paid trek and a drone flight before registration, insurance and a pilot certificate. It's re-sequenced to be legal and safe.
- **Smaller fixes:**
  - the mission funding split
  - composite licences can be auctioned from G4
  - Samudrayaan naming and timeline
  - amateur radio is non-commercial
  - Ladakh ILP abolished for Indians (2021)
  - mountaineering course ladder
  - airport drone limits
  - the drone import ban scope
  - AMASR construction ban
  - PESA in Scheduled Areas
  - AERB check for XRF devices
  - the author of *Field Geology Illustrated* is Terry S. Maley

---

## 3. Guide-by-guide judgement

### 01 Cooking

**Reality check:** 30 days will make you a **competent everyday cook**, not a chef. Professional chefs train 3 to 4 years (an IHM hotel-management degree, then years on the line).

**Pros:**
- Built on correct food-safety numbers (USDA and FSSAI)
- Mixes Indian and global technique
- Each day builds on the last
- Cheap

**Cons:**
- Heavy on North and South Indian classics; little on Northeast, coastal, or Bengali cuisine
- Assumes a gas stove, pressure cooker and mixer

**Risks:**
- Burns, knife cuts, oil fires, gas leaks
- Food poisoning (rajma, leftover rice, raw eggs)
- Allergic reactions when cooking for guests

**Probability of success** (outcome: "cook 15+ dishes confidently without a recipe by Day 30"):
- **High, roughly 60 to 75%** if you actually cook on 25+ of the 30 days, because cooking gives instant feedback and you eat the results.
- The main failure mode is skipping days. Habit research (Lally et al., 2010) found a **median of 66 days** for a behaviour to become automatic, so expect to still need willpower after Day 30.

**Predecessors:**
- India's home cooks, who pass these skills down generation to generation
- **Tarla Dalal** (India's best-selling cookbook author)
- **Sanjeev Kapoor** (*Khana Khazana*, from 1993)
- Madhur Jaffrey
- Samin Nosrat (whose "salt, fat, acid, heat" framework this guide uses)

**Education needed:** none to start. To go professional: an IHM (NCHMCT JEE entrance) or a culinary diploma, FSSAI food-safety training (FoSTaC), then kitchen experience.

### 02 Boxing

**Reality check:** 30 days gives you **correct fundamentals and fitness**. Competent sparring takes about 3 to 6 months of regular coached training. Competing takes 6 to 12+ months. Elite level takes 5 to 10 years, usually starting young.

**Pros:**
- Safety-first (no sparring, rest days, a health screen)
- Standard, correct technique
- Progressive rounds

**Cons:**
- Self-coached technique drifts without a coach's eye
- Can't teach timing and distance against a real opponent

**Risks:**
- Hand, wrist and shoulder overuse
- Heat illness
- Later, **head impacts**: repeated head blows carry long-term brain-health risks, so limit hard sparring for life

**Probability of success:**
- Outcome "finish the 30 days and do 6 x 3-minute bag rounds": **about 50 to 65%** if you follow it.
- Outcome "still training 6 months later": **lower, about 25 to 40%**. Gym retention is poor in general: an often-quoted industry figure is that around half of new gym members quit within 6 months.
- Joining a club with training partners improves both a lot.

**Predecessors:**
- **Mary Kom** (took up boxing as a teenager around 2000, inspired by Dingko Singh's 1998 Asian Games gold)
- **Vijender Singh** (Bhiwani Boxing Club, Haryana, nicknamed India's "mini-Cuba" for boxing)
- **Lovlina Borgohain** (moved from kickboxing to boxing)
- The **SAI and Army Sports Institute** systems

**Education needed:** a certified coach (NSNIS diploma or BFI-affiliated club), first aid. To coach: a SAI/NSNIS coaching diploma or B.P.Ed.

### 03 Binary computing

**Reality check:** 30 days gives you a **genuine understanding of how computers represent and send information**, plus working code. It's roughly the first third of a university "computer organisation" course. It doesn't make you an embedded engineer (that takes a degree or 1 to 2 years of projects).

**Pros:**
- Every code example verified (Python, x86, RISC-V, and an Arduino build by the reviewer)
- Uses free tools
- Hands-on
- Ends with your own protocol

**Cons:**
- Days 18, 24, 28 and 30 will overrun for true beginners
- The assembly section is short

**Risks:** almost none physically (take basic electrical care with Arduino). The real risk is **dropping out**: completion rates for self-paced online courses are famously low (studies of MIT/Harvard edX courses found only a few percent completed).

**Probability of success** (outcome: "explain and demonstrate every layer from bits to network packets"): **about 35 to 55%** for a motivated self-learner. It's higher with a study partner or by posting progress publicly.

**Predecessors:**
- **Pingala** (binary-like patterns in Sanskrit prosody)
- **Leibniz** (binary arithmetic, 1703)
- **George Boole** (1854)
- **Claude Shannon** (1937 master's thesis showing switching circuits can do Boolean logic; 1948 information theory)
- **Alan Turing**, **John von Neumann**
- In India: **TIFRAC** (India's first indigenous computer, TIFR, 1960) and **SHAKTI** (RISC-V processors, IIT Madras)

**Education needed:** none to start (school maths). Next steps: Nand2Tetris, CS50, then a B.Tech/B.Sc. in CS or electronics if you want a career in it.

### 04 Starting a company in India

**Reality check:** registering a company is the easy part (weeks, and ₹10,000 to ₹25,000). **Building a business that survives is hard:**
- In the US, government data (BLS) show about **20% of new businesses close in year 1 and about half by year 5**.
- For Indian startups, a widely cited IBM Institute for Business Value / Oxford Economics study (2017) claimed **about 90% fail within 5 years**; definitions vary.

**Pros:**
- Legally current to September 2026 after review (DIR-3 KYC, SISFS, MAT, EPF, TDS forms)
- Validation-first plan
- Realistic incorporation timeline after fixes

**Cons:**
- Rules change often, so parts will date within months
- Doesn't replace a CA/CS
- Sector licences are only listed, not explained

**Risks:**
- **Legal:** penalties for missed filings, trading before INC-20A, misclassifying workers
- **Financial:** running out of cash; personal guarantees on loans
- **Personal:** stress; relationships under strain

**Probability of success:**
- "Company incorporated and compliant by Day 30 to 45": **about 85 to 95%** (a mechanical process).
- "Paying customers by Day 30": **about 30 to 50%**, depending heavily on the idea and on doing all 20 customer interviews.
- "Business alive and profitable after 3 years": **about 20 to 40%**. Bootstrapped service businesses do better than venture-backed moonshots on survival, though worse on scale.

**Predecessors:**
- **Infosys** (1981, started with about ₹10,000 borrowed from Sudha Murty)
- **Zoho** (Sridhar Vembu, bootstrapped from 1996, now global)
- **Zerodha** (bootstrapped, 2010)
- **Flipkart** (two founders, 2007)
- **Nykaa** (Falguni Nayar, started at 50)
- Thousands of MSMEs; most of India's 6+ crore MSMEs are micro enterprises

**Education needed:** no degree is required. It helps to learn basic accounting, GST, contracts and sales. Useful: a CA or CS on retainer, and free courses (Startup India Learning Programme, YC Startup School, NPTEL entrepreneurship).

### 05 Exploration company in India

**Reality check:**
- **Minerals:** exploration is a **long, high-failure game**. A common industry rule of thumb is that only about **1 in 1,000 prospects becomes a mine**, and discovery-to-production lead times are often **10 to 20 years** (S&P Global analyses put the average at roughly 15+ years).
- **Oil and gas and deep-sea:** not realistic for one person. The offshore mineral auction itself was annulled for lack of bidders.
- **The realistic solo paths are services:** guided expeditions, drone survey, geoscience mapping and data work, and satellite analytics (with a commercial licence).

**Pros:**
- Covers every type of exploration honestly
- Recommends service-first entry
- Legally detailed, with laws current after review

**Cons:**
- Capital figures are rough estimates
- Accreditation schemes (NPEA, MoT recognition) assume a team and a track record
- 3 hours a day isn't enough in practice; training courses need full days

**Risks:**
- **Physical:** mountains, water, heat, wildlife, road travel
- **Legal:** permits, satellite phones, drones, antiquities, forest land, PESA/Gram Sabha
- **Financial:** exploration can find nothing, and the reimbursement must be repaid
- **Community:** local opposition, as with the offshore auction

**Probability of success** (by path):
- Adventure/expedition business earning revenue within 6 to 12 months: **about 30 to 50%** with certifications and a niche. This is the most realistic path.
- Drone/geospatial service business with its first paid contract within 6 months: **about 30 to 45%**.
- Geoscience consultant/subcontractor with first paid work within 6 months: **about 25 to 40%**, needing a geology degree.
- A solo founder holding an Exploration Licence that leads to a mine: **well under 1%**.

**Predecessors:**
- **Geological Survey of India** (1851, one of the world's oldest geological surveys)
- **Cairn India**'s Rajasthan discovery (Mangala, 2004), an example of a smaller explorer finding a giant field
- **Rio Tinto**'s Bunder diamond project in Madhya Pradesh (found diamonds, then exited around 2017), a cautionary example
- **Skyroot Aerospace** (Vikram-S, India's first private rocket launch, November 2022)
- **Agnikul Cosmos** (3D-printed engine launch, 2024)
- **Pixxel** (hyperspectral satellites)
- **Tenzing Norgay** (first director of field training at HMI, 1954)
- **Bachendri Pal** (first Indian woman on Everest, 1984)

**Education needed (by path):**
- **Geology:** B.Sc./M.Sc. Geology or Applied Geophysics (IIT-ISM Dhanbad and others)
- **Mountaineering:** BMC → AMC at NIM, HMI, ABVIMAS, JIM&WS or NIMAS, plus Wilderness First Responder
- **Drones:** a DGCA Remote Pilot Certificate from an RPTO
- **Space:** engineering or physics degrees (IIST Thiruvananthapuram)
- **Business basics:** see Guide 04

---

## 4. The new guides (06 to 15): honest status

| Guide | Content type | Confidence | What to double-check |
|---|---|---|---|
| 06 Human body | Established anatomy + health guidance | High for anatomy; medium for 2025 Indian obesity criteria | The BMI/waist rules with your doctor |
| 07 Life | Biology + philosophy | High for the timeline; medium for 2025/26 research news (Mars biosignature, LUCA age) | Recent research is still debated |
| 08 Martial arts | History, law, training | High (searched before the budget ran out) | Gym prices; BNS sections with a lawyer if needed |
| 09 Higher dimensions | Maths + physics + beliefs | High (code verified; physics searched) | None major |
| 10 Void | Physics + maths + philosophy | High (numbers recomputed; searched) | The Bakhshali date debate |
| 11 Planets | Planetary science | Medium to high; **written without live search** | Moon counts, exoplanet counts, mission dates |
| 12 Sound | Physics + technology + rules | Medium to high; **written without live search** | Noise-rule figures, safe-listening numbers |
| 13 Ancient technology | Archaeology + myth-busting | Medium to high; **written without live search** | Individual dates (ranges are wide) |
| 14 Ancient books | Literature + dating | Medium to high; **written without live search** | UNESCO 2025 listing, Gyan Bharatam details |
| 15 Upper and lower realms | Religion + NDE research + physical realms | Medium to high; **written without live search** | Exact counts of heavens and hells vary by text and school |

**Book lists** in 06, 08 and 11 were audited after the boxing guide's non-existent book was found. Uncertain titles were removed and replaced with ones I'm confident exist. **Recommendation:** once a fresh session with a new search allowance is available, run the same independent fact-check on guides 06 to 15.

**How the belief topics were handled** (07, 09, 10, 13, 14, 15): each guide separates **what science has evidence for**, **what traditions teach** (described respectfully, not endorsed or dismissed), and **claims that are unproven or debunked** (for example the vimana, ancient nuclear war and "432 Hz healing" claims). Science can't test non-physical realms; the guides say so plainly instead of pretending otherwise.

---

## 5. Cross-cutting risks of doing all 15 plans

- **Time:** the first five alone need 8 to 10 hours a day in parallel. All fifteen in parallel is **not realistic**. See the README for a staggered 3-month schedule.
- **Overwhelm:** doing too many plans at once is the most likely reason for failure. Pick 2 or 3 at a time.
- **Out-of-date information:** the legal and scheme details (Guides 04 and 05) will change, so re-check them every few months.
- **Safety:** cooking, boxing, martial arts and exploration all have physical risks. Follow the safety sections, get certified instruction, and never skip insurance for commercial activities.

---

## 6. Sources used by the reviewers

The three full review reports (about 460 lines, with URLs for every finding) were produced in this session. Key sources:
- **Company:** TaxGuru, Fox Mandal and SCC Times on DIR-3 KYC; the Startup India Seed Fund portal; Business Standard on MAT (Budget 2026); SCC Times on the EPF ceiling (September 2026).
- **Exploration:** the NMET reimbursement scheme PDF; Business Standard (April 2026) on the offshore auction; ETV Bharat (September 2026) on OALP deadlines; the Maritime Zones Act text (India Code); JSA on the Telecommunications Act; Google Earth Engine licensing pages.
- **Cooking, boxing, binary:** fire-service chip-pan advice; the Hawkins cooker manual; USDA FSIS; the FDA *Bad Bug Book*; McIntosh and Patton (*BJSM* 2015); Loosemore et al. (2017); Goodreads/Amazon book records; the Arduino core source; Flask docs; Apple `od` source; local runs of Python, GCC, llvm-mc and RARS.
- **Statistics quoted in this review:**
  - Lally et al. (2010), *European Journal of Social Psychology* (habit formation, median 66 days)
  - US Bureau of Labor Statistics, Business Employment Dynamics (business survival)
  - IBM Institute for Business Value and Oxford Economics (2017) (Indian startup failure, widely cited)
  - S&P Global Market Intelligence (mine lead times)
  - Reich and Ruipérez-Valiente (2019), *Science* (MOOC completion)

These were quoted from established knowledge and **not re-searched** in this session.
