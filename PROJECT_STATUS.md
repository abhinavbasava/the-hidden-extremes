# The Hidden Extremes | PROJECT_STATUS

**Snapshot:** November 25, 2026 (Eastern Time)  
**Team:** Abhinav Basava and Pratyush  
**Chapter:** Panther Creek High School, NC TSA  
**Event:** 2026–27 High School Data Science and Analytics  
**Goal:** Develop a first-place-caliber national entry; qualify at states. No placement or score is guaranteed.  
**Current phase:** Engineering pilot and pre-confirmatory protocol validation.  
**Working code:** `smoke_project_v6.zip` plus the separately audited v6.1 bootstrap patch. Neither is a frozen confirmatory release.

> Read this file first when starting a new AI session. The latest approved protocol and verified repository files supersede old chat suggestions. Distinguish confirmed facts, proposed decisions and completed findings. Update this file after each meaningful change, using a dated entry and a pull request. Do not assume that either partner's AI can access the other's private chats.

## 1. Project definition

**Title:** The Hidden Extremes: Evaluating the Reliability of AI-Generated Environmental Data During Wildfire-Smoke Events.

**Question:** Can a general-purpose generative AI reconstruct withheld daily regulatory PM2.5 observations during wildfire-smoke events without losing important pollution extremes, and how does it compare with transparent conventional estimation methods?

**Contribution:** A controlled zero-shot reconstruction experiment, paired evaluation against EPA measurements, information-matched comparisons, and an extreme-event reliability assessment. AirGPT and related specialized LLM air-quality methods already exist. Do not claim a world first or that AI underestimates pollution before observing results. The outcome is total measured PM2.5 during smoke-supported periods, not isolated wildfire-derived PM2.5 or individual exposure.

**Theme:** One AI-generated climate/environmental sustainability dataset, at least 500 rows, with tool, model and prompts documented. Written coordinator confirmation that real reference data may be used alongside it is still pending. Keep generated outputs and measured reference data clearly distinguished. Aim for at least 500 distinct target records if feasible, not merely repeated outputs to meet the minimum; confirm the interpretation with TSA.

**Threshold:** USG+ = daily PM2.5 at least 35.5 µg/m³ (Unhealthy for Sensitive Groups or worse). Not the formal AQI Hazardous category. Use appropriate EPA concentration truncation for classification and document the rule.

## 2. Experiment and analysis plan (proposed until freeze)

| Method | Inputs |
| --- | --- |
| Arm A | Location/date only |
| Arm N | Identified location/date and neighboring values/distances |
| Arm N masked | Neighbor values/distances only; strictly information-matched to IDW |
| Arm B | Identifiers, neighbors, weather, smoke and directions |
| Arm B masked | Anonymous neighbors and environmental context |
| IDW | Distance-weighted arithmetic using the same eligible neighbor values/distances |
| Contextual regression | Pre-2021 training, neighbors and environmental features; similar rather than necessarily identical inputs to Arm B |

- Primary practical comparison: Arm B minus IDW miss-rate difference on smoke-supported USG+ site-days in independently adjudicated Western episodes; equal episode weighting. Proposed directional hypothesis: AI misses more; report a two-sided 95% interval regardless of direction.
- Key secondary comparisons: masked N vs IDW; B vs contextual regression; environment and identifier effects plus interaction `(B − N) − (B_masked − N_masked)`. Identifier effects do not prove memorization. Predefine multiplicity treatment and distinguish exploratory analysis.
- Secondary reliability dimensions: valid-output coverage, numerical error, extreme-value fidelity/compression, miss/false-alarm rates, run-to-run variability; predefined failure diagnostics by severity, monitor distance, neighbor disagreement and region.
- Use 2020 exclusively for engineering development; 2021–2025 confirmatory period. Pre-2021 conventional training only; freeze sampling, comparator, model, prompts, thresholds and evaluation key before confirmatory generation. Repeats characterize model variability, not independent samples. Target three repeats, median aggregation, minimum two valid responses; finalize missing-output estimands and sensitivity checks.
- Hold out every instrument at the target site; use eligible neighbors 10–150 km away with exact site IDs. No tools/browsing or target observations in generation prompts. Public training-data exposure cannot be excluded completely.
- Proposed region split: West primary, Southeast robustness analysis, and predefined NC June/July 2023 case corroborated by NC DEQ. Do not select the local case based on AI performance.
- Proposed equivalence margin ±10 percentage points is NOT yet approved. Justify or revise using pre-confirmatory evidence. Report difference (95% interval) and equivalence (90% interval entirely inside justified bounds) as separate questions. Nonsignificance does not establish equivalence.

