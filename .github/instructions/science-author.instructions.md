---
applyTo: "**/*.tex"
description: This file describes the scientific writing style guide for papers authored by Adrian M. Price-Whelan.
---

**Purpose**: This document distills the writing style, rhetorical structure, and LaTeX conventions from a corpus of astrophysics papers authored or co-authored by Adrian M. Price-Whelan. It is designed to serve as a system prompt or style guide for AI writing agents tasked with producing new scientific papers in this voice.

- Follow the style guide below when writing LaTeX papers.
- Maintain the author's typical tone, rhetorical structure, and discipline.
- Do not copy text from prior papers.
- Avoid exaggerated or marketing language.
- All claims must be justified by evidence, equations, or citations.

---

## 1. High-Level Style Summary

This author writes observational and computational astrophysics papers with a distinctive blend of technical precision and accessible prose. The style is characterized by:

- **Confident but measured claims**: Core results are stated directly; uncertainty is reserved for limitations and generalizations
- **First-person plural voice**: Consistent use of "we" throughout, creating collaborative, active prose
- **Methodological transparency**: Assumptions are explicitly itemized; limitations are discussed candidly
- **Data-forward presentation**: Quantitative results are foregrounded with specific numerical values and uncertainties
- **Structured argumentation**: Clear logical flow from motivation → method → result → implication
- **Minimal jargon inflation**: Technical terms are used precisely but sparingly; acronyms are defined and used consistently

The papers target readers who are technically sophisticated but may not be specialists in the specific subfield. Explanations balance rigor with readability.

---

## 2. Voice & Tone Rules

### 2.1 Confidence Calibration

| Context | Tone | Example Phrasing |
|---------|------|------------------|
| Core results | Assertive | "We find...", "We detect...", "We measure..." |
| Method description | Declarative | "We use...", "We perform...", "We construct..." |
| Interpretation | Moderate | "This suggests...", "This indicates...", "This is consistent with..." |
| Speculation | Hedged | "We speculate that...", "One possible explanation is...", "This could be..." |
| Limitations | Direct | "This assumption may not hold...", "Our method does not account for..." |

### 2.2 Person and Voice

- **Always use first-person plural** ("we"), never first-person singular ("I") even for single-author papers
- **Prefer active voice** for describing actions the authors took: "We select stars using..." not "Stars were selected using..."
- **Use passive voice sparingly** for describing external processes or standard procedures: "The data were reduced using the standard pipeline"

### 2.3 Contribution Verbs

Use these verbs to describe contributions:

| Verb | Use Case |
|------|----------|
| present | Introducing a new method, sample, or result |
| demonstrate | Showing something works as claimed |
| show | Presenting evidence for a conclusion |
| find | Reporting a discovered result |
| measure | Quantitative determination |
| detect | Identifying a signal or feature |
| constrain | Placing bounds on a parameter |
| infer | Drawing conclusions from data |
| release | Making data or code available |
| develop | Creating new methodology |
| exploit | Leveraging a known property strategically |
| capitalize on | Using structure in a problem to advantage |

**Avoid**: "prove", "establish definitively", "demonstrate conclusively" (too strong for observational science)

### 2.4 Uncertainty Framing

- State uncertainties explicitly with numerical values when possible
- Use "approximately" or "roughly" for order-of-magnitude estimates
- Use "broadly consistent with" for agreement within uncertainties
- Acknowledge when assumptions are violated: "Of course, these specific assumptions do *not* hold sufficiently well!"

---

## 3. Section-by-Section Structure Guide

### 3.1 Abstract

**Purpose**: Provide a self-contained summary following a strict information hierarchy.

**Typical Structure** (4–6 sentences):
1. **Context**: One sentence establishing why the topic matters
2. **Gap/Problem**: One sentence stating what is unknown or limited
3. **Aims** (optional): What this paper sets out to do
4. **Methods**: Brief description of approach (one sentence)
5. **Results**: Key quantitative findings with numbers
6. **Implications**: Significance or future directions

**Do**:
- Include specific numerical results with uncertainties
- Use active constructions ("We present...", "We find...")
- Start with a compelling statement of importance

**Don't**:
- Begin with "In this paper, we..."
- Include citations in the abstract
- Use undefined acronyms
- Exceed ~200 words for a standard article

