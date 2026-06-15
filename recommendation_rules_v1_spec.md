# Flying Pig Recommendation Rules v1 — Short Spec

## Purpose

This spec defines the first recommendation engine for the future self-contained Flying Pig activity HTML tool.

The engine should produce **balanced lineups**, not loose ranked lists. It should use a **slot-based structure** with **weighted random selection** inside each slot. Each generated recommendation should include brief reason tags explaining why each activity was chosen.

Companion machine-readable file: `recommendation_rules_v1.json`.

---

## Selection Model

The tool should not simply rank all activities and pick the top results.

Instead:

1. Pick the recommendation mode:
   - Beginner Class
   - Advanced Class
   - Show
2. Build that mode’s required lineup slots.
3. Create an eligible candidate pool for each slot.
4. Score candidates using suitability, difficulty, format, risk, props, tags, and variety.
5. Randomly select among high-scoring candidates.
6. Enforce global constraints.
7. Show reason tags under each selected activity.

Default behavior should be **rotating recommendations**, not the same fixed lineup every time.

---

## Regenerate Behavior

Each lineup slot should have a **Regenerate** button.

Regenerate should swap only that slot while preserving the broad role of the slot:

- Long-form slot → another eligible long-form
- Guessing-game slot → another guessing game
- Show final slot → **Oh Waiter** or **Conducted Song / Show-Closing Conducted Song**
- Beginner circle-game slot → another beginner-eligible circle game or low-risk exercise
- Beginner capstone slot → **3-Line Scenes** or **I Am a Tree**
- Beginner closer slot → **Five Things** or **Name Game**
- Advanced closer slot → always **Five Things**
- Advanced short-form slot → another advanced-eligible short-form or technical rep

A regenerated slot must still respect whole-lineup constraints.

---

# Beginner Class Rules

## Default Duration

**90 minutes**

## Fixed Opening

Every beginner class recommendation must start with:

1. **Jesse’s Opening Meditation**
2. **Zip Zap Zop**

Beginner Zip Zap Zop should usually be the standard version.

## Lineup Shape

After the fixed opening, recommend:

1. **5–7 circle games / low-risk exercises**
2. Capstone exercise:
   - **3-Line Scenes**, or
   - **I Am a Tree**
3. Closer:
   - **Five Things**, or
   - **Name Game**

## Beginner Capstone Weighting

Use equal rotation between:

- **3-Line Scenes**
- **I Am a Tree**

## Beginner Closer Weighting

Use equal rotation between:

- **Five Things**
- **Name Game**

## Beginner Exclusions

Beginner recommendations should exclude by default:

- all short-form show games,
- **1 Minute Scenes**,
- advanced-only exercises such as **5 Second Delay**,
- complex long-form structures.

Beginner class usually caps out around **3-Line Scenes**. It does **not** use **1 Minute Scenes**.

## Beginner Difficulty

Allow:

- Easy activities freely.
- Moderate activities, but limit to **1–2 per lineup**.
- Hard activities should be excluded.

## Beginner Ordering

Beginner activities should generally progress **easy to harder**.

The structure should feel like:

1. Meditation
2. Zip Zap Zop
3. easiest circle/focus games
4. moderate circle games, if any
5. 3-Line Scenes or I Am a Tree
6. Five Things or Name Game

## Beginner Variety

Use light duplication control.

Some overlap is fine, but avoid building a whole class out of one skill family. For example, avoid stacking too many one-word/sentence-construction games in one beginner lineup.

A strong beginner lineup should mix some of:

- focus/listening,
- rhythm/energy,
- physical commitment,
- association,
- simple story/sentence construction,
- 3-Line Scenes or I Am a Tree,
- closer.

---

# Advanced Class Rules

## Default Duration

**2.5 hours** / **150 minutes**

## Fixed Opening

Every advanced class recommendation must start with:

1. **Jesse’s Opening Meditation**
2. **Zip Zap Zop**

Advanced class should move quickly from standard Zip Zap Zop into a variant, such as reverse or phonetic substitutions.

## Lineup Shape

After the fixed opening, recommend:

1. 1–2 additional warmups or technical focus exercises
2. **3–4 short-form games / technical reps**
3. At least one long-form structure
4. **Five Things** as the closer

## Advanced Long-Form Requirement

Every advanced class recommendation must include **at least one long-form structure**.

The long-form should usually go **near the end**.

After the long-form, the recommendation should go directly to **Five Things**. Do not add another short-form rep after the long-form by default.

## Advanced Long-Form Pool

Advanced long-form rotation should include:

- Montage
- Town Hall
- Repeater
- La Ronde
- French Braid
- Slacker
- Two Chairs
- Growing and Shrinking