## 3. Current evidence and readiness

| Item | State | Evidence / caveat |
| --- | --- | --- |
| Topic and direction | Selected | Raleigh heat retained only as fallback; flooding dropped |
| Historical screen | Reproduced from supplied intermediates | 593,849 site-days, 431 sites, 15 states; 59 eligible candidate groups |
| Episode independence | BLOCKED | 29 automated families under 800 km/3-day rule; sensitivity 22–58; not verified independent events |
| Pilot | Prepared, NOT run on real AI | 50 site-days from 2020, 250 prompts, 750 planned requests (5 conditions × 3 repeats) |
| Software integrity | Partially verified | v6 preflight independently passed; Claude reports 13/13 self-test, not independently confirmed in full; rerun after patch |
| Conventional IDW | Pilot evidence | 21/25 USG+ detected; 18/20 smoke-supported highs detected; 0/25 false alarms; MAE 9.04 µg/m³; selected sample only |
| Contextual comparator | Prototype | 4,763 supplied training observations; coefficients independently reproduced. Outcome-dependent sampling and calibration unresolved |
| Uncertainty code | PATCH NEEDED | Original v6 collapses duplicate bootstrap draws. Separate v6.1 patch and deterministic test exist; full integration pending |
| Confirmatory AI dataset/results | NOT STARTED | No real AI performance claim is supported |
| Portfolio/poster | Planning only | No completed competition-ready artifacts or earned scores |
| Semifinal | Not started | Practice in December; one laptop, 120 minutes, max 250-word synopsis |
| Rule clarification | Pending | Reference data, semifinal prewritten materials, state/regional requirements |

Automated families: 250 km/1 day = 58; 500 km/2 days = 46; 800 km/3 days = 29; 1,200 km/5 days = 22. Human adjudication must determine regional exposure periods, not merely source-fire counts. Both partners independently review `episodes/review_sheet.csv`, using full daily monitor trajectories, plume evidence and agency records; reconcile and document disagreements blinded to AI results.

### Conventional comparator evidence (NOT AI results)

2018 held-out smoke-supported USG+ sample: IDW missed 134/603; regression without smearing 85/603; with smearing 65/603. Overall MAE 8.65, 11.39, 13.03 µg/m³ respectively. 2019 had only SIX smoke-supported high observations (both IDW and regression missed 2); do not generalize from that year. In the 50 selected pilot targets, regression missed 0/20 smoke-supported highs but MAE was 16.12 versus 9.04 for IDW. Detection and reconstruction accuracy can trade off. These figures are preparatory analyses, not final findings.

## 4. Blocking work and decisions