### 3.2 Introduction

**Purpose**: Motivate the work, establish context, and preview contributions.

**Typical Structure** (5–8 paragraphs):
1. **Opening hook**: Broad statement of importance (1 paragraph)
2. **Background context**: Prior work establishing the field (2–3 paragraphs)
3. **Gap identification**: What remains unknown or problematic (1 paragraph)
4. **This work**: What the paper does and why (1–2 paragraphs)
5. **Roadmap** (optional): Brief outline of paper structure

**Do**:
- Open with a declarative statement of scientific importance
- Weave related work into the narrative (not a separate literature review)
- End with a clear statement of the paper's contributions
- Use citations as support for claims, not as the subject of sentences

**Don't**:
- Begin with a citation
- Include detailed methodology in the introduction
- Bury the paper's contribution at the end
- Use a bulleted list for contributions (embed in prose)

**Citation Style**:
- Parenthetical preferred: "...as shown in previous work (Smith et al. 2020)"
- Narrative citations for emphasis: "Following the approach of Smith et al. (2020), we..."
- Use "e.g.," for non-exhaustive examples: "(e.g., Smith 2020; Jones 2021)"
- Use "see" for directing readers: "(see Smith 2020 for a review)"

### 3.3 Methods / Model / Data

**Purpose**: Provide complete description enabling reproduction.

**Typical Structure**:
1. **Data description**: Sources, selection criteria, sample size
2. **Assumptions**: Explicitly itemized list of model assumptions
3. **Mathematical formulation**: Equations with defined notation
4. **Implementation details**: Specific algorithms, software, parameters

**Do**:
- Itemize assumptions explicitly (using \begin{itemize})
- Define notation when first introduced
- Reference equations by label consistently
- State parameter values used

**Don't**:
- Assume reader knows standard methods without brief explanation
- Hide assumptions in prose—make them explicit
- Use notation inconsistently across sections

**Mathematical Presentation**:
- Use display equations for important results
- Use inline math for simple quantities
- Define all symbols upon first use
- Use consistent notation throughout (maintain a mental symbol table)

### 3.4 Results / Experiments

**Purpose**: Present findings systematically with appropriate evidence.

**Typical Structure**:
1. **Overview of results**: Summary of main findings
2. **Detailed presentation**: Subsection per major result or experiment
3. **Comparison to prior work**: How results compare to literature
4. **Validation**: Evidence that results are robust

**Do**:
- Number experiments or results subsections systematically
- Reference figures and tables in the order they appear
- State numerical results with uncertainties
- Compare to prior measurements when available

**Don't**:
- Include interpretation in results (save for Discussion)
- Present figures without textual explanation
- Bury key results in figure captions

**Figure/Table Referencing**:
- Use "\figurename~\ref{fig:label}" not "Figure \ref{fig:label}"
- Reference all figures in the text
- Place figures near first reference
- Captions should be self-contained but not repeat all prose

### 3.5 Discussion

**Purpose**: Interpret results, acknowledge limitations, and place work in context.

**Typical Structure**:
1. **Summary of key findings**: Brief restatement
2. **Interpretation**: What the results mean scientifically
3. **Comparison to theory/prior work**: How findings fit the field
4. **Limitations**: Honest assessment of caveats
5. **Future directions**: What comes next

**Do**:
- Begin by restating the main finding clearly
- Acknowledge limitations directly and specifically
- Suggest concrete future work
- Connect to broader scientific questions

**Don't**:
- Oversell implications
- Hide limitations in subordinate clauses
- Repeat the results section verbatim

### 3.6 Conclusions / Summary

**Purpose**: Provide a concise summary of contributions.

**Typical Structure**:
- Restate main result in one sentence
- Itemize key contributions (3–5 bullet points or description list)
- End with forward-looking statement

**Do**:
- Use description lists (\begin{description}) for multi-part conclusions
- Be concrete about what was achieved
- End on a forward-looking note

**Don't**:
- Introduce new information
- Repeat abstract verbatim
- Be vague about contributions

---

## 4. Stylistic & LaTeX Conventions

### 4.1 Paragraph Structure

