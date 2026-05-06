# Commercial Sale Feasibility — Selling the Prop on Etsy or eBay

**Status:** Researched 2026-05-06. Conclusion: **don't.**

---

## Disclaimer

This is not legal advice. It's a hobbyist's risk assessment based on
public sources. If you actually intend to commercialize anything in this
space, talk to an IP attorney — preferably one who handles entertainment
trademarks.

---

## TL;DR

No, you cannot safely or legally sell a replica of the Hitchhiker's Guide
prop from the 2005 film on Etsy, eBay, or any other public marketplace.

Three layered reasons:

1. The 2005 film's prop design is copyrighted by Disney / Touchstone /
   Hammer & Tongs. Your replica is a derivative work; selling it is
   copyright infringement regardless of whether you "make a profit" or
   just "recoup costs."
2. The *Hitchhiker's Guide to the Galaxy* name, characters, and trade
   dress (including "DON'T PANIC" used in the iconic context) are
   protected by a combination of trademark, common-law trademark, and
   copyright held by Disney and/or the Douglas Adams estate.
3. Etsy and eBay both have aggressive IP-takedown programs. Disney
   alone files thousands of DMCA notices per month. Listings disappear
   within hours of a complaint, and repeat offenders are banned.

Build it for yourself. Document the build publicly under the existing CC
BY-NC-SA 4.0 license. Don't sell the physical object.

---

## What you would actually be selling

A clamshell book-shaped device whose closed cover, open-page layout,
display position, and "DON'T PANIC" trade dress collectively identify
it as **the** Hitchhiker's Guide from the 2005 film. The recognizability
*is* the value — and it is also exactly what makes the sale unlawful.

---

## IP layers in play

There are at least four overlapping rights to consider. You do not have
a license for any of them.

| Right | Subject | Likely holder |
|---|---|---|
| Copyright | Visual design of the on-screen prop in the 2005 film | Disney / Touchstone / Hammer & Tongs |
| Copyright | Underlying *Hitchhiker's Guide* literary universe | Estate of Douglas Adams |
| Trademark / common-law | The name *Hitchhiker's Guide to the Galaxy* | Disney historically; Adams estate currently |
| Trade dress | The "DON'T PANIC" + book-shaped reader visual identity | Disputable, but enforceable in context |

Important nuance: even where a registered trademark has lapsed, the
underlying **copyright** in the prop's design is still in force and
still owned by the studio. Trademark and copyright are independent
regimes.

---

## Trademark research findings (USPTO)

Two of Disney's USPTO trademark applications for "Hitchhiker's Guide to
the Galaxy" exist in the public record, and **both have been
abandoned**:

- **Serial 78614189** — filed 2005-04-21 for toys and sporting goods.
  Abandoned 2007-05-15 (no statement of use filed).
- **Serial 78979873** — filed 2005-04-21 for pre-recorded audio/video
  discs and motion pictures. Abandoned (failure to respond).

**This does not mean the franchise is unprotected.** Three reasons:

1. Disney still holds copyright in the film and its visual designs.
   That requires no registration to be enforceable.
2. The Adams estate retains the underlying literary IP and likely a
   trademark in *Hitchhiker's Guide* as a series name (separate from
   Disney's lapsed merchandising marks).
3. Common-law trademark rights attach to recognizable marks-in-use,
   especially famous ones, even without USPTO registration.

So: the absence of an active Disney USPTO registration is **not** an
opening. It just means the layer that gets you taken down is
copyright + the estate's residual trademark, not Disney's lapsed marks.

---

## "DON'T PANIC" specifically

USPTO has many "DON'T PANIC" trademark registrations across unrelated
categories (clothing brands, escape rooms, restaurants). The phrase
predates Adams in literature, and on its own is generally not
trademark-protectable as text.

**However**, using "DON'T PANIC" *on a green book-shaped device meant to
look like the Guide* is trade-dress imitation regardless of whether the
phrase itself is registered. Context matters. The combination of the
words, the visual styling, and the form factor is what you'd be selling
— and that combination is identifiable property.

---

## Marketplace reality

What the platforms actually do, sourced from their own published
guidance and reporting on enforcement actions:

- **Etsy.** Operates a notice-and-takedown system aligned with the DMCA
  and 17 USC §512. Listings can be removed within hours of a complaint
  with no warning. Repeated infringement leads to shop suspension. Etsy
  has explicitly stated that fan art of copyrighted characters is
  derivative work and not protected by a "fan art exception."
- **eBay.** Operates the VeRO (Verified Rights Owner) program. Rights
  holders can self-serve takedowns. Three strikes under VeRO and the
  account is gone.
- **Disney specifically.** Files thousands of DMCA notices per month
  across platforms. Pursues sellers, not just listings — has sued Etsy
  shop owners who sold unauthorized Disney-themed items.

The community-known shorthand is "lay low until the cease-and-desist,
then stop everything." That is a description of how to delay
consequences, not of what is legal.