- [ ] **P0 / both:** Obtain written TSA clarification on one generated dataset plus EPA reference data; confirm regional/state submission dates, semifinal materials and device rules. Do not assume permission.
- [ ] **P0 / technical:** Integrate v6.1 scorer correction into v6 on a separate branch. Test duplicate cluster draws, exact paired contrasts, smoke-specific estimand, and end-to-end scoring. Rerun preflight and self-tests. Never interpret original v6 bootstrap intervals.
- [ ] **P0 / both:** Review 10 random prompts per condition individually; approve engineering pilot. Run real 2020 pilot with one exact model ID and three repeats, log request order, validate outputs and score with corrected scorer. Never commit API credentials; cost estimate $1–2 is model-dependent and unverified.
- [ ] **P0 / both:** Independently adjudicate all 59 candidates, prioritizing coverage across families; preserve reviewer decisions and source evidence. Do not invent event independence or split events to reach a desired count.
- [ ] **P1 / technical:** Compare weighted versus unweighted contextual regression, with/without smearing, on pre-2021 validation. Account for oversampling high outcomes, report denominators, consider calibration and false alarms. Train final selected specification using approved 2018–2020 data and freeze it.
- [ ] **P1 / technical:** Export complete comparator-training source manifest (v6's 78 records omit 2018/2019 training sources); verify source checksums and preserve reproducible acquisition. Distinguish missing HMS from confirmed no plume; handle cross-year weather windows, negative measured concentrations, and missing precipitation. Pilot: 18/50 lack precipitation, including 3 without weather; one approximate six-hour aggregation.
- [ ] **P1 / both:** Freeze protocol by Dec 15 only if the data and rules support it. Lock final episode list, sample size and selection, weighting/estimands, comparator and model, margins, missing-output policy, multiplicity, scoring key hash, and exact prompts. Date both partners' approval. If infeasible, narrow scope rather than force a result.
- [ ] **P1 / both:** Begin timed semifinal practice in December, independent of the research pipeline.

## 5. Competition strategy and schedule

Current national rubric: portfolio 80 (Results 20, AI Reflection 10), poster 70 (Supporting Information 20), semifinal 80, total 230. Portfolio determines Top 24; poster round determines Top 12; top 10 announced after semifinal. Goal: exemplary performance on every criterion, not an estimated or guaranteed perfect score. Presentation still matters even though the standalone Communication criterion was removed. Official guide controls.

| Milestone | Date / status |
| --- | --- |
| Pilot, episode review and rule clarification | Immediate |
| Protocol freeze | Dec 15, 2026, internal target |
| Full generated dataset | Jan 5 internal stretch; Jan 10 working plan |
| Core analysis/figures | Jan 17 internal target |
| First complete portfolio | Jan 24 internal target |
| Regional-ready portfolio | Jan 31 internal stretch; Feb 4 previously reported progress-check target, subject to earlier official deadline |
| Eastern Regionals | Feb 12, 2027 (ECU; exact submission requirements pending confirmation) |
| State-ready package | Mar 14 internal target, earlier if required |
| NC state conference | Apr 15–17, 2027 (Greensboro) |
| Nationals upload | May 17–19, 2027 previously reported; reconfirm official event-specific dates |
| Nationals, if qualified | Jun 23–27, 2027 (Orlando, previously verified; reconfirm) |

State registration window previously verified as Dec 1–Feb 26; registration is not the portfolio deadline. Current NCTSA calls: [Regional](https://www.nctsa.org/regional-conferences), [State](https://www.nctsa.org/state-conference), [National dates](https://tsaweb.org/conferences/2027-national-tsa-conference/dates-and-deadlines_2027). Keep the earliest applicable confirmed deadline.

Portfolio: official section order; intro 1 page, data dictionary max 2, methods 1, conclusions max 2, next steps 1, AI Reflection max 4. Results/appendix as needed. Professional citation style and at least three source types. Separate one-page digital poster. Use readable original figures and trace every number to code. Poster: central practical effect and interval as hero; factorial grid secondary; measured-vs-generated diagnostic, NC example, environmental/economic/social/ethical implications. No invented findings or decorative charts masquerading as data. Test comprehension with unfamiliar viewers. Semifinal: rotate dataset types, practice offline on one laptop; confirm permission before bringing prepared code/templates. Target biweekly drills starting December and weekly by February if feasible.

## 6. Historical benchmarks and research register

Verified/accessible evidence: 2025 and 2026 WA state first-place portfolios (housing segregation and park tourism); Eastlake chapter 2025 national third, exact state/national submission identity unconfirmed; 2026 tourism economics national Top 24 per competitor documentation. Other housing and digital divide projects, poster and repositories have uncertain placements. The 2024 national champion (microplastics in yeast) is known from a school district story, not a full portfolio. No full 2025/2026 national champion portfolios recovered. Avoid attributing unverified motives, fabrication or judge behavior to competitors. Compare old portfolios using shared 70-point criteria, not penalizing them for the new AI Reflection. Retain clear quantitative questions, logical chart progression, observation/interpretation captions, readable maps, limitations and practical next steps. See `TSA Data Science 2027 Winner Analysis and Project Plan.docx` (Nov 25 winner-audit section; historical sections contain superseded heat plans and some claims needing correction).

Starting sources (verify full texts and exact claims before citation in final student work):

- [EPA AirData](https://aqs.epa.gov/aqsweb/airdata/download_files.html), [NOAA HMS archive](https://satepsanone.nesdis.noaa.gov/pub/FIRE/web/HMS/Smoke_Polygons/Shapefile/), [NOAA ISD](https://www.ncei.noaa.gov/products/land-based-station/integrated-surface-database), [NC DEQ exceptional events](https://www.deq.nc.gov/PM2.5ExceptionalEventsDemonstration).
- Burke et al. (2023), wildfire smoke and US air-quality progress: https://doi.org/10.1038/s41586-023-06522-6
- Feng et al. (2025), climate attribution of western smoke PM2.5: https://doi.org/10.1073/pnas.2421903122
- Considine et al. (2023), extreme-smoke estimation error: https://doi.org/10.1021/acs.est.2c06288
- Liu et al. (2024), surface vs aloft HMS smoke: https://doi.org/10.1071/WF23148
- AirGPT (2026), specialized instruction-tuned air-quality framework: https://doi.org/10.1016/j.inffus.2025.103730
- GeoLLM (2024), geospatial contextual prompting: https://arxiv.org/abs/2310.06213
- Roberts et al. (2017), spatial/temporal dependence in validation: https://doi.org/10.1111/ecog.02881
- Outcome-dependent sampling: https://pmc.ncbi.nlm.nih.gov/articles/PMC3664946/ ; Duan smearing: https://doi.org/10.1080/01621459.1983.10478017
- Climate-attributable wildfire mortality economic burden: https://doi.org/10.1038/s43247-025-02314-0
- [WA TSA winner archive](https://www.washingtontsa.org/high-school-events/data-science-and-analytics), [2025 national results](https://tsamembership.registermychapter.com/finalplacement/ntc2025), [2026 national results](https://tsamembership.registermychapter.com/finalplacement/ntc2026).

## 7. Repository and collaboration

Recommended layout: root `PROJECT_STATUS.md`, `AGENTS.md`, `README.md`, `CHANGELOG.md`; retain v6's `episodes/` and `pilot/` relative paths to avoid breaking scripts; add `research/`, `winner-analysis/`, `guidelines/`, `portfolio/`, `poster/`, `semifinal/` and `results/` as needed. Keep v6.1 patch separate until reviewed. Store raw large downloads outside Git, with hashes/download scripts; keep evaluation truth inaccessible to generation processes and AI sessions generating experimental values. Private repository and separate branches; review pull requests together. Do not commit `.env`, keys, raw private chats or restricted competition files without checking permissions. Keep student ownership and comply with current TSA AI rules. Separate pilot, mock and confirmatory outputs conspicuously.

Proposed division (confirm with partner): Abhinav leads code/statistics; Pratyush leads episode/source documentation and visual communication; both independently review episodes, understand all methods, approve changes, write reflections, present and practice. No partner approval has been assumed.

## 8. Next-session handoff

1. Read this status and v6 `pilot/README.md`; review the open blockers above.
2. Use the existing pipeline, not a new project. Check the v6.1 patch, then run the engineering tests and pilot only when credentials and team approval are available.
3. Do not claim that the pilot, episode adjudication or confirmatory experiment has already succeeded. Report actual test outcomes and blockers.
4. For each substantive revision, verify primary literature, compare the applicable historical winning examples under their own year's guidelines, and audit against the current rubric. Prioritize meaningful scientific and communication improvements, not extra complexity. No guarantee of winning and no invented evidence.

### Change log

- **2026-11-25:** Consolidated current v6 state, separate bootstrap correction, winner-audit findings, deadline plan and outstanding decisions for shared GitHub use. No new API calls, protocol approval, episode adjudication or GitHub upload performed by this document.