Use equal rotation unless later overridden.

## Advanced Short-Form / Technical Reps

Advanced class should include **3–4 short-form games or technical reps**.

Selection should mix:

- show-suitable short-form games,
- practice-only technical exercises,
- scene/relationship/emotional work,
- physical/character work,
- verbal/constraint work.

Do not restrict advanced class recommendations only to show-ready games. Training value matters.

## Advanced Closer

Advanced class should always close with:

- **Five Things**

Do not use **Name Game** as the advanced-class default closer.

## Advanced Difficulty

Hard/high-load games are allowed, but limit to **2–3 hard short-form / technical / constraint activities** per advanced class lineup.

The required long-form does **not** count against this hard-activity limit.

## Advanced Guessing Game Limit

Advanced class recommendations should include **max 1 guessing game**.

## Advanced Variety

Use light variety preference.

Prefer skill variety, but allow focused repetition if the class is clearly targeting a specific skill.

---

# Show Recommendation Rules

## Default Duration

**75 minutes**

## Output Type

Generate a **full show lineup**, not just a list of possible games.

## Formal Opening

Always include a formal opening / host-framing slot.

Do **not** treat the formal opening as a catalog activity.

## Show Shape

A standard 75-minute show recommendation should include:

1. Formal opening / host framing
2. First playable activity
3. **5–6 short-form games** total
4. Exactly **1 guessing game**
5. At least **1 long-form structure**
6. Optional final game if the long-form is second-to-last

## Required Guessing Game

Every show recommendation should include **exactly 1 guessing game**.

Guessing-game pool:

- Why Were You Late?
- The Dating Game
- Job Interview
- Home Shopping Network / HSN

Use equal rotation.

Do **not** count these as guessing games:

- Foreign Film
- Three-Headed Expert

## Show Long-Form Requirement

Every show recommendation should include **at least 1 long-form structure**.

Show long-form pool:

- Montage
- Town Hall
- French Braid
- Slacker
- Repeater
- Growing and Shrinking
- Two Chairs

Use equal rotation.

## Show Long-Form Placement

Long-form usually goes **last or second-to-last**.

Exception:

- **Town Hall** opens the show when selected.

## Show Final Game

If the long-form is last, no extra final game is needed.

If the long-form is second-to-last, the final game should be one of:

- **Oh Waiter**
- **Conducted Song / Show-Closing Conducted Song**

Use equal rotation between those two.

The final-game pool should be limited to those two by default.

## Show Opener

When the show does not open with Town Hall, the first playable activity should rotate among clear opener candidates.

Do not force one opener every time.

Avoid complex or slow games first.

**Four Square** is a strong opener candidate and is often the first short-form game, but it should not be forced every time.

Four Square counts as **short form**, not long form.

## Show Format Variety

A show recommendation should intentionally vary short-form game types.

Default target mix:

- 1 quick joke / line game
- 1 physical or visual game
- 1 structured hosted game
- 1 verbal or constraint game
- exactly 1 guessing game
- optional final filler/song closer
- at least 1 long-form

Avoid back-to-back games with very similar mechanics.

## Show Risk Control

Show recommendations should include:

- exactly 1 guessing game,
- max 1 physical onstage audience-volunteer game,
- max 2 additional high-risk games beyond the required guessing game.

The required guessing game is tracked separately and does **not** count against the additional high-risk cap.

High-risk factors include:

- high memory/tracking load,
- difficult verbal constraints,
- strong host-dependence,
- likely stall risk if a role is weak,
- complex mechanics.

## Audience-Volunteer Limit

Audience-volunteer cap applies only to games that bring audience members physically onstage.

Current audience-volunteer pool:

- Pillars

Do **not** count these as audience-volunteer games:

- Lines from a Box
- Town Hall
- Slideshow
- ordinary audience-suggestion games

---

# Reason Tags

Every recommended activity should show brief reason tags directly under the activity name.

Examples:

- `beginner-eligible · circle game · focus · no props`
- `required guessing game · audience-readable · host structure`
- `required long-form · late-show structure · ensemble tracking`
- `show closer · final-game pool · high energy`

Use no more than five reason tags per activity.

---

# Implementation Notes

The recommendation rules should remain separate from the catalog text.

The catalog is the preserved content source. The rules file is only a recommendation layer.

The future HTML tool should embed:

1. `flying_pig_activity_dataset_v1.json`
2. `recommendation_rules_v1.json`
3. JavaScript logic for search, filtering, expansion, scoring, lineup generation, and slot regeneration.

If a slot has no valid candidates, the tool should relax soft preferences before violating hard constraints.

Hard constraints should generally never be violated silently.