---

## Scenarios you might consider, ranked by risk

### A. Listed openly as "Hitchhiker's Guide" prop

**Risk:** Maximum. Listing pulled in hours, C&D likely, account
suspension on repeat. Personal liability for damages possible if
listings persisted at scale.

### B. Listed ambiguously ("sci-fi book-reader prop")

**Risk:** High. Lower automated-detection probability, but a single
complaint reveals the design as clearly derivative. Same outcomes as A,
delayed by days or weeks.

### C. Sufficiently transformed original design

**Risk:** Low — *if actually transformed*. Build an "interactive prop
book" with original cover art, no "DON'T PANIC" text, original
proportions, no recognizable visual cues. The aesthetic of "small
clamshell device that plays a video" is not itself protected. The
specific Guide design is.

### D. License the IP from rights holders

**Risk:** Low. **Feasibility:** effectively zero for an individual
maker. Disney does not entertain individual licensing inquiries for
prop replicas.

### E. Sell the build documentation, not the prop

**Risk:** Lower than selling the physical object, but non-zero. Books
and tutorials documenting how to build a copyrighted prop have
themselves been targeted by takedowns. Documentation framed as
*commentary, criticism, or instructional reference* has stronger fair-use
footing than the object itself, but is still adjacent to the IP.

---

## What you can do legally and commercially

- **Sell your skill, not the IP.** Take commissions to build "an
  interactive prop book in the style my client describes" — where the
  client supplies the design intent. The legal exposure shifts toward
  the client and away from a public storefront listing branded
  Hitchhiker's. This is still imperfect, but it's a different legal
  posture.
- **Sell a transformed original.** Use the engineering you developed
  here to make and sell an original-design "interactive prop book"
  brand. Open the hinge differently. Pick a different on-cover phrase.
  Use original art. The technical work transfers; the IP risk doesn't.
- **Sell the engineering education.** A blog post, video, or course
  about building a Pi-powered prop book is a viable revenue path.
  Discuss technique generically; show your build as illustration. Avoid
  selling files or models that are direct derivatives of the film
  prop.
- **Keep this build personal.** Display at cons, use as a portfolio
  piece, photograph and share for community goodwill. None of that is
  commercial sale.

---

## How this interacts with the project's license

The repository is licensed CC BY-NC-SA 4.0 (see ADR-0004). That license
covers **only the original work in this repo** — the writing, the ADRs,
the 3D models, schematics, and code that you author. It does **not**:

- Grant any rights in the underlying *Hitchhiker's Guide* IP, which
  isn't yours to license.
- Make non-commercial fan use safe — that's a copyright question
  governed by US/UK statute and the rights holders' tolerance, not by
  this repo.

The license's NC term aligns with this conclusion: the project
explicitly does not authorize anyone — including the project owner — to
manufacture and sell replicas under cover of the project files.

---

## Recommendation

Drop the idea of selling the prop. The legal exposure ranges from
"listing yanked, account banned" at the low end to "named defendant in
a copyright suit" at the high end, and the upside is a small-margin
prop sale.

If commercial revenue from this skill set is the goal, the path is to
develop an **original-design interactive book prop** as a separate
project — same Pi, same display, same hinge mechanism, completely
different aesthetic with no Hitchhiker's references. The technical
skills built here transfer cleanly. The IP exposure does not.

---

## Addendum (2026-05-06): the one-time-prototype-sale scenario

After the initial writeup, the project intent was clarified: build the
prop **once**, publish the plans **for free**, and **sell the single
prototype** to dispose of it. This narrows the scenario but does not
change the legal conclusion. Treating it as two separate questions:

### Question 1: Can the plans be published for free?

Strictly speaking, the published plans (CAD, STLs, code, schematics) are
derivative works of the on-screen prop design. Distributing them, even
gratis, is technically copyright infringement.

**Practical reality:** rights holders almost never pursue free
distribution of fan-made prop files. The enforcement bar is "is this
causing commercial harm?" Free files don't clear it, and the optics of
"Disney sues hobbyist for sharing free fan files" are uniformly bad for
the rights holder. Free fan files for *Star Wars* helmets, *Iron Man*
gauntlets, *Halo* armor, and dozens of other franchises sit on Printables
and Thingiverse for years without takedowns.

**Risk:** low. Most likely outcome: nothing happens. Worst likely
outcome: a polite takedown notice from the host, you remove the files,
done.

**License interaction:** the project's CC BY-NC-SA 4.0 license already
forbids others from commercializing the plans (the NC clause). Continue
to publish under that license. It doesn't grant rights you don't have,
but it sets the right expectation for the fan community.

### Question 2: Can the single prototype be sold?

This is where the legal answer doesn't bend.

A one-time sale of one derivative-work object is **still copyright
infringement** under US law (and similarly under UK CDPA 1988). There is
no "first physical build" exception. The first sale doctrine (17 USC
§109) covers reselling a copy you bought lawfully — it does **not**
authorize selling a copy you yourself manufactured without a license.

