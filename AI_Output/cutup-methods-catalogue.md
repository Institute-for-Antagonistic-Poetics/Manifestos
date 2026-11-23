# Scissors, Hats, and Folded Pages
## A catalogue of chance and recombination methods in text art, from Dada to the Burroughs–Gysin cut-up and after

This catalogue is meant to support building software tools. Each method is written out precisely enough to implement, and each entry has the same fields:

- **Origin**: who, when, where, and how sure we can be about it.
- **Procedure**: the method as an algorithm.
- **Parameters**: the knobs a tool could expose.
- **What it makes visible**: what the method shows that ordinary reading hides. This is the "art" payload.
- **Tool sketch**: one way to turn it into something people can play with.

Historical claims that are disputed or that rest on a single self-interested account are flagged. Several of the most repeated stories in this area (the Tzara "riot," the date of the first computer permutation poem) are shakier than their popularity suggests.

---

## Part 0: Deep ancestors (brief)

These come before the modern movements. They are not usually treated as "cut-up," but they establish the two basic moves: **recombining existing text** and **generating text by mechanism**.

| Ancestor | Date | Move | Note for tools |
|---|---|---|---|
| **Cento** (e.g. Proba's *Cento Vergilianus*, Ausonius's *Cento Nuptialis*) | 4th c. CE | A new poem made entirely of lines lifted from Virgil | The oldest "cut-up with line-sized scissors." The source's authority is borrowed, then subverted. |
| **Ramon Llull, *Ars magna*** | c. 1270s–1300s | Concentric rotating wheels of terms, so every combination can be read off | The first combinatorial text machine. A "volvelle" UI (draggable rings) is a natural interface. |
| **Swift, the Lagado word-engine** (*Gulliver's Travels*, Part III) | 1726 | A frame of word-blocks turned by cranks; students copy down any fragments that make sense | A satire of mechanical authorship, 230 years before computer text generation. Worth quoting in any tool's "about" page. |
| **Lautréamont, *Les Chants de Maldoror*** | 1869 | The "chance meeting of a sewing machine and an umbrella on a dissecting table" | A principle, not a procedure: meaning arises from unexpected juxtaposition. The Surrealists made it a motto. |
| **Mallarmé, *Un coup de dés*** | 1897 | Words scattered across the double page, with type size and spacing carrying meaning | Typography as a compositional dimension. Relevant for any tool that lays text out spatially. |
| **Raymond Roussel's *procédé*** | 1900s–1930s (explained in a posthumous 1935 essay) | Two nearly homophonous phrases with different meanings; the story must get from one to the other | A constraint-driven generator. Gysin later cited Roussel alongside Tzara. |
| **Futurist *parole in libertà*** (Marinetti) | 1912–14 | Syntax abolished; words, noise, and typography freed | Liberates the unit of composition from the sentence. |

---

## Part I: Precursors (1913–1950s)

### 1. Duchamp's chance compositions
**Origin.** Marcel Duchamp, *Erratum Musical* (1913): notes drawn at random from a hat to make a score for three voices. *3 Standard Stoppages* (1913–14): three one-meter threads dropped from a height of one meter, with the curves they made fixed as new "units of length."

**Procedure.** (a) Put the units (notes, words) in a container and draw without replacement; the draw order is the composition. (b) Let a physical process (a falling thread) define a shape, then use that shape as a ruler or template.

**Parameters.** Unit pool; with or without replacement; the physical process used.

**What it makes visible.** That standards (the meter, the musical scale) are conventions. A chance-made ruler is as "correct" as the official one.

**Tool sketch.** A "chance ruler" that turns a physical gesture (a mouse drop, a phone accelerometer trace) into a curve, then uses that curve to set line breaks or word spacing.

---

### 2. The simultaneous poem
**Origin.** *L'amiral cherche une maison à louer* by Richard Huelsenbeck, Marcel Janco and Tristan Tzara, performed at the Cabaret Voltaire in Zurich on 30 March 1916. Three voices perform at once in German, English and French, with a siren whistle, rattle and bass drum.

**Procedure.** Write several independent texts. Align them on a shared time grid, like a musical score, and perform them all at once. Occasional moments of unison are composed in deliberately.

**Parameters.** Number of voices; language of each voice; time alignment (strict score vs loose); noise tracks; where the unisons fall.

**What it makes visible.** How the ear separates, or fails to separate, competing speech streams (the "cocktail-party" problem). Also nationality: three languages occupying one acoustic space during a war in which those nations were fighting.

**Tool sketch.** A multi-track text-to-speech score editor. Each track has a language and voice, words sit on a timeline, and there is a "unison" marker. Users hear the moment the voices collapse into a single phrase.

---

### 3. The sound poem (*Lautgedicht*)
**Origin.** Hugo Ball, *Karawane* and *Gadji beri bimba* (Cabaret Voltaire, 1916). Later Kurt Schwitters, *Ursonate* (c. 1922–32), which grew from Hausmann's poster poem (see 5).

**Procedure.** Compose with phonemes and syllables that have no lexical meaning but keep the sound patterns (phonotactics), rhythm and intonation of speech.

**Parameters.** Phoneme inventory; syllable structure rules; repetition structure (Schwitters used sonata form).

**What it makes visible.** How much "meaning" comes from prosody alone. A meaningless incantation still sounds angry, liturgical or comic.

**Tool sketch.** A pseudo-language generator trained on the phonotactics of a chosen language (an n-gram model over letters or phonemes), with a slider that blends between languages and a choice of performance "mood" for text-to-speech.

---

### 4. Arp's collages "according to the laws of chance"
**Origin.** Hans (Jean) Arp, Zurich, 1916–17. Several contemporaries describe him tearing paper, letting the pieces fall onto a sheet, and pasting them where they landed. Hans Richter's story is that the idea came when Arp tore up a failed drawing and noticed the pattern on the floor.

**Important caveat.** The finished collages look fairly grid-like. MoMA notes glue traces showing Arp shifted pieces after they fell, and a curator there calls the result "assisted chance." He also sometimes used a paper cutter rather than tearing.

**Procedure.** Make the fragments, drop them, record their positions, then (optionally) adjust.

**Parameters.** Fragment shape and count; drop physics; and, most interestingly, **how much correction after the drop**.

**What it makes visible.** The tension between chance and taste. Every "chance" artwork has a hidden editing step.

**Tool sketch.** A physics-based drop of word tiles or paper shapes. The user can then nudge pieces, and the tool records every nudge. A "reveal" button overlays where chance put each piece against where the artist moved it: the invisible intervention becomes visible.

---

### 5. Hausmann's poster poems and optophonetic poems
**Origin.** Raoul Hausmann, Berlin, 1918. The poster poems (e.g. *fmsbwtözäu…*) were originally made by a printer lining up letters by chance, without Hausmann's direct intervention. The optophonetic poems used typographic size and weight as instructions for how to voice the letters.

**Procedure.** (a) Draw letters at random from a type case (letter frequencies follow the printer's stock, not the language). (b) Map typographic properties (size, boldness, case) to performance properties (loudness, pitch, duration).

**Parameters.** Letter pool and its frequency distribution; mapping from typography to voice.

**What it makes visible.** That letters are both visual objects and sound instructions. Also, the "random" letter distribution depends on what's in the type case, so randomness inherits the bias of its source.

**Tool sketch.** A type-case sampler where users choose the "case" (English letter frequencies, German, a specific book) and then play the result as sound, with font size mapped to volume.

---

### 6. Tzara's recipe: "To make a Dadaist poem"
**Origin.** Part of Tristan Tzara's *Manifesto on Feeble Love and Bitter Love*, read in Paris in December 1920 and published in 1921.

**Procedure** (paraphrased):
1. Take a newspaper and a pair of scissors.
2. Choose an article about as long as the poem you want.
3. Cut the article out, then cut out every word of it.
4. Put the words in a bag and shake it gently.
5. Take the words out one by one and copy them down, faithfully, in the order they come out.
6. Tzara's punchline: the poem will resemble you.

**Formal description.** A uniformly random permutation of the article's word tokens. Everything about the original except word order is preserved.

**Parameters.** Choice of source (the only authorial decision); unit size (Tzara specifies words); whether punctuation counts as a token.

**What it makes visible.** This is the most important method to understand precisely.
- The output preserves the **multiset of words** (the "bag of words") exactly. Word frequencies, vocabulary and length are unchanged; only order is destroyed. This is exactly the representation used by classical text-classification and topic models. A Tzara poem is what a bag-of-words model "sees" when it reads a text.
- The joke "it will resemble you" is partly true: the only real choice was **which article**, and that choice survives the shuffle completely.
- How much "sense" readers still find in a shuffled text shows how much meaning lives in vocabulary alone, separate from syntax.

**Tool sketch.** `tzara`: paste or fetch an article and shuffle. Then show a side panel with the word-frequency histogram, unchanged before and after, to make that invariant visible. A "resemblance" mode could shuffle several articles and let users guess which source produced which poem from vocabulary alone.

**A note on the famous anecdote.** Burroughs and Gysin both tell a story that at a Surrealist rally in the 1920s Tzara proposed pulling a poem out of a hat, a riot wrecked the theater, and André Breton expelled him. Treat this as their myth-making, not documented history:
- Tzara and Breton had already split before Surrealism was founded in 1924. The best-documented riot involving both is the July 1923 *Soirée du Cœur à barbe*, over Tzara's play, not a hat poem.
- The scholar Oliver Harris notes that Gysin promoted Tzara partly to settle an old score with Breton, who had excluded Gysin from a Surrealist exhibition in 1935.
- Harris also notes that the anecdote has tended to close off investigation into how the cut-up actually relates to Tzara.

---

### 7. Schwitters: Merz and the found poem (*i*-poems)
**Origin.** Kurt Schwitters, Hanover, from 1919. Merz collage used rubbish and printed scraps. His *i* poetics (early 1920s) held that the artistic act could consist only of isolating, framing and rhythmically presenting a piece of found material.

**Procedure.** Select a fragment of found text (a sign, an advertisement, a sentence from a textbook); change nothing except its frame (the title, layout, line breaks, or context of presentation).

**Parameters.** Selection rule; framing (title, line breaks, setting).

**What it makes visible.** That poetry can be a way of looking rather than a way of writing. Line breaks alone change how a sentence is read.

**Tool sketch.** A "lineation" toy: paste any prose and drag line breaks around. Each layout is a different poem from the same words.

---

### 8. Automatic writing
**Origin.** André Breton and Philippe Soupault, *Les Champs magnétiques* (written 1919, published 1920). Formalized in Breton's 1924 *Manifesto of Surrealism*.

**Procedure.** Write as fast as possible without stopping, correcting, or reflecting, so that the unconscious rather than deliberate thought produces the text.

**Parameters.** Speed; duration; whether deletion is allowed.

**Why it matters here.** It is the **opposite theory of chance** from the cut-up. The Surrealists placed the source of novelty inside the psyche. Tzara, and later Gysin and Burroughs, put it in a mechanical operation on external material. Burroughs's version of the Tzara story ends with Breton "grounding the cut-ups on the Freudian couch," meaning he redirected chance into psychology.

**Tool sketch.** A writing surface with no backspace, a visible timer, and text that fades if you pause. Pair it with a cut-up tool so users can feel the difference between the two kinds of chance.

---

### 9. The exquisite corpse (*cadavre exquis*)
**Origin.** Breton dates it to around 1925, at the house at 54 rue du Château in Paris (Jacques Prévert, Yves Tanguy, Marcel Duhamel and others). Pierre Reverdy claimed the game was older. It adapts an old parlor game. The name comes from the first sentence produced: *Le cadavre exquis boira le vin nouveau* ("The exquisite corpse will drink the new wine"). It soon became a drawing game too.

**Procedure.** Players fill fixed grammatical slots in turn, each folding the paper so the next player cannot see what came before. The classic French sentence has five slots: noun / adjective / verb / noun / adjective. In English the adjective comes first: adjective–noun–verb–adjective–noun. In the drawing version, each player draws a body section; only the connecting lines at the fold are visible to the next player.

**Parameters.** Number of players; the syntactic template (which is language-specific); **how much the next player sees** (nothing, the last word, the connecting lines).

**What it makes visible.** Grammar is what holds the sentence together when nobody knows the content. Syntax alone guarantees a "sentence" with an uncanny, collective sense. It is also a model of collaboration without communication.

**Tool sketch.** `corpse`: multiplayer (networked, or pass-the-phone). The server holds the template and enforces concealment; the reveal is animated as the paper "unfolding." A variant draws the slot fillers from different source texts instead of players.

---

### 10. Other Surrealist text games
Documented in compilations such as Brotchie and Gooding's *A Book of Surrealist Games*:
- **Questions and answers.** One player writes a question, another writes an answer without seeing it; the pairs are then matched.
- **Conditionals.** One player writes an "If…" or "When…" clause, another writes a consequence clause blind.

**Procedure.** Independent generation of the two halves of a fixed logical or dialogue form, then random pairing.

**What it makes visible.** Readers supply a causal or conversational link between any two clauses placed in a relation. The *form* produces the meaning.

**Tool sketch.** Pools of questions and answers (or ifs and thens) contributed by users or extracted from corpora, then randomly paired. FAQ pages and legal "if/then" clauses make particularly good sources.

---

### 11. Literary collage: newsreel and quotation montage
**Origin.** Burroughs himself cited T. S. Eliot's *The Waste Land* (1922) and John Dos Passos's *U.S.A.* trilogy (1930–36) as early examples of cut-ups. Dos Passos's "Newsreel" sections are montages of headlines, song fragments and news copy. Max Ernst's collage novels (e.g. *Une semaine de bonté*, 1934) did the same with engravings.

**Procedure.** Intentional selection and juxtaposition of quoted fragments from media, without chance.

**Why it matters.** It shows that the cut-up sits on a spectrum running from fully intentional collage to fully random shuffling. Burroughs's own practice sat somewhere in between (see the curation note in Part IV).

---

## Part II: Gysin and Burroughs (1959–1970s)

### Dating and credit
- The discovery is usually placed at the Beat Hotel, 9 rue Gît-le-Cœur, Paris, in **1959**. Gysin was cutting cardboard mounts with a Stanley knife over a pad of old newspapers. He noticed that the sliced layers formed new combinations of words.
- **Accounts differ on the month.** Burroughs's 1961 essay says summer 1959; many later accounts say late October. Gysin's account has him sharing the discovery when Burroughs returned from London in September 1959.
- Burroughs consistently credited Gysin as, to his knowledge, the first to make cut-ups.
- First publication: ***Minutes to Go*** (Paris: Two Cities, 1960), with Burroughs, Gysin, Gregory Corso and Sinclair Beiles. Corso's postscript disowned the project, noting that Tzara had done it before.
- Then *The Exterminator* (1960), the novels *The Soft Machine* (1961), *The Ticket That Exploded* (1962) and *Nova Express* (1964), and the collected essays and examples in ***The Third Mind*** (French 1976 / English 1978).

### The theory, briefly
Their methods carry a theory that differs from Dada's. Dada used chance mostly as negation and provocation. For Burroughs, language and recorded media are **control systems** (the "word virus"). Cutting them up does three things:
1. It breaks their hold ("rub out the word").
2. It reveals hidden content the text "really" contains.
3. It can even leak the future. Burroughs repeatedly claimed that cut-ups anticipated later events.

You don't have to accept the metaphysics to see the useful design principle: **the cut-up is presented as a way of reading the source, not only of writing something new.**

---

### 12. The basic cut-up (quartering a page)
**Origin.** Burroughs, "The Cut-Up Method of Brion Gysin" (first published 1961; reprinted in LeRoi Jones, ed., *The Moderns*, 1963).

**Procedure.** Take a page. Cut it down the middle and across the middle, making four sections. Rearrange the sections (e.g. put the fourth beside the first, the second beside the third) and read the new page as a text. Then edit: keep what works.

**Formal description.** The text is cut into a small number of **large blocks** whose internal order is preserved, and only the blocks are permuted. Because the cuts are *spatial* (a physical page), they fall mid-line and often mid-word, so new "words" appear at the seams.

**Parameters.**
- Number of cuts (2×2, 3×3, …).
- Cut geometry: straight, diagonal, or random polygons, like Gysin's original knife.
- The rearrangement rule.
- Whether to cut by **page geometry** (characters on a rendered line) or by **tokens**. Geometry produces broken words; tokens don't. This is a real aesthetic choice.

**What it makes visible.** **Where coherence lives.** Quartering preserves almost all local structure, so the result reads as plausible sentences that veer off at the seams. The method is also a measuring instrument: see the bigram-survival calculation in Part IV.

**Tool sketch.** `scissors`: render a text as a page. Users draw cut lines with the mouse (straight or freehand), then drag the pieces. The tool reflows the text across seams and **highlights the seams** in color, so the reader sees exactly where meaning was spliced. Add a "unit" slider for automatic cutting: letter → word → phrase → line → quarter page.

---

### 13. Multi-source cut-ups and "intersection readings"
**Origin.** *Minutes to Go* (1960) includes "Intersection Readings." Burroughs cut his own work together with newspapers, Rimbaud, Shakespeare, letters and conversations. Gysin offered the provocation that words don't belong to anyone.

**Procedure.** Cut several sources into units; combine the units by a rule. Rules include alternation (A, B, A, B), random choice, or proportional mixing.

**Parameters.** Sources; unit size; mixing weights; alternation pattern.

**What it makes visible.** How each voice "colors" the others. Rimbaud next to a stock report reveals the rhetoric of both.

**Tool sketch.** A mixer with one channel per source and a fader for each mix weight. Output text is color-coded by source, so provenance stays visible. A "who wins?" display shows which source's vocabulary dominates the reader's impression.

---

### 14. The fold-in
**Origin.** Burroughs, described at the 1962 International Writers' Conference in Edinburgh. He said he used it in writing *The Ticket That Exploded* and *Nova Express*; there is also an essay "Fold-ins" in *The Third Mind*.

**Procedure.** Fold a page of text vertically down the middle and lay it on another page. Read the composite straight across: each line is half of text A and half of text B.

**Time-travel variant** (Burroughs's own example): fold page one into page one hundred and insert the composite as page ten. The reader at page ten then flashes forward to page one hundred and back to page one, like a film flashback.

**Formal description.** For aligned lines i = 1…L, output line i = left-half(A_i) + right-half(B_i). The split is at a **spatial** column, so words are cut where the fold falls.

**Parameters.**
- Fold position (the middle, or offset).
- Which half of each text is shown.
- Vertical offset (sliding one page up or down a line before reading).
- Line width or font; this matters because the fold is spatial.
- For the time-travel version: which pages are folded together and where the composite is inserted.

**What it makes visible.** Two texts reading each other line by line. In the book variant, the **nonlinearity of a book's time**: every page coexists with every other.

**Tool sketch.** `fold`: two texts side by side. Users drag a literal paper fold and slide pages vertically, with the composite updating live. Book mode takes a whole text, picks a pair of pages, folds them, inserts the result elsewhere, and shows a "time map" of where each line came from.

---

### 15. Reading across columns and the three-column format
**Origin.**
- Burroughs observed that newspaper readers already read across columns peripherally: the eye catches the neighbouring story. The cut-up makes this unconscious cross-reading explicit.
- From early 1964 he worked in a **three-column format**: three parallel texts, often a newspaper layout (e.g. pieces in *My Own Mag*; later *The Dead Star*, 1969).
- He kept journals in parallel columns: events of the day, memories they triggered, and passages from what he was reading.

**Procedure.** Lay out three texts in parallel columns. Read in any order: down each column, straight across, or zigzagging.

**Parameters.** Sources per column; column widths; reading path.

**What it makes visible.** The simultaneity of experience. Several streams (news, memory, reading) are always running at once, and conventional prose serializes them.

**Tool sketch.** A three-column "newspaper" built from three feeds (or three of the user's own texts). A reading cursor follows a chosen path and can export the linearized result. This also works as a journaling tool: today / what it reminded me of / what I was reading.

---

### 16. The grid
**Origin.** "Formats: The Grid" (*Insect Trust Gazette*, 1964; reprinted in *The Third Mind*). Burroughs's "Warning Warning Warning Warning" in *My Own Mag* is a 32-cell grid meant to be read in any direction. Gysin's painting also used grids: in his calligraphic works he wrote in rows across the canvas, turned it, and wrote again.

**Procedure.** Place text fragments in the cells of a rectangular grid. Any path through the grid is a reading.

**Formal description.** The grid is a graph whose nodes are cells and whose edges are allowed moves. A reading is a walk on that graph.

**Parameters.**
- Grid size.
- Allowed moves: rook, king, knight, diagonal.
- Path type: rows, columns, boustrophedon (alternating direction), spiral, random walk, or self-avoiding walk.
- How fragments are assigned to cells.

**What it makes visible.** That "linear reading" is just one path among very many. For an m×n grid the number of self-avoiding paths is astronomically large, so the text "contains" far more readings than any reader will ever take.

**Tool sketch.** `grid`: fill cells from sources, choose a move rule, and watch a cursor walk. Users can also draw their own path with the mouse. Showing the path as a line over the grid (the path *is* the poem) gives a strong visual.

---

### 17. Permutation poems (Gysin)
**Origin.** Gysin took a short phrase and printed every reordering of its words. Examples include "I AM THAT I AM" and "KICK THAT HABIT MAN" (the latter often dated 1959, made by hand). Gysin performed permutation poems for BBC radio in 1960. Ian Sommerville programmed a computer to generate them. The tapes also included the "Pistol Poem," a gunshot recorded at different distances and spliced into a permutation.

**Dating caveat.** The date of the *computer* version is genuinely uncertain.
- Many sources say "1960."
- *The Third Mind* says the poems were printed on a Honeywell Series 200 model 120 programmed by Sommerville. That machine was not introduced until 1965.
- In a 1975 interview Gysin himself said they were programmed on a Honeywell in 1965.
- Nick Montfort, who reimplemented the program, has noted the question is unresolved.

So: the hand-made permutations date from 1959–60, and the computer version is more likely mid-1960s.

**Procedure.** Enumerate all orderings of the phrase's words and print them as lines, often as a block.

**The math, which a tool should get right.**
- A phrase of n *distinct* words has n! orderings. "KICK THAT HABIT MAN" gives 4! = 24 lines.
- With repeated words, the number of *distinct* lines is the multinomial coefficient n! / (k₁!·k₂!·…), where the kⱼ are the repetition counts. "I AM THAT I AM" has 5 tokens with "I" and "AM" each appearing twice, so there are 5! = 120 orderings of labelled tokens but only 5!/(2!·2!) = **30 distinct lines**.
- German sources speak of 120 permutations, which fits treating the tokens as labelled.
- *The Third Mind* headnote gives 2,420 lines of computer printout. That cannot be the set of distinct orderings of that one phrase (at most 30), so it must cover several phrases or include repetitions. Some popular accounts say the 2,420 lines are "every permutation of the title phrase"; that is arithmetically wrong.
- Growth is factorial: 6 distinct words → 720 lines, 8 → 40,320. This is why Gysin used very short phrases.

**Orderings matter aesthetically.**
- *Lexicographic* order clusters lines by their first word.
- *Random* order sounds like a shuffle.
- The **Steinhaus–Johnson–Trotter** order changes each line from the previous one by swapping one adjacent pair of words. The poem then "rotates" slowly, which is close to the incantatory effect of the recordings.
- Reimplementations differ, and the exact ordering Sommerville used isn't clearly documented.

**Parameters.** Phrase; ordering algorithm; distinct-only vs labelled duplicates; line layout; for audio, the spacing and inflection of each repetition.

**What it makes visible.** How word order alone produces meaning. "I don't dig work, man / Man, work I don't dig": the same words assert different things. Repetition also wears meaning away until the words become sound, which is what Burroughs and Gysin wanted.

**Tool sketch.** `permute`: type a phrase and choose an ordering algorithm. A counter shows n!, the distinct count, and the time needed to recite them all. Text-to-speech recitation varies pause and pitch. A permutohedron graph lights up the current ordering as it moves through the space of permutations.

---

### 18. Tape cut-ups
**Origin.** Burroughs, Gysin and Ian Sommerville from the early 1960s, intensively in the mid-to-late 1960s. Burroughs's "The Invisible Generation" (1966) addressed readers with portable tape recorders.

**Procedure** (a family of operations):
- **Splice.** Physically cut tape and rejoin it in a new order (the audio equivalent of method 12).
- **Cut-in / drop-in.** Record a stream (radio, TV, street sound, your own voice). Then rewind to random points and record new material over fragments of it.
- **Speed and direction.** Play back faster, slower, or backwards.
- **Overlay.** Mix several recordings, sometimes from several machines at once.
- **Micro-cutting.** Burroughs discussed slicing recorded speech into pieces only hundredths of a second long and rearranging them. He said he had tried this in 1968. This is essentially what we now call **granular synthesis**.

**Parameters.** Segment duration (from about 20 ms to minutes); selection rule; speed; direction; overlay count; crossfade (Burroughs used hard cuts).

**What it makes visible.** Hidden words that appear at splice points (the auditory equivalent of new words forming at a page seam). Also the way a recorded voice can be turned against its speaker: a politician's speech recombined into something they never said.

**Tool sketch.** `tape`: load or record audio, choose a grain size, and shuffle, splice, reverse or overlay with hard cuts. Show the waveform with colored splice marks. A "phrase finder" could run speech recognition on the output and highlight words that exist in the cut-up but not in the source.

**Ethics flag.** This is also the method of the deepfake. A tool that cuts up real people's voices should warn about that and probably limit itself to user-recorded audio.

---

### 19. Playback ("waking suggestion") and the Moka Bar operation
**Origin.** *The Electronic Revolution* (1970; it includes "The Feedback from Watergate to the Garden of Eden"). Burroughs framed tape cut-ups as a weapon available to anyone. He described using recorders in crowds to provoke unease by playing back riot noises cut in with recordings of the crowd itself.

**Practice.** In London Burroughs ran "operations": he made daily photographs and recordings of a place, then returned and played them back there. One target was the Church of Scientology's Fitzroy Street premises. The best known was the **Moka Bar** at 29 Frith Street, Soho, from August 1972. He reportedly edited "trouble noise" (sirens, shouting) into the recordings and played them at low volume so they blended with the street. The bar closed on 30 October 1972. Burroughs believed the operation worked; rising rents and ordinary business pressures are the obvious alternative explanation, so **the causal claim is unverifiable.**

**Procedure.** Record a place (Burroughs's "tape recorder 2"). Edit the recording, optionally inserting foreign sounds. Play it back in the same place at a later time, so the place hears a displaced version of itself.

**Parameters.** Time delay; inserted material; playback volume.

**What it makes visible.** That a place has a soundscape we stop hearing, and that displacing it in time makes it strange.

**Tool sketch (non-hostile).** `playback`: a phone app that records ambient sound in a place the user chooses (their own kitchen, a park) and plays it back there days later, layered with the present. The user hears "Tuesday's kitchen" inside "Friday's kitchen." Don't build the version aimed at a third party; it is harassment.

---

### 20. Film cut-ups
**Origin.** *Towers Open Fire* (1963) and *The Cut-Ups* (1966), both directed by Antony Balch with Burroughs. *The Cut-Ups* was reportedly assembled by cutting footage into fixed lengths and splicing them in strict rotation, regardless of content. Its soundtrack repeats a few phrases ("Yes, hello?") in permutation. Audiences at the London premiere reportedly demanded refunds.

**Procedure.** Split several reels into equal-length segments; interleave them by a fixed rule (round robin) rather than by meaning.

**Parameters.** Segment length; number of source reels; interleave rule; soundtrack.

**What it makes visible.** The **Kuleshov effect** run backward. Instead of editing to create meaning, a content-blind rule produces juxtapositions that viewers still interpret as meaningful.

**Tool sketch.** A browser video cutter: drop in clips, set the segment length, choose round robin or random, and render. Pair with method 17 for the soundtrack.

---

### 21. Scrapbooks and photographic cut-ups
**Origin.** From about March 1964 Burroughs kept scrapbooks combining his texts, newspaper clippings and photographs. He also photographed street scenes that resembled scenes in his writing. He said that after preparing a page he would often dream something related to its juxtapositions that night.

**Procedure.** Combine word and image fragments on a page around a theme or a correspondence (a coincidence between a text and the world).

**What it makes visible.** Coincidence. Burroughs treated "correspondences" between his texts and later events as evidence of prophecy. A tool can let users log their own coincidences without endorsing the metaphysics.

**Tool sketch.** A digital scrapbook where each page records the date of every fragment, so that later the user can look at what came "before" and "after."

---

### 22. Adjacent: the Dreamachine (cutting the visual field in time)
**Origin.** Gysin and Sommerville, about 1961. A slotted cylinder spins around a light bulb, and the viewer sits with eyes **closed** facing it. The flicker, in roughly the 8–13 Hz range associated with alpha rhythms, produces vivid patterns. It is not a text method, but it applies the cut-up idea to light: continuous illumination chopped into intervals.

**Safety, essential for any screen version.** Flicker in this range can trigger seizures in people with photosensitive epilepsy. Accessibility guidelines (WCAG) advise no more than three flashes per second. A screen-based Dreamachine should not be built for general play without strong warnings and design limits. It is better documented than simulated.

---

## Part III: Parallel and later procedural traditions (brief)

These are not Burroughs–Gysin methods, but they belong in the same toolbox, and some clarify the cut-up by contrast.

### 23. Shannon's approximations to English (1948)
In "A Mathematical Theory of Communication," Claude Shannon generated text of increasing statistical order: random letters; letters weighted by frequency; letter n-grams; then word unigrams and bigrams.

For the higher orders he used a **manual procedure that is itself a cut-up**:
1. Open a book at a random page.
2. Find the next occurrence of the current word (or letters).
3. Copy down what follows it.
4. Repeat from step 2 with the new word.

This sits right next to the cut-up in time and method. It is the founding example of what became Markov text generation (Kenner & O'Rourke's *Travesty*, *BYTE*, 1984), and in the long run of statistical language models.

**Tool sketch.** `shannon`: an order-k dial from 0 to 5. At k = 0 on words it reproduces Tzara's bag of words; as k rises the text approaches the source.

### 24. Cage's chance operations, mesostics, and "writing through"
- **Chance operations.** John Cage used the I Ching to make compositional decisions from 1951 (*Music of Changes*). Note that the I Ching's coin method has non-uniform line probabilities (1/8, 3/8, 3/8, 1/8), so "chance" here has a specific distribution.
- **Mesostics.** A spine string (often a name) runs down the middle of the poem. Each line is chosen from a source so that it contains the next spine letter. Cage used rules restricting where the spine letters may also appear, in stricter and looser variants. "Writing through" a source (e.g. *Writing through Finnegans Wake*, and the radio work *Roaratorio*, 1979) applies this across a whole book.

### 25. Jackson Mac Low: acrostic and diastic reading-through
Mac Low used systematic chance and "non-intentional" methods from 1954 (*5 biblical poems*).
- **Acrostic reading-through** (mostly 1960–63). Read through a source and take the next word beginning with each successive letter of a seed or index string. *Stanzas for Iris Lezak* was written in 1960 and published in 1972.
- **Diastic reading-through** (from 1963). The name is from Greek *dia* (through) + *stichos* (line), by analogy with "acrostic." For seed s₁s₂…s_k, take the first word in the source that has s₁ in position 1, then the next word after it with s₂ in position 2, s₃ in position 3, and so on; repeat the seed. Charles O. Hartman later automated this as the DIASTEXT program.

**What it makes visible.** A hidden name or phrase "threaded" through a text, reading it from inside. These are especially good for portraits and elegies.

### 26. Oulipo (founded 1960 by Raymond Queneau and François Le Lionnais)
The Oulipo explicitly rejects *chance* in favor of **constraint**, which makes a useful contrast.
- **N+7 (S+7)**, Jean Lescure: replace each noun with the seventh noun after it in a chosen dictionary. The dictionary is a hidden author; changing it changes the poem.
- **Queneau, *Cent mille milliards de poèmes*** (1961): 10 sonnets cut into strips line by line, so any line can be combined with any other. That gives 10¹⁴ sonnets. At one sonnet per minute, around the clock, reading them all would take about 1.9 × 10⁸ years.
- **Lipogram** (Perec, *La Disparition*, 1969, without the letter *e*), **snowball** (each word one letter longer than the last), **homophonic translation**.

### 27. Early computer text generators (context for the permutation poems)
- Christopher Strachey's love-letter generator, Manchester Mark 1 (1952): template + word pools.
- Theo Lutz, *Stochastische Texte* (1959): sentences built from vocabulary drawn from Kafka's *The Castle*, on a Zuse Z22.
- Nanni Balestrini, *Tape Mark I* (1961): recombined fragments of three source texts by computer.
- Alison Knowles and James Tenney, *A House of Dust* (1967): permutational verses on a computer.

Nick Montfort's *Memory Slam* reimplements several of these, including the permutation poems, and is a good reference for faithful reconstruction.

### 28. Erasure and treated texts
Tom Phillips, *A Humument* (begun 1966), painting over a Victorian novel to leave a new text. Ronald Johnson, *Radi os* (1977), an erasure of *Paradise Lost*. Later "blackout poetry."

**Procedure.** Keep a subset of a source's words *in their original positions*. Formally, select a subsequence: order is preserved, which is the opposite of Tzara's operation.

**What it makes visible.** The poem latent inside another poem, with the surrounding page still visible as a ghost.

### 29. Later cut-up practice
- **David Bowie** used cut-ups for lyrics from the 1970s. He met Burroughs for a 1974 *Rolling Stone* interview. In the mid-1990s he used the **Verbasizer** (developed with Ty Roberts), which shuffled lines from typed-in sources.
- **Kathy Acker** extended cut-up into wholesale appropriation.
- In sound, Burroughs's tape work prefigures industrial music, sampling and plunderphonics.

---

## Part IV: A unified model for tool design

Every method above can be described as a pipeline of six choices. A shared core library could implement them once and let each "tool" be a preset with its own playful interface.

1. **Source pool.** One text, several texts, a live feed, the user's own writing or recordings, or a place.
2. **Segmentation unit.** Letter, phoneme, syllable, word, phrase, line, half-line (the fold), page region (spatial cuts), time slice (audio/video), or grid cell.
3. **Recombination operator.**
   - Shuffle (Tzara).
   - Block permutation (quartering).
   - Full enumeration of permutations (Gysin).
   - Splice at a fold (fold-in).
   - Interleave (film cut-ups, multi-source).
   - Slot filling from a template (exquisite corpse, Strachey).
   - Walk on a graph (grid, Markov chain).
   - Constraint filter (diastic, N+7, lipogram).
   - Subsequence selection (erasure).
   - Simultaneity (simultaneous poem, overlay).
4. **Concealment.** Who sees what, and when (exquisite corpse, Surrealist games).
5. **The hand.** How much curation follows the chance step. This is underrated. Arp moved his pieces, and Burroughs heavily selected and edited his cut-up output. Most published "cut-ups" are **generated material that was then curated.** Tools should make keep/discard easy and should *log* the editing, so the balance between chance and choice can be shown afterwards.
6. **Rendering.** Page, column, grid, voice, tape, film, or a place in space.

### Coherence as a measurable dial
A useful way to make the invisible visible is to show users **how much of the source's sequential structure survives** each method.

Take a text of n tokens with n − 1 adjacent pairs (bigram occurrences). Cut it into b contiguous blocks and permute the blocks uniformly at random.
- The n − b pairs inside blocks always survive.
- Each of the b − 1 original boundary pairs survives only if block i lands immediately before block i+1. That happens with probability (b−1)!/b! = 1/b.
- So the expected number of surviving pairs is (n − b) + (b − 1)/b, and the expected surviving fraction is

  **[ (n − b) + (b − 1)/b ] / (n − 1).**

Check the extremes. At b = 1 (no cut) the fraction is 1. At b = n (Tzara's word-level shuffle) it is 1/n, essentially zero. Quartering a 300-word page (b = 4) keeps about 99% of word pairs, which is why such cut-ups read as near-sentences that swerve at the seams.

Three things follow:
- A single "scissors size" slider moves smoothly from Gysin to Tzara.
- Showing the surviving-pair percentage live teaches something true about where meaning lives in text.
- Bag-of-words (Tzara) → n-gram (Shannon) → modern language models is the same axis extended. A cut-up tool can honestly present itself as a way to *feel* what different text models preserve and discard.

(This counts surviving *occurrences* of adjacent pairs, not distinct word types; a pair can also reappear by coincidence elsewhere, which the formula ignores.)

### Other visibility devices
- **Seams.** Always able to highlight cut points.
- **Provenance coloring.** Every fragment remembers its source and position.
- **Invariants panels.** Show what a method *preserves*: word frequencies for Tzara, line positions for the fold-in, the multiset for permutations.
- **Path drawing.** For grids and columns, the reading path drawn over the layout.
- **Edit log.** Chance vs choice, à la Arp's glue traces.

### Randomness
- Use a **seeded** pseudo-random generator, so a cut-up can be shared and reproduced by its seed. A seed is also a nice playful object ("poem #48213").
- Offer distributions as well as the uniform one: the I Ching's non-uniform probabilities, or Hausmann's "type case" frequencies.
- Physical randomness inputs (a drop, a tilt, a microphone) bring back the gestural quality of scissors and paper.

### Sources and rights
Burroughs freely cut Rimbaud, Shakespeare and the newspapers. A public tool is better off defaulting to **public-domain corpora** (Project Gutenberg, old newspapers) and the **user's own text or recordings**, and leaving third-party copyrighted material to the user's own responsibility.

---

## Part V: Candidate tools (one line each)

| Tool | Method(s) | Hook |
|---|---|---|
| `tzara` | 6 | Bag shuffle with a frequency panel that never changes |
| `scissors` | 12, 13 | Draw cuts, drag pieces, see seams; unit slider from letter to page with live bigram survival |
| `fold` | 14 | Drag a paper fold across two texts; book-mode time travel |
| `columns` | 15 | Three-column newspaper and journal; reading-path export |
| `grid` | 16 | Fragments in cells; walk rules from rook to knight to spiral |
| `permute` | 17 | Phrase permutations with SJT "rotation," counts, and recitation |
| `corpse` | 9, 10 | Multiplayer concealment game with an animated unfolding reveal |
| `simultan` | 2 | Multi-voice, multi-language text-to-speech score with unison markers |
| `lautgedicht` | 3, 5 | Pseudo-language and type-case letter sound poems |
| `arp` | 4 | Physics drop of word tiles, nudges logged and revealable |
| `shannon` | 23 | Order-k dial from Tzara's bag to near-source |
| `diastic` / `mesostic` | 24, 25 | Thread a name through a text |
| `n7` | 26 | Noun substitution with selectable dictionaries |
| `erase` | 28 | Click to black out words; keep what remains in place |
| `tape` | 18 | Granular, splice, reverse and overlay audio cut-up with seam markers |
| `playback` | 19 | Record a place and replay it there later, layered with the present |

---

## Sources (selected)

Primary and near-primary:
- Burroughs, "The Cut-Up Method of Brion Gysin" (1961; in *The Moderns*, 1963): https://writing.upenn.edu/~afilreis/88v/burroughs-cutup.html
- Burroughs, statements at the 1962 International Writers' Conference (fold-in): https://realitystudio.org/texts/burroughs-statements-at-the-1962-international-writers-conference/
- Tzara, *Dada manifeste sur l'amour faible et l'amour amer* (dating and publication): https://zeteojournal.com/wp-content/uploads/2016/03/5565b-tristan-tzara-dada-manifeste-sur-lamour-faible-et-lamour-amer.pdf
- Breton archive on the exquisite corpse: https://www.andrebreton.fr/en/work/56600100663500

Scholarship and museum records:
- Oliver Harris, "Burroughs is a Poet Too, Really: The Poetics of *Minutes to Go*": https://realitystudio.org/scholarship/burroughs-is-a-poet-too-really-the-poetics-of-minutes-to-go/
- Nick Montfort, "A Gysin & Sommerville Question" (dating the permutation program): https://nickm.com/post/2014/11/a-gysin-sommerville-question/
- MoMA on Arp's chance collages: https://www.moma.org/collection/works/37013 and https://www.moma.org/audio/playlist/198/2645
- Mac Low on acrostic and diastic methods: https://www.writing.upenn.edu/~afilreis/88v/maclow-pleasure.html
- Simultaneous poem dating (30 March 1916): https://www.melusine-surrealisme.fr/2000_Simultaneisme-Dada.pdf
- Grid and three-column formats in *My Own Mag*: https://realitystudio.org/bibliographic-bunker/my-own-mag/the-evolution-of-the-cut-up-technique-in-my-own-mag/
- *The Electronic Revolution*: https://en.wikipedia.org/wiki/The_Electronic_Revolution
- Moka Bar operation: https://greatwen.com/2011/11/09/william-burroughs-and-the-strange-demise-of-londons-first-espresso-bar/
- Hausmann poster poems: https://www.wikipedia.org/wiki/Raoul_Hausmann and Centre Pompidou records
- Cut-up overview and the Gysin discovery: https://oeln.net/cut-ups ; https://en.wikipedia.org/wiki/Cut-up_technique ; https://en.wikipedia.org/wiki/Brion_Gysin

Items in Parts 0 and III not listed above (Shannon 1948, Cage, Oulipo, Strachey, Lutz, Balestrini, Phillips, Johnson, the Verbasizer) are standard references stated from general knowledge and should be checked against primary sources before being quoted in a tool's documentation.