- **Length**: 3–6 sentences typical; 8 sentences maximum
- **Topic sentences**: Begin paragraphs with the main point
- **One idea per paragraph**: Do not conflate multiple topics
- **Transitions**: Use logical connectors ("However,", "Furthermore,", "In contrast,")

### 4.2 Sentence Structure

- **Length**: Vary between short (10 words) and medium (25 words); avoid very long sentences (>40 words)
- **Complexity**: Use semicolons sparingly; prefer shorter sentences
- **Em-dashes**: Use for parenthetical asides: "The method---while computationally expensive---produces correct results"

### 4.3 Document Setup

Always use the custom preamble package:
```latex
\documentclass[modern]{aastex63}  % or aastex62, elsarticle
\usepackage{preamble-adrn}        % ALWAYS load the custom preamble
\usepackage{microtype}            % ALWAYS
\setlength{\parindent}{1.1\baselineskip}
\sloppy\sloppypar\raggedbottom\frenchspacing
```

The `preamble-adrn` package provides all standard macros. Do not redefine commands that already exist in the preamble.

### 4.4 Terminology and Acronyms

Use the predefined macros from `preamble-adrn`:

| Category | Macro | Output |
|----------|-------|--------|
| Projects/missions | `\gaia` | *Gaia* (italic) |
| Surveys | `\apogee`, `\sdss`, `\sdssiv`, `\sdssv` | APOGEE, SDSS (small caps) |
| Data releases | `\dr{2}`, `\dr{3}` | DR2, DR3 |
| Software packages | `\gala`, `\numpy`, `\scipy`, `\jax`, `\agama` | `gala`, `NumPy` (typewriter) |
| Languages/platforms | `\python`, `\github` | *Python*, *GitHub* (italic) |
| Generic acronyms | `\acronym{MCMC}` | MCMC (small caps) |
| Generic projects | `\project{Astropy}` | *Astropy* (italic) |
| Generic packages | `\package{emcee}` | `emcee` (typewriter) |

**Rules**:
- Define acronyms on first use: "Data Release 2 (\dr{2})"
- Use `\acronym{}` for acronyms not predefined in the preamble
- Use `\project{}` for mission/project names not predefined
- Use `\package{}` for software not predefined

### 4.5 Mathematical Conventions

Use the predefined math macros from `preamble-adrn`:

**Vectors and Matrices**:
| Macro | Usage | Example |
|-------|-------|---------|
| `\vec{x}` | Vectors (bold italic) | $\vec{x}$, $\vec{\theta}$ |
| `\mat{C}` | Matrices (bold upright) | $\mat{C}$, $\mat{M}$ |
| `\bs{x}` | Generic bold symbol | $\bs{\mu}$ |

**Operators and Calculus**:
| Macro | Usage | Example |
|-------|-------|---------|
| `\dd` | Differential operator | $\dd x$, $\int \dd^3 x$ |
| `\deriv{y}{x}` | First derivative | $\deriv{f}{t}$ |
| `\dderiv{y}{x}` | Second derivative | $\dderiv{f}{t}$ |
| `\pderiv{y}{x}` | Partial derivative | $\pderiv{\Phi}{z}$ |
| `\ppderiv{y}{x}` | Second partial | $\ppderiv{\Phi}{z}$ |
| `\Deriv{y}{x}` | Material derivative | $\Deriv{f}{t}$ |
| `\transp{A}` | Transpose | $\transp{\mat{M}}$ |
| `\inver{A}` | Inverse | $\inver{\mat{C}}$ |
| `\argmin` | Argmin operator | $\argmin_\theta$ |
| `\mean{x}` | Expectation/mean | $\mean{v_z}$ |

**Probability and Statistics**:
| Macro | Usage | Example |
|-------|-------|---------|
| `\given` | Conditional bar | $p(x \given y)$ |
| `\norm` | Normal distribution | $\norm(\mu, \sigma^2)$ |
| `\pdf` | Probability density | the posterior \pdf |
| `\df` | Distribution function | the stellar \df |

### 4.6 Units with siunitx

**Always use `siunitx` for units**. The preamble defines custom units and convenience macros:

**Predefined unit macros** (use these for common combinations):
| Macro | Output | Usage |
|-------|--------|-------|
| `\kpc` | kpc | `$D = 20\kpc$` |
| `\kms` | km s⁻¹ | `$v = 150\kms$` |
| `\mas` | mas | `$\mu = 3.5\mas$` |
| `\muas` | μas | `$\varpi = 50\muas$` |
| `\usurfdens` | M☉ pc⁻² | `$\Sigma = 40\usurfdens$` |
| `\uvoldens` | M☉ pc⁻³ | `$\rho = 0.1\uvoldens$` |

**Using siunitx directly** for other units:
```latex
$M = \qty{1.5e10}{\Msun}$           % 1.5×10¹⁰ M☉
$t = \qty{12}{\giga\year}$          % 12 Gyr
$r = \qty{8.2}{\kilo\parsec}$       % 8.2 kpc
$\sigma = \qty{30}{\km\per\s}$      % 30 km s⁻¹
```

**Custom SI units defined in preamble**:
- `\year` — year (yr)
- `\parsec` — parsec (pc)
- `\Msun` — solar mass (M☉)
- `\Rsun` — solar radius (R☉)

**Rules**:
- Use `\qty{value}{unit}` for number-unit combinations
- Use `\unit{...}` for units without numbers
- Use the convenience macros (`\kpc`, `\kms`, etc.) when they exist
- Do not manually format units with `\textrm{}` or `\mathrm{}`

### 4.7 Astronomy-Specific Macros

Use the predefined astronomy macros:

| Macro | Output | Usage |
|-------|--------|-------|
| `\feh` | [Fe/H] | metallicity `\feh = -1.5` |
| `\afe` | [α/Fe] | alpha enhancement |
| `\mgfe` | [Mg/Fe] | magnesium abundance |
| `\abun{X}{Y}` | [X/Y] | any abundance ratio: `\abun{O}{Fe}` |
| `\logg` | log g | surface gravity |
| `\Teff` | T_eff | effective temperature |
| `\vsini` | v sin i | projected rotation |
| `\zmax` | z_max | maximum height |
| `\DM` | DM | distance modulus |

### 4.8 Cross-References

Define these reference macros in your document (not in the preamble, for flexibility):
```latex
\newcommand{\sectionname}{Section}
\newcommand{\figurename}{Figure}
\newcommand{\equationname}{Equation}
\newcommand{\tablename}{Table}
```

Use consistently: `\sectionname~\ref{sec:method}` not `Section \ref{sec:method}`

### 4.9 Figure Captions

- Begin with a brief summary of what the figure shows
- Include all information needed to interpret the figure
- Use consistent structure: "**Top panel:** ... **Bottom panel:** ..."
- End with the key takeaway

### 4.10 Table Formatting

- Use `booktabs` package with `\toprule`, `\midrule`, `\bottomrule`
- Include units in column headers (use `siunitx` S columns for alignment)
- Align decimal points in numerical columns
- Keep captions above tables

### 4.11 Software and Data

Use the predefined software macros in `\software{}` sections:
```latex
\software{
    \gala\ \citep{gala},
    \numpy\ \citep{numpy},
    \scipy\ \citep{scipy},
    \package{Astropy} \citep{astropy},
    \package{emcee} \citep{emcee}
}
```

- Cite software with Zenodo DOIs when available
- State code availability clearly
- Use `\facility{}` for telescope/instrument acknowledgments

### 4.12 Draft Annotations

Use the predefined annotation macros during drafting:
- `\todo{fix this section}` — red TODO marker
- `\placeholder{approximate value}` — purple placeholder text

Remove all `\todo{}` and `\placeholder{}` before submission.

---

## 5. Synthetic Style Exemplars

### 5.1 Introduction Opening (Synthetic)

> The formation history of galaxies is encoded in the spatial distribution and kinematics of their stellar populations. In the Milky Way, we have access to precise measurements of individual stars, enabling detailed reconstruction of assembly events that would be unresolvable in external galaxies. However, connecting the observed phase-space distribution of stars to specific accretion events requires both exquisite data and sophisticated dynamical models. Here we present a new framework for identifying coherent stellar structures in the combined space of orbital properties and chemical abundances.

### 5.2 Methods Assumptions (Synthetic)