**Practical risk for a single low-priced listing:**

| Outcome | Likelihood |
|---|---|
| Etsy/eBay automated systems pull the listing within days, before sale completes | Moderate to high — bots flag "hitchhiker," "DON'T PANIC," and prop-replica keywords |
| Listing survives, sale completes quietly | Possible, especially if listed ambiguously |
| Cease-and-desist letter | Low |
| Lawsuit | Very low for a single sale, not zero |

The dominant outcome is "listing yanked before it sells, time wasted,
prototype still in your basement." Lawsuits over a single low-dollar sale
are extremely rare; the cost of pursuing one exceeds any damages.

But the goal here was *getting rid of the prototype*, not *getting paid*
specifically. There are cleaner ways to dispose of one finished build:

### Better disposal options (no legal risk)

- **Gift it.** To a fellow fan, a Douglas Adams enthusiast in your
  social circle, a maker friend, or a coworker. Distributing a single
  copy as a personal gift to someone you know is the lowest-risk path
  and is functionally equivalent to "selling for $0." Rights holders do
  not pursue private gifts.
- **Donate to a fan-community auction or raffle.** A local sci-fi con
  charity raffle, a fan-club fundraiser, a Reddit r/HHGTTG raffle. The
  charitable framing doesn't grant a license, but enforcement against
  charity raffles is essentially nil. The optics for the rights holder
  would be terrible.
- **Display it indefinitely.** Bookshelf, office, con table, makerspace
  display case. Costs nothing, dispenses with the "what do I do with
  it" question, and you keep the portfolio piece.
- **Use it as a portfolio piece for paid commission work.** Show it as
  evidence of your prop-build skill; if someone hires you to build
  *something custom they specify*, that's a different transaction with
  different legal posture.

### What to avoid even in a one-time scenario

- Listing it on Etsy or eBay. Even one listing is indexed, scraped, and
  flagged. The most probable outcome is wasted effort.
- Listing it with "Hitchhiker's Guide," "DON'T PANIC," or film-specific
  language anywhere in the description or tags. That's where automated
  enforcement triggers.
- Doing a paid private sale to a stranger via a marketplace platform's
  message system specifically to evade detection. That's not just
  legally identical to a public sale — it adds a small bad-faith
  signal if it ever did get pursued.

### Updated recommendation

- Publish the plans for free under the existing CC BY-NC-SA 4.0 license.
  Risk: low, common practice, fits the project's stated intent.
- **Don't sell the physical prototype.** Gift it, donate it to a fan
  raffle, or keep it as a display piece. The likely outcome of an Etsy
  listing is the listing getting yanked anyway, so the "sell it to
  recover materials cost" dollars probably don't materialize.

## Sources

- [USPTO record for "Hitchhiker's Guide to the Galaxy" — Disney, Serial 78614189, abandoned 2007](https://uspto.report/TM/78614197)
- [USPTO record for "Hitchhiker's Guide to the Galaxy" — Disney, Serial 78979873, abandoned](https://trademarks.justia.com/789/79/hitchhiker-s-guide-to-the-galaxy-78979873.html)
- ["The Hitchhiker's Guide to the Galaxy" — Adams, Douglas, USPTO record](https://uspto.report/TM/74417641/)
- [Phrases from The Hitchhiker's Guide to the Galaxy — Wikipedia](https://en.wikipedia.org/wiki/Phrases_from_The_Hitchhiker's_Guide_to_the_Galaxy)
- [Etsy seller handbook — Fan Art and Fair Use: One Truth and Five Myths](https://www.etsy.com/seller-handbook/article/39402098770)
- [Made Urban — How to Avoid Etsy Copyright Infringement (Disney & Fan Art)](https://www.madeurban.com/blog/how-to-avoid-etsy-copyright-infringement/)
- [Marketing Artfully — How To Avoid Problems With Disney on Etsy](https://marketingartfully.com/avoid-problems-with-disney-etsy-sellers/)
- [Landry Legal PLLC — Etsy and Disney: Legalities of Using Popular Characters](https://landrypllc.com/etsy-and-disney-understanding-the-legalities-of-using-popular-characters-in-your-designs/)
- [Nolo — Can You Legally Sell Fan Art Online?](https://www.nolo.com/legal-encyclopedia/can-you-legally-sell-fan-art-online.html)
- [Harrison Pensa — IP infringement: Handmade items that break copyright](https://www.harrisonpensa.com/ip-infringement-handmade-items-that-break-copyright/)
- [RPF Costume and Prop Maker Community — Copyright problems when selling props](https://www.therpf.com/forums/threads/copyright-problems-when-selling-props.135102/)
- [JustAnswer — Is It Illegal to Sell Movie Prop Replicas?](https://www.justanswer.com/intellectual-property-law/6f17o-illegal-sell-movie-prop-replicas-built-yourself.html)