> To proceed, we make the following assumptions:
> - The gravitational potential of the host galaxy can be approximated as static and axisymmetric over the timescales of interest.
> - Stars do not appreciably change their element abundances over dynamical timescales.
> - The stellar population is well phase-mixed, such that the distribution function depends only on integrals of motion.
> - Observational uncertainties are well-described by Gaussian distributions with known variances.
>
> Each of these assumptions could be challenged: in particular, we expect the potential to evolve due to ongoing satellite accretion and interaction with the bar. We return to these assumptions, and the consequences of relaxing them, in the Discussion.

### 5.3 Results Paragraph (Synthetic)

> We detect a significant gradient in proper motion along the structure, with the amplitude varying from $3.2 \pm 0.1~\masyr$ at the trailing edge to $4.1 \pm 0.2~\masyr$ at the leading edge. This gradient is broadly consistent with expectations from orbital dynamics in a realistic Milky Way potential. However, the measured distance gradient of $0.15~\kpc~\textrm{deg}^{-1}$ is steeper than predicted by models that assume a smooth mass distribution, suggesting either systematic errors in our distance calibration or the influence of unmodeled perturbations.

### 5.4 Limitations Paragraph (Synthetic)

> Several important caveats apply to our analysis. First, we have assumed that the selection function of the input survey is spatially uniform, which is unlikely to hold in regions of high extinction. Second, our model treats the vertical and radial dynamics as separable, which breaks down near resonances and in the outer disk. Third, we have not accounted for the time-dependent gravitational influence of the Sagittarius dwarf galaxy, which is known to perturb disk dynamics at the level relevant to our measurements. Despite these limitations, our method provides a useful framework for estimating orbital properties directly from data without requiring a global potential model.

---

## 6. Rules for AI Writing Agents

### Voice and Tone
- [ ] Use first-person plural ("we") consistently
- [ ] Prefer active voice for author actions
- [ ] Match confidence to evidence: assertive for results, hedged for speculation
- [ ] Do not oversell: avoid "prove", "definitively", "for the first time ever"

### Structure
- [ ] Follow the standard section order: Abstract → Introduction → Methods → Results → Discussion → Conclusion
- [ ] Open Introduction with scientific importance, not a citation
- [ ] Itemize assumptions explicitly in Methods
- [ ] Reference all figures and tables in order of appearance
- [ ] Include a Limitations discussion

### Technical Accuracy
- [ ] Define all notation upon first use
- [ ] Include numerical uncertainties with all measurements
- [ ] Cite software and data sources appropriately
- [ ] Use consistent notation throughout

### LaTeX Conventions
- [ ] Load `preamble-adrn` package — do not redefine its commands
- [ ] Use predefined macros: `\gaia`, `\apogee`, `\dr{}`, `\gala`, `\numpy`, etc.
- [ ] Use `siunitx` for all units: `\kpc`, `\kms`, `\qty{value}{unit}`
- [ ] Use math macros: `\vec{}`, `\mat{}`, `\dd`, `\deriv{}{}`, `\given`
- [ ] Use astronomy macros: `\feh`, `\afe`, `\abun{}{}`, `\logg`, `\Teff`
- [ ] Use `booktabs` for tables with `\toprule`, `\midrule`, `\bottomrule`
- [ ] Use `\sectionname~\ref{}` style cross-references
- [ ] Include `\software{}` section with predefined package macros
- [ ] Remove all `\todo{}` and `\placeholder{}` before submission

### Common Failure Modes to Avoid
- [ ] **Vague claims**: "The results are interesting" → "We detect a $3\sigma$ signal"
- [ ] **Citation as subject**: "Smith et al. (2020) showed..." → "Previous work has shown (Smith et al. 2020)..."
- [ ] **Marketing language**: "revolutionary", "groundbreaking", "unprecedented"
- [ ] **Passive obfuscation**: "It was found that..." → "We find that..."
- [ ] **Missing uncertainties**: Report all measurements with error bars
- [ ] **Undefined acronyms**: Always define on first use
- [ ] **Buried contributions**: State what the paper does clearly in the Introduction

### Quality Checklist
- [ ] Every claim is supported by either evidence or citation
- [ ] Abstract contains specific numerical results
- [ ] Introduction ends with clear statement of contributions
- [ ] Methods could be reproduced by a competent reader
- [ ] Results are presented before interpretation
- [ ] Limitations are discussed honestly
- [ ] Conclusions are concrete, not vague
