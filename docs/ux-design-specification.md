---
stepsCompleted: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13]
inputDocuments:
  - /home/riddler/mental/docs/prd.md
workflowType: 'ux-design'
lastStep: 13
project_name: 'mental'
user_name: 'Riddler'
date: '2026-02-05'
---

# UX Design Specification - mental

**Author:** Riddler
**Date:** 2026-02-05

---

## Executive Summary

### Project Vision

Mental is a cryptographically-verified heads-up poker server where trustlessness replaces blind trust. Every game is mathematically provable—players can download hand histories with embedded cryptographic proofs that prove the shuffle was mathematically fair, cards remained private until showdown, and the server couldn't have manipulated outcomes. This is radical transparency through mathematics, not reputation.

The core innovation isn't cryptographic breakthrough, but practical application of proven peer-reviewed mathematics to solve a market problem no online poker platform currently addresses: giving players mathematical proof they weren't cheated, eliminating the "trust the house" problem entirely.

### Target Users

Mental serves four distinct audiences with very different needs:

**1. Alex Chen (Player) - The Skeptical Casual**
- Serious online poker player who's been burned by rigged games before
- Wants normal poker gameplay without worrying about being cheated
- Needs the cryptography to be *invisible* during play—just plays poker naturally
- Discovers the proof afterward as a confidence moment
- Emotional state: hopeful but skeptical, wants concrete reassurance
- Tech level: Moderate—comfortable with WebAssembly but needs poker-centric framing

**2. Jordan Lee (Professional Auditor) - The Verification Expert**
- Professional player who wants to verify games independently over time
- Downloads multiple hand histories and analyzes proofs with scripts
- Audits games across weeks and months, looking for patterns or anomalies
- Needs clean data formats, bulk operations, and verification documentation
- Values: Mathematical rigor, auditability, long-term record preservation

**3. Sam Rodriguez (Server Operator) - The Pragmatist**
- Technical but not specialized in cryptography
- Wants to deploy on a Linux machine, check logs, retrieve hand histories when requested
- Needs simple deployment process, log-based monitoring, no complex administration
- Values: Simplicity, reliability, standard infrastructure

**4. Maya Patel (Researcher) - The Validator**
- Cryptography expert who audits code and analyzes proofs mathematically
- Publishes validation reports that become authoritative references for other players
- Needs open-source, well-documented cryptographic implementation
- Cares about: Code clarity, algorithm correctness, peer-reviewed foundations

### Key Design Challenges

**1. The Invisibility Paradox**
The cryptography is Mental's competitive advantage, but it must remain *invisible* during play. Players shouldn't experience delays while ZKP proofs generate—poker rhythm matters. Yet after play, the cryptography needs to become *visible* and verifiable. Balancing these opposite requirements is a core UX challenge: transparent technology that doesn't interrupt flow.

**2. Translating Complex Math into Concrete Trust**
For Alex (casual player), "zero-knowledge proof (ZKP)" sounds academic and intimidating. The UX must communicate the emotional truth: *"I played poker and I have mathematical proof I wasn't cheated"*—in simple, tangible terms that don't require understanding the algorithm. The math is real, but the experience shouldn't feel theoretical.

**3. Multi-Level UX for Different Audiences**
Sam needs deployment documentation. Maya needs algorithm specifications. Alex needs simple poker. All using the same system. The UX must serve vastly different needs—from casual player to cryptography researcher—without confusion or bloat.

### Design Opportunities

**1. Make Proof Verification Visual & Intuitive**
Instead of showing dense cryptographic proof strings, hand history downloads could include visual proof verification: charts showing shuffle fairness, action timeline, game flow visualization. Make the math *feel* real without requiring math knowledge. Turn verification into a satisfying discovery moment.

**2. Concrete Trust Moments**
Design specific "trust moments" where the proof becomes tangible. When downloading a hand history, a notification: *"Your cryptographic proof is ready. You can now prove this game was fair."* Make verification feel rewarding, not obligatory.

**3. Simplicity as Competitive Advantage**
The whole system is heads-up only, stateless, no accounts—unusual in poker, but elegant. The UX can celebrate this: "Join in seconds with just a name. Play. Verify. Done." vs. the complexity of traditional platforms. Simplicity itself becomes a feature and trust signal.

**4. Open-Source as User Empowerment**
Instead of treating "open-source code" as a technical requirement, position it as a UX feature: "Audit the code yourself. No black boxes. No trust required." This appeals directly to Mental's core user: the skeptical player who doesn't want to trust anyone.

---

## Core User Experience Definition

### Defining Experience

**The Two-Moment Loop: Normal Poker → Proof Verification**

Mental's defining experience isn't a single moment—it's the seamless transition between two states that together create the unique value proposition:

**Moment 1: Play Normal Poker**
Players experience standard heads-up No Limit Hold'em gameplay. The game is responsive, natural, and engaging. From their perspective, it's just poker. They see hole cards, make betting decisions, watch community cards develop, and complete the hand. No indication of cryptographic overhead, no delays, no strange UI cues. Just poker.

The mental poker protocol works invisibly underneath, securing cards and verifying shuffles through cryptographic communication between client and server. But the player doesn't need to understand or even notice this complexity.

**Moment 2: Get Proof Immediately**
The hand ends, cards are revealed at showdown, and the system immediately presents the hand history with embedded cryptographic proofs. The proof is accessible—downloadable without friction, always available for retrieval later, owned by the player, not locked behind the platform.

The player can verify the proof themselves (or share it with others to verify), and see mathematical evidence that:
- The shuffle was fair and verifiable
- Their cards were genuinely private
- Nothing was manipulated

**The Defining Success Metric:**
If we achieve this loop flawlessly—responsive normal poker + immediately-available proof—then everything else (lobby, operators, auditors) works because the core value is delivered.

### User Mental Model

**Alex (Casual Player) Mental Model:**
- Expectation: "I want to play poker and know for certain I wasn't cheated"
- Current behavior: Plays on regulated platforms, but inherently skeptical of fairness claims
- Mental model before using Mental: "Fairness is claimed by the operator, and I have to trust them"
- Mental model after using Mental: "I have mathematical proof. I own my proof. I verified it myself"

The mental model shift is crucial: from trust-based to proof-based thinking.

**Jordan (Auditor) Mental Model:**
- Expectation: "I want to audit games across time and validate fairness independently"
- Current behavior: Downloads hand histories, analyzes them with scripts, spot-checks patterns
- Mental model: "If I can verify multiple games and they're all mathematically fair, I have authority to recommend this system"

**Sam (Operator) Mental Model:**
- Expectation: "I want to run a poker server that obviously can't cheat"
- Current behavior: Deploys servers, monitors logs, handles player requests
- Mental model: "I'm running code that's mathematically proven to be fair. Players can verify it. I don't have to convince anyone to trust me"

**Maya (Researcher) Mental Model:**
- Expectation: "I want to audit the protocol and validate the cryptographic implementation"
- Current behavior: Reviews open-source code, analyzes proofs, publishes findings
- Mental model: "This is a legitimate cryptographic implementation. I can validate it. I can become the authority on this system's fairness"

### Success Criteria for Core Experience

**Gameplay Success:**
- ✅ Player action → Server response within 500ms (including cryptographic overhead)
- ✅ Game feels as responsive as traditional online poker platforms
- ✅ Zero cryptographic delays visible during betting rounds
- ✅ Player can complete a full hand (pre-flop through showdown) without noticing computational work

**Proof Success:**
- ✅ Hand history with proofs generated within 1 second of showdown
- ✅ Proof downloadable with single click (no authentication required)
- ✅ Hand history persistent and retrievable indefinitely
- ✅ Proof format matches mental poker literature standards (externally verifiable)

**Trust Success:**
- ✅ Player can independently verify proof without platform verification
- ✅ Proof can be shared with cryptographer/researcher who validates it independently
- ✅ Player feels confident: "I have mathematical evidence I wasn't cheated"
- ✅ No lingering skepticism or doubt about fairness

### Novel UX Pattern

Mental's core experience **does not use an established poker platform pattern**—instead, it combines familiar poker UX with a novel cryptographic transparency moment.

**What's Familiar:**
- Lobby with table list (Chess.com, Lichess, GGPoker pattern)
- Heads-up poker gameplay (standard Hold'em rules and UI)
- Showdown revealing cards (traditional poker moment)
- Hand history download (some platforms offer this)

**What's Novel:**
- **Proof as immediate deliverable** rather than historical reference
- **Proof as verifiable evidence** rather than platform claim
- **Cryptographic transparency** replacing operator reputation as trust signal
- **Mathematical certainty** instead of regulatory assurance

The novel aspect isn't the interaction itself—it's the *meaning* of the interaction. Getting your hand history isn't new. Having cryptographic proof embedded in it that you can verify independently *is* new.

**User Education Needed:**
Players don't need to understand zero-knowledge proofs to use Mental. They need to understand one simple concept: "Your hand history includes mathematical proof the game was fair. You can verify it yourself or ask someone else to verify it for you."

### Experience Mechanics: Normal Poker + Proof Loop

**Part 1: Lobby & Join**

1. **Initiation:** Player opens Mental client, sees lobby
2. **Interaction:** Player views available tables, clicks "Join" on a table
3. **Feedback:** Player is immediately seated, sees hole cards, sees opponent name
4. **Completion:** Hand begins; player is ready to act

**Expectation:** <3 clicks from landing page to seated at a table

---

**Part 2: Gameplay (Per-Hand)**

1. **Initiation:** Hand begins with blinds posted
2. **Interaction:**
   - Player sees their hole cards
   - Player makes betting decisions (fold/check/call/bet/raise)
   - Server processes action, broadcasts to opponent within 500ms
   - Community cards appear after each betting round
   - Hidden cryptographic communication: mental poker protocol securing card state
3. **Feedback:**
   - Immediate visual feedback for player actions
   - Pot updates in real-time
   - Current action indicator shows whose turn it is
   - Community cards appear smoothly
4. **Completion:** Final betting round concludes; cards are revealed at showdown

**Expectation:** Game rhythm feels normal; no noticeable cryptographic delays

---

**Part 3: Proof Moment (Game Conclusion)**

1. **Initiation:** Showdown completes; both players' cards revealed
2. **Interaction:**
   - Hand history page appears automatically
   - Proof is generated and embedded in hand history (happens within 1 second)
   - "Download Hand History" button becomes available
   - Player clicks download
3. **Feedback:**
   - Visual confirmation: "Your hand history is ready"
   - Download completes; file is in player's downloads folder
   - Proof is visible in hand history file (JSON showing cryptographic data)
4. **Completion:** Player has their proof; can verify, share, or store

**Expectation:** Hand history is immediately accessible; proof feels like a natural conclusion to the game

---

**Part 4: Verification (Optional, Ongoing)**

1. **Initiation:** Player downloads hand history (immediately after game or anytime later)
2. **Interaction:**
   - Player opens hand history file locally
   - Proof is visible in human-readable form (or downloadable as JSON)
   - Player shares proof with friend/researcher/auditor
   - External validator independently verifies proof
3. **Feedback:**
   - Proof verification succeeds → "This game was mathematically fair"
   - Player gains confidence → "I can prove this was fair"
4. **Completion:** Player becomes advocate (can recommend Mental to others with evidence)

**Expectation:** Verification is easy, proofs are authentic, validation succeeds

---

**Single-Language Stack (C++ Everywhere)**

Mental will use C++ as the unified language across the entire system:
- **Backend:** C++ server implementing mental poker protocol and game logic
- **Client:** C++ compiled to WebAssembly for browser execution
- **Cryptographic computation:** Heavy cryptographic operations run in WebAssembly (C++) for performance

This single-language approach simplifies development, auditing, and allows alternative client builders to work from a unified codebase. The C++ backend and C++ WebAssembly client speak the same protocol language, with the browser as the delivery mechanism.

**Browser-First Delivery**

For MVP, the browser-based WebAssembly client is the reference implementation. This allows:
- Zero installation friction (players just visit a URL)
- Open-source reference clients to be built in other languages
- Automatic updates (players always get latest version on refresh)
- Platform independence (works on any OS with a browser)

Alternative client implementations are possible in future, but the MVP establishes the protocol through a single, clean reference implementation.

**Cryptography at the Protocol Level**

The mental poker protocol operates at the communication layer between client and server. Every game action—shuffle, bet submission, card state management—is cryptographically secured. This is not layered on top; it's fundamental to how the game works. The player doesn't interact with cryptography directly; they play poker. The protocol handles everything.

### Effortless Interactions

**1. Joining a Game (Lobby Experience)**
Players open the client and immediately see a list of available tables. The lobby shows:
- Active tables with seat availability
- Current players (if table has started)
- Simple one-click "Join" action

Success metric: Player is seated and seeing their hole cards within 2-3 clicks, no registration or account creation.

**2. Playing Normally (Invisible Cryptography)**
Players experience standard poker gameplay:
- See their hole cards clearly
- Make betting decisions intuitively (fold, check, call, bet, raise buttons)
- See community cards develop through betting rounds
- Game rhythm feels natural despite underlying cryptographic communication

The mental poker protocol handles card privacy and shuffle verification at the protocol level. From the player's perspective, it's just poker. The cryptographic communication between client and server is invisible—it happens continuously but never interrupts gameplay.

**3. Getting the Proof (Persistent Hand History)**
Hand histories are always available for download:
- Players can download immediately after game concludes
- Players can download any past hand history at any time (they persist indefinitely)
- Same hand history is available whether downloaded immediately or days later
- Single-click download access—no hunting through menus or databases

**4. Auditing Multiple Games (Same Hand History)**
For players like Jordan who verify multiple games:
- Download hand histories (one at a time or in batches)
- Hand history format is machine-readable (JSON with embedded proofs)
- Proof format matches mental poker literature standards
- Scripts can verify proofs independently without server trust

### Critical Success Moments

**Moment 1: Lobby Clarity**
- Player opens Mental client
- Sees list of available tables with clear seat information
- Makes or break: Can they instantly understand "I can sit here and play poker"?
- Success: Player clicks "Join" confidently without confusion

**Moment 2: First Hand Completion**
- Player completes their first game (win or lose doesn't matter)
- Sees showdown where both players' cards are revealed
- Make or break: Does the experience feel like normal poker?
- Success: Player thinks "That felt like poker, and it was fair"

**Moment 3: Proof Discovery**
- Player finishes a game and has an obvious way to get their hand history
- Downloads hand history and opens it locally
- Make or break: Does the proof feel real and verifiable?
- Success: Player can examine the proof, understand it's mathematical evidence, and share it with others to verify

**Moment 4: Protocol Verification**
- For researchers like Maya: examining the protocol, seeing cryptography at work
- Make or break: Is the C++ code clean, auditable, and demonstrating the protocol correctly?
- Success: Researcher can validate that the mental poker protocol is correctly implemented throughout the system

---

## Desired Emotional Response

### Primary Emotional Goal

**"I have proof. I'm in control."**

Mental's core emotional objective is not "I trust the operator" or "I believe the system is fair." It's personal empowerment through verification: players have mathematical evidence in their hands, they control who sees it, they decide if they trust it. This emotional foundation differentiates Mental from every other poker platform that asks players to trust the operator.

### Emotional Journey Mapping

**Discovery (First Contact):**
- **Emotion:** Intrigue with skepticism
- **UX Trigger:** Clean explanation of the concept, no hype, straightforward value proposition
- **Success feeling:** "I understand what this is, and I'm curious to try it"

**Joining a Game (Lobby):**
- **Emotion:** Clarity and readiness
- **UX Trigger:** Available tables are obvious, joining is one click, expectation is clear
- **Success feeling:** "I'm about to play poker with someone real, and I know what to expect"

**Playing the Game (Core Experience):**
- **Emotion:** Normal engagement (poker emotion) + hidden confidence (cryptography working invisibly)
- **UX Trigger:** Normal poker gameplay, zero indication of cryptographic overhead, responsive actions
- **Success feeling:** "This is poker. Nothing weird. It just works."

**Showdown/Game End:**
- **Emotion:** Relief (in the moment) → anticipation (about the proof)
- **UX Trigger:** Cards reveal naturally, game concludes normally, then hand history is obviously available
- **Success feeling:** "My game is over, and I can now prove it was fair"

**Downloading Proof (Trust Moment):**
- **Emotion:** Empowerment and confidence
- **UX Trigger:** Hand history is immediate, downloadable, obviously contains proof
- **Success feeling:** "I have mathematical evidence of fairness in my hands"

**Verifying/Auditing (Deep Engagement):**
- **Emotion:** Rigor, confidence, perhaps delight at finding consistency
- **UX Trigger:** Proofs are understandable, verifiable, match literature standards
- **Success feeling:** "I've independently verified this was fair. I'm now an expert who can validate this for others"

### Micro-Emotions

**Trust vs. Skepticism:**
Trust should feel *earned*, not given. It comes from verification, not design patterns. Players prove fairness themselves (high trust) rather than being told it's fair (low trust).

**Confidence vs. Anxiety:**
Every interaction should reinforce confidence. Anxiety should never occur—players always know how to get their proof, proof is never lost, verification is always possible.

**Simplicity vs. Overwhelm:**
Lobby should feel simple and focused, not feature-heavy. Poker should feel normal, not different from familiar games. Proof should feel accessible, not technically overwhelming.

**Empowerment vs. Helplessness:**
Players must feel ownership of their proof. Proof is always available and never locked behind logins. Unavailable hand histories or inaccessible proofs would be the opposite feeling.

**Pride vs. Anonymity:**
Players should feel pride in playing mathematically fair poker. Games are stateless (no persistent identity), so each session is fresh—but the accomplishment of verified fairness is real and personal.

### Design Implications

**For the Empowerment Emotion:**
- Hand histories must be immediately accessible after games end
- Proofs must be downloadable, never locked behind logins or accounts
- Verification should feel rewarding and natural, not obligatory or technical

**For the Confidence Emotion:**
- Proof should be tangible (downloadable files, not abstract claims)
- The mathematics should speak for itself (no marketing claims needed)
- Share mechanics should let players convince others ("here's my proof, verify it yourself")

**For the Normalcy + Hidden Security Emotion:**
- Lobby and gameplay should look familiar to poker players
- Cryptographic communication should never interrupt flow
- Proof moments should feel natural and expected, not surprising or intrusive

**For the Authority Emotion (Researchers/Auditors):**
- Code should be auditable and clean (clear cryptographic implementation)
- Deployment should be straightforward (simple operations feel trustworthy)
- Operations should feel reliable and predictable

### Emotional Design Principles

**1. Verification is the Reward**
Don't make proof feel obligatory or technical. Make it the satisfying conclusion to a game: "You played fair poker. Here's your proof." Downloading and verifying becomes intrinsically rewarding.

**2. Proof Belongs to the Player**
Hand histories are owned by players, not the platform. Always accessible, never deleted, never trapped behind authentication. Ownership creates emotional investment and trust.

**3. Normal Poker, Extraordinary Assurance**
The game feels like poker. The proof feels extraordinary. The contrast between familiar gameplay and mathematical verification is the emotional power point.

**4. Trust Through Math, Not Reputation**
Every emotional moment should reinforce: "This is proven, not promised." No marketing speak, no trust badges, no appeals to reputation. Just verifiable mathematics.

**5. Simplicity Signals Integrity**
The fewer features, the clearer the purpose. Heads-up only, no accounts, no stats—this simplicity itself communicates integrity. "We focus on one thing: fair poker."

---

## UX Pattern Analysis & Inspiration

### Core Pattern Principles for Mental

Rather than copying patterns from existing poker platforms, Mental's UX should derive from its unique value proposition: cryptographically-verified fairness through transparent mathematics.

**Pattern Philosophy for Mental:**
The most relevant inspiration comes from products that successfully build trust through transparency and clarity, not from traditional poker platforms that rely on reputation and regulation.

### Transferable UX Patterns

**1. Lobby as Gateway (From: Chess.com, Lichess.org, Discord)**

**Pattern:** A clean, immediately-understandable interface showing available options with zero friction to entry.

**Application for Mental:**
- Display available tables with clear information: number of players, stakes (if applicable), game status
- One-click join action that immediately places the player at the table
- No intermediate steps, no confirmation dialogs, no "are you sure?" friction
- **Why this works for Mental:** The lobby is the first impression. It should communicate: "Pick a game and play. That's it."

**2. Proof as Achievement Unlocked (From: Duolingo, achievement systems, GitHub badges)**

**Pattern:** Completing an action triggers a satisfying moment of accomplishment with tangible evidence.

**Application for Mental:**
- After a game ends, the hand history with proof becomes immediately available
- The proof is the "achievement"—visual confirmation that fairness was mathematically verified
- Download action should feel rewarding: "You completed a fair game. Here's your proof."
- **Why this works for Mental:** Makes verification feel like a natural reward, not a technical requirement

**3. Open-Source as Trust Signal (From: GitHub, Linux, academic projects)**

**Pattern:** Transparent code, clear documentation, and community validation build authority.

**Application for Mental:**
- C++ codebase published openly from day one
- Cryptographic implementation matches peer-reviewed literature
- Hand history format is documented and externally verifiable
- **Why this works for Mental:** "Audit it yourself" becomes a trust feature, not a disclaimer

**4. Simplicity Through Constraint (From: iA Writer, Stripe, Unix philosophy)**

**Pattern:** By limiting features to essentials, every design decision serves the core purpose.

**Application for Mental:**
- Heads-up only (no multi-player complexity)
- Stateless sessions (no accounts or persistent identity)
- No leaderboards, stats, or social features
- **Why this works for Mental:** Constraints become features. "We focus only on fair poker" is a powerful positioning

**5. Real-Time Verification Feedback (From: Banking apps showing transaction status, Git showing file permissions)**

**Pattern:** Immediate, tangible feedback that something important has happened correctly.

**Application for Mental:**
- Game state updates happen in real-time (normal poker rhythm)
- Cryptographic proofs are generated and ready immediately after game end
- No waiting or mysterious background processes
- **Why this works for Mental:** Players immediately know: "My proof is ready. My fairness is verified."

### Anti-Patterns to Avoid

**1. Account Creation Friction**
- **Anti-pattern:** Forcing signup, login, email verification before playing
- **Why avoid:** Reduces accessibility; creates friction for skeptical new players; unnecessary given stateless design
- **Mental's approach:** Join with just a name, immediate access

**2. Hidden or Delayed Proofs**
- **Anti-pattern:** Locking hand histories behind logins or requiring navigation to retrieve them
- **Why avoid:** Makes proof feel like a platform feature, not a player-owned asset; undermines emotional goal of "I have proof"
- **Mental's approach:** Immediate download after game, always accessible, no account required

**3. Feature Bloat Around Core Experience**
- **Anti-pattern:** Adding social features, tournaments, stats, challenges to seem more "complete"
- **Why avoid:** Dilutes focus; adds complexity; confuses the value proposition
- **Mental's approach:** One thing, done perfectly: fair heads-up poker

**4. Hiding Complexity Instead of Eliminating It**
- **Anti-pattern:** Making the interface simple while the system underneath is convoluted (false simplicity)
- **Why avoid:** Works until users want to verify or understand deeper; breaks trust
- **Mental's approach:** Simple interface reflects simple architecture (heads-up, stateless, protocol-focused)

**5. Trust Appeals vs. Trust Evidence**
- **Anti-pattern:** "Trust us because we're regulated/audited/licensed" messaging
- **Why avoid:** Doesn't align with Mental's value proposition; asks for trust instead of proving with math
- **Mental's approach:** "Here's the proof. Verify it yourself."

### Design Inspiration Strategy

**What to Adopt Directly:**

1. **Clean Lobby Design** - Simple table list with join action (from Lichess.org, Chess.com)
   - Why: Matches Mental's straightforward value: find a game, join, play
   - Keeps focus on the core action

2. **Proof as Reward Moment** - Achievement-like feeling when proof is ready (from achievement systems)
   - Why: Makes verification feel intrinsically rewarding
   - Supports emotional goal of empowerment

3. **Open-Source Trust Signal** - Published code and clear documentation (from successful open-source projects)
   - Why: Differentiates Mental from platforms built on reputation
   - Supports researcher and auditor user journeys

**What to Adapt:**

1. **Real-Time Game State Updates** - Adapt from traditional poker UX, but optimize for cryptographic latency
   - Modify: Accept that some actions may have slight ZKP delays (2 seconds acceptable for proof generation)
   - Keep: Game rhythm feels natural despite hidden cryptography

2. **Simplicity Principle** - Adapt from minimalist software (iA Writer, Stripe)
   - Modify: Make constraints a feature, not a limitation
   - Apply: "We focus on one thing: proving fair poker"

**What to Avoid:**

1. **Traditional Poker Platforms' Complexity** - Don't replicate features from PokerStars/888poker
   - Why: Adds unnecessary complexity; dilutes unique value
   - Instead: Embrace simplicity as competitive advantage

2. **Trust Appeals and Reputation Marketing** - Don't use licensing/regulation/company size as trust signal
   - Why: Doesn't align with Mental's "proof over promise" philosophy
   - Instead: Let mathematics be the trust signal

3. **Account-Based Systems** - Don't require persistent player identity
   - Why: Unnecessary given stateless design; creates friction; contradicts simplicity principle
   - Instead: Join with name, session expires with game

### Mental's UX Foundation

The design inspiration strategy distills to this: **Mental's UX should feel like open-source software (transparent, auditable, trustworthy) presented through a poker player's interface (simple, engaging, focused).**

This means:
- Lobby should feel as simple as a GitHub repository listing
- Poker should feel as natural as an existing platform (but mathematically proven)
- Proof should feel as accessible as downloading a file (no friction, no barriers)
- Trust should come from inspection, not assertion

---

## Design System Foundation

### Design System Choice

**Minimal CSS + Custom JavaScript Components Wrapping C++ WebAssembly**

Mental's design system prioritizes simplicity, transparency, and performance. Using a minimal CSS approach with custom C++ WebAssembly components and lightweight JavaScript DOM manipulation matches Mental's minimalist philosophy and integrates cleanly with the full C++ architecture.

### Rationale for Selection

**1. Speed & Simplicity**
Minimal CSS and lightweight JavaScript allow rapid development without the overhead of pre-built component libraries or heavy frameworks. This matches Mental's core principle: do one thing (fair poker) exceptionally well, with minimal UI complexity.

**2. C++ WebAssembly Integration**
Minimal JavaScript dependencies mean cleaner integration with the WebAssembly cryptographic core. No heavy component frameworks interfering with high-performance proof generation and verification.

**3. Transparency & Auditability**
Custom components with minimal dependencies are straightforward and auditable. The code is clear, with no "magic" or hidden complexity—important when researchers like Maya are reviewing the entire system.

**4. Performance**
Minimal CSS and JavaScript keep the WebAssembly client lean and fast. No bloated component libraries or heavy frameworks slowing down real-time gameplay.

**5. Alignment with Open-Source Philosophy**
Custom components are easy for alternative client builders to understand and adapt. The design system itself becomes part of the open-source specification that developers can implement in C++ and other languages.

### Implementation Approach

**Frontend Framework:** Minimal JavaScript for DOM manipulation and WebAssembly integration

**Styling Foundation:**
- Minimal CSS for layout and basic styling
- Custom CSS optimized for WebAssembly rendering
- Accessible semantic HTML as foundation

**Component Architecture:**
- Lightweight JavaScript components wrapping C++ WebAssembly modules
- Props-based data flow
- Accessible semantic HTML as foundation
- Minimal styling focused on performance

**Design Tokens (Mental Brand):**

```
Colors:
  - Primary: Deep Blue (trust, cryptography)
  - Success: Green (verified, proof confirmed)
  - Neutral: Gray (clean, minimal)
  - Alert: Orange (attention, important state)

Typography:
  - Heading: System sans-serif, 700 weight
  - Body: System sans-serif, 400 weight
  - Monospace: Code font (for proofs, technical data)

Spacing:
  - Base unit: 4px
  - Standard gaps: 8px, 16px, 24px, 32px

Interactions:
  - Button hover: Subtle color shift, no animation overhead
  - State transitions: Minimal, prefer instant feedback
  - Responsive breakpoints: 320px (mobile), 768px (tablet), 1024px (desktop)
```

### Customization & Accessibility Strategy

**Accessibility First:**
- Semantic HTML structure (buttons are `<button>`, not `<div>`)
- ARIA labels for game state and transitions
- Keyboard navigation for all interactions
- Color contrast compliance (WCAG AA minimum)
- Focus indicators visible for keyboard users

**Responsive Design:**
- Mobile-first approach
- Works on: phones (iOS/Android browsers), tablets, desktops
- Touch-friendly button sizes (48px minimum targets)
- Flexible layouts using CSS grid/flexbox

**Design System as Specification:**
- Component library documented in code
- Storybook or similar for interactive documentation
- Accessible to alternative client builders
- Clear examples for each component

---

## Core User Experience Definition

### Defining Experience

**The Two-Moment Loop: Normal Poker → Proof Verification**

Mental's defining experience isn't a single moment—it's the seamless transition between two states that together create the unique value proposition:

**Moment 1: Play Normal Poker**
Players experience standard heads-up No Limit Hold'em gameplay. The game is responsive, natural, and engaging. From their perspective, it's just poker. They see hole cards, make betting decisions, watch community cards develop, and complete the hand. No indication of cryptographic overhead, no delays, no strange UI cues. Just poker.

The mental poker protocol works invisibly underneath, securing cards and verifying shuffles through cryptographic communication between client and server. But the player doesn't need to understand or even notice this complexity.

**Moment 2: Get Proof Immediately**
The hand ends, cards are revealed at showdown, and the system immediately presents the hand history with embedded cryptographic proofs. The proof is accessible—downloadable without friction, always available for retrieval later, owned by the player, not locked behind the platform.

The player can verify the proof themselves (or share it with others to verify), and see mathematical evidence that:
- The shuffle was fair and verifiable
- Their cards were genuinely private
- Nothing was manipulated

**The Defining Success Metric:**
If we achieve this loop flawlessly—responsive normal poker + immediately-available proof—then everything else (lobby, operators, auditors) works because the core value is delivered.

### User Mental Model

**Alex (Casual Player) Mental Model:**
- Expectation: "I want to play poker and know for certain I wasn't cheated"
- Current behavior: Plays on regulated platforms, but inherently skeptical of fairness claims
- Mental model before using Mental: "Fairness is claimed by the operator, and I have to trust them"
- Mental model after using Mental: "I have mathematical proof. I own my proof. I verified it myself"

The mental model shift is crucial: from trust-based to proof-based thinking.

**Jordan (Auditor) Mental Model:**
- Expectation: "I want to audit games across time and validate fairness independently"
- Current behavior: Downloads hand histories, analyzes them with scripts, spot-checks patterns
- Mental model: "If I can verify multiple games and they're all mathematically fair, I have authority to recommend this system"

**Sam (Operator) Mental Model:**
- Expectation: "I want to run a poker server that obviously can't cheat"
- Current behavior: Deploys servers, monitors logs, handles player requests
- Mental model: "I'm running code that's mathematically proven to be fair. Players can verify it. I don't have to convince anyone to trust me"

**Maya (Researcher) Mental Model:**
- Expectation: "I want to audit the protocol and validate the cryptographic implementation"
- Current behavior: Reviews open-source code, analyzes proofs, publishes findings
- Mental model: "This is a legitimate cryptographic implementation. I can validate it. I can become the authority on this system's fairness"

### Success Criteria for Core Experience

**Gameplay Success:**
- ✅ Player action → Server response within 500ms (including cryptographic overhead)
- ✅ Game feels as responsive as traditional online poker platforms
- ✅ Zero cryptographic delays visible during betting rounds
- ✅ Player can complete a full hand (pre-flop through showdown) without noticing computational work

**Proof Success:**
- ✅ Hand history with proofs generated within 1 second of showdown
- ✅ Proof downloadable with single click (no authentication required)
- ✅ Hand history persistent and retrievable indefinitely
- ✅ Proof format matches mental poker literature standards (externally verifiable)

**Trust Success:**
- ✅ Player can independently verify proof without platform verification
- ✅ Proof can be shared with cryptographer/researcher who validates it independently
- ✅ Player feels confident: "I have mathematical evidence I wasn't cheated"
- ✅ No lingering skepticism or doubt about fairness

### Novel UX Pattern

Mental's core experience **does not use an established poker platform pattern**—instead, it combines familiar poker UX with a novel cryptographic transparency moment.

**What's Familiar:**
- Lobby with table list (Chess.com, Lichess, GGPoker pattern)
- Heads-up poker gameplay (standard Hold'em rules and UI)
- Showdown revealing cards (traditional poker moment)
- Hand history download (some platforms offer this)

**What's Novel:**
- **Proof as immediate deliverable** rather than historical reference
- **Proof as verifiable evidence** rather than platform claim
- **Cryptographic transparency** replacing operator reputation as trust signal
- **Mathematical certainty** instead of regulatory assurance

The novel aspect isn't the interaction itself—it's the *meaning* of the interaction. Getting your hand history isn't new. Having cryptographic proof embedded in it that you can verify independently *is* new.

**User Education Needed:**
Players don't need to understand zero-knowledge proofs to use Mental. They need to understand one simple concept: "Your hand history includes mathematical proof the game was fair. You can verify it yourself or ask someone else to verify it for you."

### Experience Mechanics: Normal Poker + Proof Loop

**Part 1: Lobby & Join**

1. **Initiation:** Player opens Mental client, sees lobby
2. **Interaction:** Player views available tables, clicks "Join" on a table
3. **Feedback:** Player is immediately seated, sees hole cards, sees opponent name
4. **Completion:** Hand begins; player is ready to act

**Expectation:** <3 clicks from landing page to seated at a table

---

**Part 2: Gameplay (Per-Hand)**

1. **Initiation:** Hand begins with blinds posted
2. **Interaction:**
   - Player sees their hole cards
   - Player makes betting decisions (fold/check/call/bet/raise)
   - Server processes action, broadcasts to opponent within 500ms
   - Community cards appear after each betting round
   - Hidden cryptographic communication: mental poker protocol securing card state
3. **Feedback:**
   - Immediate visual feedback for player actions
   - Pot updates in real-time
   - Current action indicator shows whose turn it is
   - Community cards appear smoothly
4. **Completion:** Final betting round concludes; cards are revealed at showdown

**Expectation:** Game rhythm feels normal; no noticeable cryptographic delays

---

**Part 3: Proof Moment (Game Conclusion)**

1. **Initiation:** Showdown completes; both players' cards revealed
2. **Interaction:**
   - Hand history page appears automatically
   - Proof is generated and embedded in hand history (happens within 1 second)
   - "Download Hand History" button becomes available
   - Player clicks download
3. **Feedback:**
   - Visual confirmation: "Your hand history is ready"
   - Download completes; file is in player's downloads folder
   - Proof is visible in hand history file (JSON showing cryptographic data)
4. **Completion:** Player has their proof; can verify, share, or store

**Expectation:** Hand history is immediately accessible; proof feels like a natural conclusion to the game

---

**Part 4: Verification (Optional, Ongoing)**

1. **Initiation:** Player downloads hand history (immediately after game or anytime later)
2. **Interaction:**
   - Player opens hand history file locally
   - Proof is visible in human-readable form (or downloadable as JSON)
   - Player shares proof with friend/researcher/auditor
   - External validator independently verifies proof
3. **Feedback:**
   - Proof verification succeeds → "This game was mathematically fair"
   - Player gains confidence → "I can prove this was fair"
4. **Completion:** Player becomes advocate (can recommend Mental to others with evidence)

**Expectation:** Verification is easy, proofs are authentic, validation succeeds

---

### Experience Principles

**1. Invisibility Then Tangibility**
Cryptography is invisible during play (game flows naturally). After play, it becomes tangible (proof in hand). This contrast is the defining moment.

**2. One Loop, One Purpose**
Everything serves the core loop: play normal poker → get proof. No side quests, no extra features, no distraction. Just the loop.

**3. Proof Ownership**
The proof belongs to the player. Not locked in a platform database, not requiring login, not deleted when the platform shuts down. Downloaded, owned, verifiable independently.

**4. Mathematical Certainty Over Operator Trust**
The proof speaks for itself. No need to trust Mental, the operator, or anyone else. The mathematics is the authority.

**5. Responsive Gameplay Despite Complexity**
The technical complexity is real (mental poker protocol, ZKP proofs), but the user experience is simple. Heavy lifting happens invisibly.

---

## Visual Design Foundation

### Color System

**Primary Palette:**

**Deep Blue (#1F3A93)**
- Role: Primary action, trust, cryptographic/technical association
- Usage: Buttons, links, important CTAs
- Rationale: Signals security, technology, trustworthiness. Associated with scientific credibility and cryptographic communities.

**Neutral Gray (#6B7280)**
- Role: Secondary text, disabled states, dividers
- Usage: Helper text, borders, less important information
- Rationale: Professional and non-distracting. Makes primary elements stand out.

**Success Green (#059669)**
- Role: Verification, proof confirmed, positive states
- Usage: "Proof verified," successful game completion, checkmarks
- Rationale: Psychological association with "confirmed" and "verified." Critical for proof moments.

**Alert Orange (#D97706)**
- Role: Attention, warnings, important notifications
- Usage: Network issues, game state changes, critical alerts
- Rationale: Noticeable without being alarming. Stands out in grayscale contexts.

**Error Red (#DC2626)**
- Role: Errors, disconnections, critical problems
- Usage: Connection lost, invalid actions, game state errors
- Rationale: Universally understood as "problem." Used sparingly.

**White (#FFFFFF) & Black (#111827)**
- Role: Background and text
- Usage: Clean surfaces, maximum contrast readability
- Rationale: Simple, accessible, scientific aesthetic

**Accessibility Compliance:**
- All color combinations meet WCAG AA contrast standards (4.5:1 minimum)
- Don't rely solely on color to convey information (always pair with icons or text)
- High contrast mode supported

### Typography System

**Font Selection:**

**Primary Font: System Sans-Serif Stack**
```
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif
```
- Instantly familiar and performant across platforms
- No custom font loading delays (important for WebAssembly performance)
- Professional and neutral aesthetic
- Excellent accessibility and readability

**Monospace Font: For Cryptographic Data**
```
font-family: "SF Mono", Monaco, "Cascadia Code", "Roboto Mono", Consolas, "Courier New", monospace
```
- Usage: Hand histories, proofs, technical data displays
- Rationale: Monospace communicates "data" and "code." Players expect cryptographic proofs in monospace.

**Type Scale:**

```
Display: 32px / 40px (1.25x line-height) - Page titles, main headings
Heading 1 (h1): 24px / 32px - Section titles
Heading 2 (h2): 20px / 28px - Subsection titles
Heading 3 (h3): 16px / 24px - Component titles
Body: 14px / 20px - Default text content
Small: 12px / 16px - Helper text, captions, metadata
```

**Typography Hierarchy:**

- **Bold (700 weight):** Section headings, important labels, action emphasis
- **Regular (400 weight):** Body text, default state
- **Light (300 weight):** Disabled text, secondary information

**Rationale:**
- 14px body font is readable on all devices without zooming
- 20px line-height provides comfortable reading spacing
- Clear hierarchy helps players quickly understand game state
- Monospace for proofs emphasizes technical authenticity

### Spacing & Layout Foundation

**Spacing Unit: 4px Base (industry standard)**

Standard spacing intervals:
- **4px:** Tight spacing (icon-to-text gaps)
- **8px:** Compact spacing (between inline elements)
- **16px:** Standard spacing (between components)
- **24px:** Generous spacing (between sections)
- **32px:** Large spacing (page sections)

**Layout Principles:**

1. **Maximum Content Width: 1200px**
   - Prevents long lines of text (better readability)
   - Leaves room for sidebars or additional information
   - Responsive: Full width on mobile, constrained on desktop

2. **Grid System: 12-column responsive grid**
   - Mobile: 1 column
   - Tablet (md): 6 columns
   - Desktop (lg): 12 columns
   - Provides flexibility for complex layouts

3. **Card-Based Layout**
   - Game tables are cards
   - Hand history is a card
   - Clear visual separation between distinct information blocks
   - Consistent 8px border-radius on cards for softness

4. **Generous Whitespace**
   - 32px vertical spacing between major sections
   - Empty space helps reduce cognitive load
   - Emphasizes simplicity and clarity

**Component Spacing:**

- **Button padding:** 12px vertical, 16px horizontal (48px minimum touch target)
- **Input field padding:** 12px all sides
- **Card padding:** 24px
- **Section padding:** 32px top/bottom, 24px left/right

### Visual Design Principles

**1. Clarity Over Decoration**
No gradients, no animations for animation's sake. Visual elements serve function, not decoration. The interface feels scientific and trustworthy, not playful.

**2. Accessibility First**
- Minimum 4.5:1 contrast ratio on all text
- Large enough touch targets (48px minimum)
- Clear focus indicators for keyboard navigation
- Don't rely on color alone to communicate state

**3. Responsive by Default**
- Mobile-first approach
- Touch-friendly spacing (larger buttons, more whitespace)
- Flexible layouts that adapt to screen size

**4. Consistent Spacing**
All spacing follows the 4px unit system. No arbitrary margins or padding. Consistency builds trust and professionalism.

**5. Proof Emphasis**
The proof/hand history moments deserve visual emphasis:
- Success green highlights verified states
- Monospace fonts emphasize cryptographic data authenticity
- Ample whitespace around proof download/verification CTAs

---

## Design Direction Decision

### Design Directions Explored

Eight distinct visual and layout approaches were generated and explored:

1. **Minimal & Clean Lobby** - Stripped-down list view for scannable simplicity
2. **Dense Game Grid** - Card-based grid for efficient table discovery
3. **Game Layout - Clean** - Symmetrical game view with classic poker aesthetics
4. **Proof Moment Emphasis** - Green success state celebrating proof verification
5. **Tabbed Interface** - Organized sections via tabs (Lobby, Play, History)
6. **Split Sidebar Layout** - Left sidebar navigation with main content area
7. **Full Game View** - Immersive game experience centered on gameplay
8. **Colorful & Engaged** - Prominent color usage with status bar at top

### Chosen Direction

**Direction 1: Minimal & Clean Lobby + Direction 7: Full Game View**

The winning combination pairs:
- **Lobby Experience:** Minimal, scannable list view (Direction 1)
- **Game Experience:** Full, immersive game view (Direction 7)
- **Proof Moment:** Success green emphasis when proof is ready (Direction 4 element)

This combination serves Mental's core experience perfectly:

**For the Lobby:**
- Clean table list with join buttons
- No visual noise or distracting features
- Players can find and join games in seconds
- Emphasis on simplicity matches Mental's "one thing" philosophy

**For Active Gameplay:**
- Full-screen immersive experience focused on the game
- Header showing stacks, pot, and game state
- Centered play area with players and community cards
- Action buttons obvious and accessible
- Game rhythm feels natural despite hidden cryptography

**For Proof Moments:**
- After game ends, hand history with green success indicator
- Proof download is primary action
- Monospace cryptographic data is visible and verifiable
- Clean aesthetic reinforces trustworthiness

### Design Rationale

**Why This Combination Works:**

1. **Minimalism Across the Board**
   The minimal lobby and focused game view both reinforce Mental's core principle: simplicity through constraint. No unnecessary features, just the essentials.

2. **Two Distinct Contexts, Distinct UX**
   Lobby is about finding (minimal, scannable). Game is about playing (immersive, focused). Each context gets the UX it needs.

3. **Proof Elevation**
   The success green from Direction 4 becomes the moment when players transition from "player" to "auditor." It's a visual statement: "Your proof is ready. You're in control."

4. **Performance & Technical Alignment**
   Minimal interfaces perform better with WebAssembly. No heavy components, just clean HTML/CSS. Responsive and fast.

5. **Accessibility First**
   Clean layouts have better keyboard navigation. High contrast colors are built in. Monospace proofs are scannable.

6. **Professional Trust Signal**
   The minimal aesthetic (no gamification, no flashiness) communicates: "This is serious. This is trustworthy. This is science."

### Implementation Approach

**Lobby View:**
- Simple table list with minimal styling
- Each table shows: name, player count, status
- One-click join action
- No filters, no advanced features (keep for future)
- Mobile-optimized single column layout

**Game View:**
- Header bar with player information (stacks, position)
- Centered play area with both players visible
- Community cards displayed clearly
- Current action indicator shows whose turn
- Action buttons (fold, check, call, bet, raise) always visible
- Game log/history visible on request
- Pot displayed prominently

**Proof Moment:**
- After showdown, green success state appears
- Hand history automatically generated
- Download button primary action
- Monospace proof data visible in structured format
- Proof can be shared or saved locally

**Responsive Behavior:**
- Lobby: Single column on mobile, scales up on tablet/desktop
- Game: Full-screen on mobile, side-by-side players on desktop
- Touch-friendly button sizes (48px minimum)
- Accessible on all screen sizes

### Design System Application

This direction leverages the design system foundation established earlier:

**Color Usage:**
- Deep Blue (#1F3A93) for lobby navigation and primary actions
- Success Green (#059669) for proof moments and verification
- Neutral Gray (#6B7280) for secondary information
- White background for clean, minimal aesthetic

**Typography:**
- System sans-serif for all UI text (clean, performant)
- Monospace for cryptographic proofs and data (authenticity)
- Clear hierarchy: headings for sections, body for content

**Spacing:**
- 4px base unit throughout
- Generous whitespace (32px sections) to reduce cognitive load
- Tight spacing only where needed (icon-text pairs)
- Cards and containers consistently spaced

**Component Usage:**
- Simple buttons with clear states (normal, hover, disabled)
- Card containers for tables and game info
- Clean input fields for player names
- Status indicators using color and text

---

## User Journey Flows

### Journey 1: Alex Chen - Playing Fair Poker (Player Experience)

**Overview:** Alex discovers Mental, downloads the client, joins a game, plays hands naturally, and downloads his cryptographic proof.

**Key Stages:**

**1. Discovery & Setup (5 minutes)**
- Alex finds Mental online
- Downloads/loads WebAssembly client
- Client loads with lobby view

**2. Lobby (Find Opponent)**
- Views available tables (minimal clean list)
- Enters player name
- Clicks "Join" on selected table
- Waits for opponent

**3. Gameplay (15-30 minutes per hand)**
- Sees hole cards clearly
- Makes betting decisions (fold, check, call, bet, raise)
- Responds to actions within 500ms
- Hidden: Mental poker protocol securing cards in background
- Watches community cards develop through betting rounds
- Completes showdown naturally

**4. Proof Moment (Critical Success)**
- Game ends, showdown completes
- Green success state appears: "✓ Your hand is fair"
- Hand history with embedded cryptographic proof appears
- One-click "Download Hand History" button
- Proof shows: cryptographic data, shuffle verification, card privacy

**5. Verification (Optional but Powerful)**
- Alex downloads hand history JSON locally
- Can share with friend/cryptographer
- Friend independently verifies proof
- Confirmation: "This game was mathematically fair"

**6. Return to Lobby**
- Button to play another hand
- Each hand generates its own proof
- Building library of verified games

**Success Metrics for Alex's Journey:**
- ✅ Time to first fair game: <5 minutes
- ✅ Proof generation: <1 second after showdown
- ✅ Cognitive load: Minimal (just plays poker)
- ✅ Trust moment: Proof download is simple and obvious
- ✅ Delight moment: Green success state celebrating fairness

**Error Recovery:**
- Lost connection mid-game → Server saves state, reconnect resumes
- Proof not ready → Show "Proof generating..." with status
- Download failed → Retry button, always available in lobby

### Journey 2: Jordan Lee - Auditing Multiple Games (Power User)

**Overview:** Jordan plays 20+ games over time, then audits them systematically to build authority as a validator.

**Key Stages:**

**1. Gameplay Phase**
- Plays multiple hands across different sessions
- Downloads proof after each game
- Stores hand histories locally
- Goal: Build dataset of 20+ verified games

**2. Audit Phase (Systematic Verification)**
- Option A: Bulk download from lobby
  - Click "Download all past games"
  - Receive .zip with all hand history JSONs
- Option B: API access
  - Write verification script using open-source libraries
  - Call `/table/{id}/history` endpoint
  - Get complete proofs for analysis

**3. Analysis Phase (Expert Investigation)**
- Load hand histories into analysis tool
- Check: Shuffle randomness, card distribution
- Spot-check: Random hands for anomalies
- Verify: All proofs independently with verification script
- Confirm: "All proofs valid ✓"

**4. Authority Building**
- Jordan becomes trusted validator in community
- Can share analysis and proofs
- Recommends Mental to poker circle with personal verification
- Personal authority: "I verified this system myself"

**Success Metrics for Jordan's Journey:**
- ✅ Bulk operations: Download multiple games at once
- ✅ Data access: Machine-readable JSON format
- ✅ Verification: Independent script-based validation possible
- ✅ Authority: Public proof of verification
- ✅ Trust escalation: From player to validator to advocate

**Key Design Elements:**
- Hand history format is standardized and documented
- Proof format matches mental poker literature
- API endpoints support batch operations
- Verification documentation with examples

### Journey 3: Sam Rodriguez - Operating the Server (Operator Experience)

**Overview:** Sam deploys the Mental server, monitors game activity, and handles player support.

**Key Stages:**

**1. Deployment (Simple & Documented)**
- Pulls open-source repo from GitHub
- Reads deployment docs (5-10 minutes)
- Runs: `docker build && docker run`
- Server starts on port 8080
- Opens admin dashboard
- SUCCESS: Server running, games can begin

**2. Monitoring (Ongoing)**
- Checks logs regularly
- Sees entries: "Game created", "Player joined", "Proof generated"
- Dashboard shows simple metrics:
  - Games running: X
  - Total proofs generated today: X
  - Error rate: X%
- Looks for issues in logs

**3. Support (Player Requests)**
- Player: "Can you retrieve hand history #12345?"
- Sam checks logs for game ID
- Finds game in history database
- Retrieves hand history JSON
- Emails to player
- No complex user authentication needed

**4. Maintenance (Updates)**
- New version released
- Sam pulls latest from GitHub
- Runs deployment command again
- No data loss (stateless games)
- Old games still accessible (backward compatible)

**Success Metrics for Sam's Journey:**
- ✅ Deployment: One Docker command, <5 minutes
- ✅ Monitoring: Log-based visibility, clear error messages
- ✅ Support: Simple file retrieval, no user accounts
- ✅ Reliability: Stateless design means no state persistence problems
- ✅ Maintenance: Simple update process, backward compatible

**Key Design Elements:**
- Docker or standard Linux deployment
- Logs tell the complete story of game activity
- Simple metrics dashboard
- Hand histories auto-persisted
- Graceful error handling

---

## Journey Design Patterns

### Navigation Pattern
**Simple Decision Tree at Each State:**
1. Where am I? (Current state clearly indicated)
2. What can I do here? (Available actions obvious)
3. Which action do I want? (Player chooses)
4. What happens next? (Immediate feedback)

### Feedback Pattern
**Color + Text for All States:**
- ✓ **Green (#059669):** Success, proof ready, verification complete
- ⚠ **Orange (#D97706):** Waiting, attention needed, connection issue
- ✗ **Red (#DC2626):** Error, disconnection, critical problem
- **Gray (#6B7280):** Secondary information, disabled states

### Error Recovery Pattern
**Show → Explain → Recover:**
1. Show what went wrong: "Connection lost"
2. Explain what it means: "Your game was saved on the server"
3. Recover path: "Click here to reconnect and resume"

### Progressive Disclosure Pattern
**Show only what matters at each stage:**
- Lobby: Just available tables
- Game: Just your cards and actions
- Proof: Cryptographic data for those interested

---

## Flow Optimization Principles

**1. Minimize Steps to Value**
- Players: 5 minutes to first fair game
- Auditors: One batch operation for all proofs
- Operators: One command to deploy server

**2. Clear Success Indicators**
- Every action gets immediate feedback
- Players know when they've succeeded
- Proofs are obvious, not hidden
- Status always visible

**3. Graceful Degradation**
- Network issues don't destroy games
- Proof not ready? Show progress
- Player disconnects? Game state saved
- Error? Tell user clearly and offer recovery

**4. Authority Through Transparency**
- Jordan builds authority by verifying
- Sam's logs prove fairness
- Proofs speak for themselves
- No need to trust—just verify

**5. Simplicity in Complexity**
- Technical system (cryptography, ZKP) feels simple to users
- Heavy lifting happens invisibly
- UI is minimal and focused
- All complexity hidden from non-technical users

---

## Component Strategy

### Design System Components

Our minimal CSS approach provides a robust foundation of components:
- Buttons in multiple styles and sizes
- Input fields and form elements
- Card and container primitives
- Grid and flex layout utilities
- Comprehensive color utilities aligned with our palette
- Typography scale from 32px display to 12px small text
- Responsive modifiers for mobile-first design
- Accessibility utilities (focus states, sr-only text)

These foundation components handle the baseline UI needs and ensure consistency across the platform.

### Custom Components

Mental requires specialized components for the poker gameplay experience and cryptographic proof verification. These custom components are built using our minimal CSS design system and implement domain-specific logic:

#### 1. Table Component

**Purpose:** Displays the poker table layout with player seats, community cards, pot, and action flow

**Content:**
- 6 seat positions (heads-up uses 2)
- Community card area (5 cards max for Texas Hold'em)
- Pot display and betting information
- Action indicator showing current player

**States:**
- Waiting for players (empty seats shown)
- Game active (cards dealt, betting in progress)
- Showdown (all cards revealed)
- Hand complete (ready to return to lobby)

**Variants:**
- Full table (all information visible)
- Mobile view (stacked, minimized)

**Accessibility:** Semantic table structure with ARIA labels for each seat position, live region announces turn changes, screen reader can navigate table state

#### 2. Card Component

**Purpose:** Visual representation of playing cards with cryptographic integrity

**Content:**
- Card rank (A-K)
- Card suit (♠♣♥♦)
- Card back image (when face-down)
- Card face image (when revealed)

**States:**
- Face up (visible to authorized viewer)
- Face down (hidden from opponent)
- Highlighted (involved in current action)
- Disabled (folded cards, historical)

**Variants:**
- Large (48x72px for hole cards in game view)
- Medium (32x48px for community cards)
- Small (24x36px for hand history)

**Accessibility:** Alt text provides card identity, focus states visible with border highlights, keyboard can navigate through cards in history view

#### 3. Player Status Component

**Purpose:** Shows player information and current action state at the table

**Content:**
- Player name
- Chip stack amount
- Current bet in this hand
- Connection status indicator
- Action button if it's their turn

**States:**
- Active (waiting for action)
- Folded (no longer in hand)
- All-in (no more chips to act)
- Disconnected (connection lost - warning orange)
- Away (sitting out)

**Variants:**
- Expanded (full details, names visible)
- Compact (seat number + chips only)

**Accessibility:** Live region announces when player's turn arrives, status changes (fold, all-in) immediately announced, ARIA labels describe each piece of information

#### 4. Action Button Group

**Purpose:** Provides player with available poker actions and immediate feedback

**Content:**
- Fold button
- Check/Call button (label changes based on action)
- Bet/Raise button with input for amount
- All-in quick action option

**States:**
- Default (available, ready to click)
- Hover (highlighted in deep blue)
- Active (button pressed, awaiting server response)
- Disabled (action not available in current state)
- Loading (processing action on server)

**Variants:**
- Full controls (all buttons visible)
- Quick actions (just Fold/Call/Raise)

**Accessibility:** Button labels clearly state action (not just "Call" but "Call 10 chips"), keyboard shortcuts (F=Fold, C=Call, R=Raise), focus management keeps player aware of available actions

#### 5. Proof Display Component

**Purpose:** Shows cryptographic proof with emphasis on success verification (core emotional moment)

**Content:**
- Green success indicator (✓)
- "Your hand is fair" message
- Proof summary (excerpts of cryptographic data)
- Download hand history button
- Share/verify options
- Direct link to complete proof JSON

**States:**
- Generating (loading spinner with "Proof generating...")
- Ready (success state - green background, prominent display)
- Error (failure state - red background with retry option)
- Downloaded (confirmation message)

**Variants:**
- Modal dialog (prominent full-screen at game end)
- Embedded summary (in lobby after game completes)
- Full proof view (detailed cryptographic data with monospace font)

**Accessibility:** Modal properly manages focus trap, success state announced immediately, proof data readable by screen readers with proper semantic structure, download button clearly labeled

#### 6. Hand History Component

**Purpose:** Displays complete hand record with action sequence and outcome for replay and auditing

**Content:**
- Game ID and timestamp
- Player names and final result
- Blinds amount
- Action sequence (pre-flop, flop, turn, river, showdown)
- Final outcome (winner, pot amount)
- Link to associated cryptographic proof
- Chips won/lost for each player

**States:**
- Summary view (collapsed, shows outcome only)
- Detail view (expanded, shows all actions)
- Comparison view (two hands side-by-side for analysis)
- Full proof view (with cryptographic verification data)

**Variants:**
- Card view (visual layout with community cards shown)
- Text view (compact, machine-readable format for APIs)
- Auditor view (enhanced data including proof verification status)

**Accessibility:** Actions presented as semantic list, keyboard navigation between hands, export buttons provide accessible formats (CSV, JSON), proof verification results announced

#### 7. Lobby List Component

**Purpose:** Shows available games and tables player can join

**Content:**
- Table/Game ID
- Seat availability (X/2 for heads-up)
- Stakes (big blind amount)
- Game status badge
- Join button
- Quick info (how long game has been running)

**States:**
- Empty state (no tables available, encouragement message)
- Loading state (fetching available games)
- List state (multiple tables shown)
- Detail state (expanded view of single game)

**Variants:**
- Card grid view (visual layout)
- Compact list view (row-based, dense)
- Filter view (search by stakes, table ID)

**Accessibility:** Sortable table headers for alternative view, semantic link/button elements, table structure properly marked, live region announces new games appearing

#### 8. Game Status Banner

**Purpose:** Communicates current game state, phase, and any alerts

**Content:**
- Current game phase (Pre-Flop, Flop, Turn, River, Showdown)
- Current player (whose turn)
- Alert messages (connection issues, action timeout)
- Time-sensitive indicators

**States:**
- Normal (gray/neutral, informational)
- Warning (orange - slow connection, timeout approaching)
- Error (red - connection lost, critical issue)
- Success (green - proof ready, hand complete)

**Variants:**
- Full banner (top of screen, all information)
- Compact badge (corner indicator, minimal info)
- Toast notification (temporary alert, auto-dismisses)

**Accessibility:** Status changes announced via ARIA live region, color never sole indicator (always accompanied by text), high contrast meets WCAG AA, dismissible when user action isn't required

### Component Implementation Strategy

**Architecture:**
- Components built as custom JavaScript wrappers around C++ WebAssembly modules
- State management through WebAssembly memory interface and props
- Game logic lives in parent container
- Each component has clear responsibilities

**Design System Integration:**
- All components use our color palette:
  - Deep Blue (#1F3A93) for primary actions and highlights
  - Success Green (#059669) for verification and success states
  - Alert Orange (#D97706) for warnings and attention
  - Error Red (#DC2626) for errors and critical issues
  - Neutral Gray (#6B7280) for secondary and disabled states
- Typography uses system sans-serif for UI, monospace for proofs
- Spacing follows 4px base unit (8px, 16px, 24px, 32px intervals)
- Border radius 8px for cards and containers
- Shadows for depth: small shadow for cards, medium for modals

**Accessibility Baseline:**
- All interactive elements properly labeled
- Keyboard navigation supported throughout
- ARIA live regions announce game state changes
- Focus management keeps user context clear
- Color contrast meets WCAG AA (4.5:1 minimum)
- Semantic HTML (buttons are `<button>`, not `<div>` with click handlers)

**Consistency Principles:**
- Consistent button styling across all components
- Consistent feedback patterns (all actions get immediate response)
- Consistent spacing and alignment using grid/flex
- Consistent focus states for keyboard navigation
- Consistent error messaging and recovery paths

### Implementation Roadmap

**Phase 1 - Critical MVP (Enables Playable Game):**
1. **Table Component** - Core gameplay display, essential for any game
2. **Card Component** - Shows hole cards and community cards, required for decisions
3. **Action Button Group** - Enables player actions, fundamental to gameplay
4. **Game Status Banner** - Communicates game phase and player turn
5. **Proof Display Component** - Fulfills Mental's core promise (fairness proof)

*Dependencies:* These 5 components can be built in parallel. Table and Card integrate closely. Action Button Group depends on Game Status to know valid actions.

**Phase 2 - Supporting Components (Enables Full Feature Set):**
6. **Player Status Component** - Shows who's in play, enhances table awareness
7. **Hand History Component** - Required for auditor journey (Jordan's use case)
8. **Lobby List Component** - Required for player discovery and joining games

*Dependencies:* These 3 can be built after Phase 1. Hand History consumes proof data from Phase 1. Lobby List is independent.

**Phase 3 - Polish & Enhancement (Optional, After MVP):**
- Animated card dealing sequence
- Smooth transitions between game states
- Advanced hand history filters
- Proof comparison tools for auditors
- Mobile-optimized gestures

**Why This Sequencing:**
- Phase 1 enables a playable game (minimal viable product)
- Proof Display in Phase 1 emphasizes Mental's unique value (fair proof)
- Phase 2 enables the auditor use case (Jordan's journey to build authority)
- Phase 3 enhances user experience without blocking core functionality

**Effort Estimation:**
- Phase 1: 2-3 weeks (core gameplay, proof moment)
- Phase 2: 1-2 weeks (supporting features)
- Phase 3: 1-2 weeks (polish, optional enhancements)

**Note:** These estimates are for UX implementation only. Overall project timeline is 8-12 weeks including backend development, integration, and testing as specified in the PRD.

---

## UX Consistency Patterns

### Button Hierarchy & Action Patterns

**When to Use:**
- Fold/Check/Call/Bet/Raise: Game action buttons during active play
- Join: Lobby action to enter a game
- Download: Export proof or history
- Secondary actions: Navigation, help, settings

**Visual Hierarchy:**

**Primary Button** (Player action required)
- Deep Blue (#1F3A93) background
- White text, 16px/500 weight
- 12px vertical / 16px horizontal padding
- Used for: Fold, Call, Raise, Join Game
- State changes:
  - Default: Clickable
  - Hover: Darker blue (#1a2e72)
  - Active/Pressing: 2px inset effect
  - Disabled: Gray (#6B7280), cursor not-allowed

**Secondary Button** (Optional actions)
- Transparent background, Deep Blue text
- 2px Deep Blue border
- Same padding as primary
- Used for: Download History, View Proof, Back
- State changes:
  - Default: Blue text, blue border
  - Hover: Light blue background (#EFF6FF)
  - Active: Dark blue background

**Success Button** (Positive outcomes)
- Success Green (#059669) background
- White text
- Used for: Download Proof (after game complete)
- State changes:
  - Default: Green (#059669)
  - Hover: Darker green (#047857)
  - Active: 2px inset effect

**Danger Button** (Destructive actions - minimal use)
- Error Red (#DC2626) background
- White text
- Used sparingly (disconnect, leave game)

**Button Groups in Poker Actions:**
- Primary action (Call/Bet): Left/largest
- Secondary action (Fold): Right/smallest
- Tertiary action (Raise/All-in): Between or below
- Spacing: 8px between buttons
- On mobile: Stack vertically, each 100% width
- Keyboard accessible: Tab order matches visual left-to-right

**Accessibility:**
- Button labels include amount when relevant: "Call 10 chips" not just "Call"
- Disabled buttons clearly communicate why (gray + aria-disabled)
- Focus visible with 2px blue outline
- Keyboard shortcuts displayed in tooltip (F=Fold, C=Call)

---

### Feedback Patterns (Success, Error, Warning, Info)

**When to Use:**
- Success: Proof generated, hand history downloaded, action confirmed
- Error: Connection lost, action invalid, server error
- Warning: Slow connection, action timeout approaching
- Info: Game waiting for opponent, your turn, proof generating

**Visual Specification:**

**Success Feedback**
- Color: Success Green (#059669)
- Icon: ✓ checkmark
- Used: Proof ready moment (critical emotional design)
- Example: "✓ Your hand is fair" in green banner
- Timing: Appears immediately after game ends
- Duration: Persistent (user must acknowledge or download)
- Sound: Optional subtle chime (accessibility: always offer toggle)

**Error Feedback**
- Color: Error Red (#DC2626)
- Icon: ✗ or exclamation
- Text: Clear explanation + recovery path
- Example: "Connection lost. Your game was saved. Reconnect?"
- Timing: Appears immediately when error occurs
- Duration: Persistent until resolved
- Recovery: Always include action button

**Warning Feedback**
- Color: Alert Orange (#D97706)
- Icon: ⚠ triangle
- Text: Explains situation + prevention
- Example: "Slow connection (450ms). Action may be delayed."
- Timing: Appears when condition detected
- Duration: Until condition clears
- Action: Optional (usually informational)

**Info Feedback**
- Color: Neutral Gray (#6B7280) or Deep Blue
- Icon: ℹ or none
- Text: Helpful context
- Example: "Waiting for opponent to join..."
- Timing: Contextual (shown during wait state)
- Duration: Until state changes
- Action: Usually no action required

**Feedback Placement:**
- Critical game alerts: Top banner (sticky)
- Game status: Below table (Game Status Banner component)
- Proof moment: Center modal (full attention)
- Form errors: Inline below field + red border
- Download confirmation: Toast notification (bottom-right, auto-dismiss after 3s)

**Accessibility:**
- Color contrast meets WCAG AA (4.5:1)
- ARIA live regions announce status changes immediately
- Errors announced as "Alert: [error message]"
- Success announced as "Success: [confirmation message]"
- Users can dismiss/hide persistent messages if needed

---

### Form Patterns

**When to Use:**
- Player name entry (lobby)
- Bet amount input (during game)
- Login/authentication (if implemented)

**Visual Specification:**

**Text Input Fields**
- Border: 1px Neutral Gray (#6B7280)
- Background: White
- Padding: 12px
- Font: System sans-serif, 16px
- Focus state: 2px Deep Blue border, inner shadow
- Placeholder text: Light gray, placeholder text style
- Width: 100% of container (max 400px)

**Labels**
- Font: 14px/500 weight, gray text
- Above field (not floating)
- Bold for required fields
- "Player Name" example

**Validation States**

Error State (invalid input):
- Border: 2px Error Red (#DC2626)
- Message below field: "Name must be 2-30 characters"
- Message text: Error Red
- Error appears on blur or submit attempt
- Keyboard focus moves to field with error

Valid State (passes validation):
- Border: 2px Success Green (#059669)
- Shows only on explicit validation pass
- Not shown immediately (avoid annoying user)

**Input-Specific Patterns**

Player Name Input:
- Type: text
- Min: 2 characters, Max: 30 characters
- No special characters except spaces
- Real-time validation on blur
- Helpful error: "Names must be 2-30 characters"

Bet Amount Input:
- Type: number
- Min: minimum bet amount
- Max: player's available chips
- Keyboard: numeric keypad on mobile
- Real-time validation: "Can't bet more than [X] chips"
- Stepper buttons: + / - for quick adjustment
- Large touch target (48px height)

**Form Submission**

Button placement:
- Below all fields
- Primary button (Deep Blue)
- Label: "Join Game" or "Continue"
- Disabled until form valid
- Shows loading state during submission

Error messaging:
- Inline errors for specific fields
- Summary error at top if multiple issues
- Each error links to corresponding field

**Accessibility:**
- Labels properly associated with inputs (for/id)
- Required fields clearly marked
- Error messages linked via aria-describedby
- Keyboard navigation through fields (Tab)
- Enter submits form from last field
- Form announces when validation completes

---

### Navigation Patterns

**When to Use:**
- Moving between Lobby ↔ Game ↔ History
- Returning to lobby after game
- Viewing hand history
- Accessing different game sections

**Information Architecture:**

**Main Flow:**
```
Lobby
  ├→ [Select Game]
      └→ Game Table
           ├→ [Play hands]
           └→ [Proof generated]
                └→ [Return to Lobby] ← or [View History]
  └→ [History view]
       └→ [Return to Lobby]
```

**Navigation Consistency**

Lobby Navigation:
- Primary action: "Join Game" button
- Secondary: View past games ("Hand History")
- Location: Top bar or left sidebar
- Always accessible: Logo returns to lobby

Game View Navigation:
- No backward navigation (can't leave mid-game)
- Forward only: After showdown, "Return to Lobby" button
- Alternative: View hand history before returning
- Always visible: Game status banner shows game phase

History View Navigation:
- Back to Lobby: Clear button
- Navigation between games: Previous/Next buttons
- Jump to specific game: Game ID search/jump
- Filter options: By date, result, stakes

**Breadcrumb Trail (Optional but helpful):**
- Lobby > Game #1234 (during game)
- Lobby > History > Game #1234 (viewing past game)
- Helps user understand position in hierarchy

**Mobile Navigation Considerations:**

Full screen for game (no competing content):
- Game table fills screen
- Buttons below cards/table
- No top nav bar during active play

Lobby as scroll-able list:
- Games as cards in vertical list
- Join button on each card
- Filter/search at top

History as swipeable cards:
- Swipe left/right between games
- Previous/next buttons also available
- Details expand on tap

**Accessibility:**
- Clear navigation landmarks (nav, main, aside)
- All navigation items are proper links/buttons
- Current page indicated in nav
- Keyboard can access all navigation

---

### Modal & Dialog Patterns

**When to Use:**
- Proof Display (critical moment after game)
- Game Details (before joining)
- Confirmation (leave game, disconnect)
- Alerts (critical errors)

**Visual Specification:**

**Proof Display Modal** (Highest priority)
- Full screen modal with dark overlay (60% opacity)
- Centered white container (90vw max 600px)
- Top padding 20px, bottom padding 40px
- Green success state background (light green tint, #F0FDF4)

Content layout:
- Large ✓ checkmark icon (64px, green)
- "Your hand is fair" heading (24px/bold)
- Proof summary with key data
- Download button (primary green)
- Close button (top-right, X icon)

**Game Details Modal** (Before joining)
- Smaller modal (400px max width)
- Lists: Game ID, Stakes, Players, Time running
- Join button (primary)
- Cancel button (secondary)
- Clear information hierarchy

**Confirmation Dialog** (Destructive actions)
- Minimal modal
- Clear question: "Leave this game?"
- Warning: "Your chips will be lost if you leave during play"
- Buttons: "Stay" (secondary), "Leave" (danger red)
- Escape key cancels

**Accessibility:**

Focus Management:
- Focus trap: Tab cycles within modal
- First focusable element receives focus when opened
- Escape key closes modal
- Focus returns to trigger button when modal closes

Screen Readers:
- Modal announced as "dialog" role
- aria-modal="true"
- aria-labelledby points to modal heading
- Content readable without modal dismissed

Visual:
- Sufficient contrast on modal background
- Close button clearly visible
- All content visible without scrolling (if possible)

---

### Empty States & Loading States

**When to Use:**
- Empty States: No tables available, no hand history
- Loading States: Proof generating, game loading, table list fetching

**Empty States**

No Tables Available:
- Icon: Deck of cards or table illustration
- Heading: "No games available right now"
- Message: "Create a table or check back soon for new games"
- Action: Button to create game (if allowed) or refresh
- Feeling: Neutral, not alarming

No Hand History:
- Icon: Empty document
- Heading: "No hands yet"
- Message: "Join a game and win hands to build your history"
- Action: "Find a Game" button (links to lobby)
- Feeling: Encouraging, progressive

Error State (Server unreachable):
- Icon: Broken connection
- Heading: "Can't reach game server"
- Message: "Check your connection and try again"
- Action: Retry button
- Feeling: Helpful, not blaming

**Loading States**

Proof Generating:
- Spinner animation (rotating circle)
- Text: "Proof generating..."
- Progress indicator if available (though usually <1 second)
- No action available (disabled)

Game Table Loading:
- Skeleton screen (gray placeholder cards)
- Placeholder for table layout
- "Loading table..." text
- Prevents layout shift when content loads

Table List Loading:
- Several skeleton card placeholders
- "Loading games..." text
- After 3 seconds, show message if still loading

**Loading Timelines:**
- <200ms: Show nothing (too quick to matter)
- 200-1000ms: Show spinner with text
- >1000ms: Show spinner + estimated time ("About 5 more seconds")

**Accessibility:**
- Empty states have meaningful alt text for icons
- Loading state announced via ARIA live region
- Screen readers get: "Loading, please wait"
- Users can cancel loading (if applicable) with clear button

---

### Error Recovery Patterns

**When to Use:**
- Connection lost during game
- Invalid action submitted
- Server error responses
- User timeout approaching

**Recovery Model: Show → Explain → Recover**

**Show (immediate):**
- Error banner appears at top
- Color: Error Red (#DC2626)
- Icon: ✗
- Clear error text: "Connection lost"

**Explain (context):**
- Second line explains impact: "Your game was automatically saved on the server"
- Tells user it's not catastrophic
- "Your chips are safe"

**Recover (action):**
- Primary button: "Reconnect" or "Retry"
- Secondary: "Return to lobby" (fallback)
- Keyboard: Enter key triggers retry

**Connection Loss During Game:**
```
Banner: ✗ Connection lost (red)
Message: Your game was saved. Your turn action not received.
Actions: [Reconnect] [Return to Lobby]
Outcome: Reconnect → resume game, OR return and rejoin
```

**Invalid Bet Amount:**
```
Field error: Can't bet more than 500 chips (appears below field)
Field border: Red
Focus: Moves to field
Recovery: User enters valid amount, border turns green, error clears
```

**Proof Generation Failed:**
```
Modal: ✗ Proof generation failed (red)
Message: We couldn't generate your proof. This is rare.
Actions: [Retry] [Contact Support] [Skip (you'll get it later)]
```

**Accessibility:**
- Errors announced immediately via ARIA live
- Focus moves to error or recovery button
- Users can't be "stuck" (always has recovery path)
- Error messages are specific, not generic

---

### Consistency Rules Across All Patterns

**1. Color Consistency**
- Success always green (#059669)
- Error always red (#DC2626)
- Warning always orange (#D97706)
- Primary actions always deep blue (#1F3A93)
- Secondary always outlined/subtle

**2. Spacing Consistency**
- All button padding: 12px vertical, 16px horizontal
- All gap between buttons: 8px
- All field padding: 12px
- All container margins: 16px or 24px (multiples of 8)

**3. Typography Consistency**
- Headings: Bold, all caps sometimes for emphasis
- Body: Regular weight, system font
- Input values: 16px (prevents mobile zoom)
- Monospace for proofs/code: SF Mono, Cascadia Code

**4. Animation Consistency**
- All transitions: 200ms ease-out
- Hover effects: Subtle color change, no spinning
- Loading spinners: 1 second rotation, 3 second complete spin
- Success confirmation: 300ms fade-in with scale

**5. Keyboard Consistency**
- Tab moves through all interactive elements
- Enter/Space activates buttons
- Escape closes modals
- Arrow keys in lists navigate items
- F key shortcuts for poker actions (F=Fold, C=Call, R=Raise)

---

## Responsive Design & Accessibility

### Responsive Strategy

**Desktop Strategy (1024px+):**
Mental on desktop benefits from:
- Wide layout for full table view with all 6 seats visible
- Side navigation/sidebar for game history and settings
- Space for detailed proof verification display
- Multi-column layouts (table + player info + proof)
- Full keyboard support with multiple input methods
- Large readable text and spacious UI

**Tablet Strategy (768px - 1023px):**
Tablets are in transition zone:
- Single column layout with toggle between table and info panels
- Landscape orientation preferred for poker (wider = better table view)
- Touch-optimized buttons (48px minimum height)
- Bottom action buttons (easier for thumb reach)
- Portrait mode shows simplified table
- Gesture support for navigation (swipe to history)

**Mobile Strategy (320px - 767px):**
Mobile is the constraint, requiring:
- Single column, full-screen game view
- Simplified table layout (just my cards + community, minimal seat info)
- Bottom action buttons (fold, call, raise within thumb reach)
- Hamburger menu for secondary actions
- Proof display as full-screen modal
- Vertical stacking for all content
- Touch targets minimum 44x44px (48px for poker actions)

### Breakpoint Strategy

**Recommended Breakpoints for Mental:**

```
Mobile:   320px - 767px   (phones)
Tablet:   768px - 1023px  (tablets, landscape phones)
Desktop:  1024px+         (large screens, desktop)
Large:    1440px+         (ultrawide, multiple monitors)
```

**Mobile-First Approach:** Build for mobile first (constraints are hardest), then enhance for larger screens.

**Key Decision Points:**
- **544px (small tablet):** Stack buttons vertically
- **768px (tablet):** Two-column layout possible
- **1024px (desktop):** Full table with sidebar navigation
- **1440px (large desktop):** Extra whitespace, larger components

### Accessibility Strategy

**Target: WCAG 2.1 Level AA (Industry Standard)**

This level ensures:
- Accessible to users with various disabilities
- Legal compliance in most jurisdictions
- Doesn't require excessive trade-offs with design
- Covers: color blindness, low vision, hearing loss, motor disabilities, cognitive disabilities, temporary disabilities (broken arm, etc.)

**Key Mental-Specific Accessibility Considerations:**

**1. Color Contrast:** All game states visible without color alone
- Success Green + checkmark (not just color)
- Error Red + X icon (not just color)
- Player action indicators use shape/position + color
- Proof success uses "✓ Your hand is fair" (text + icon + color)

**2. Keyboard Navigation:** Full game playable without mouse
- Tab moves through action buttons
- Enter/Space activates buttons
- F=Fold, C=Call, R=Raise shortcuts
- Arrow keys navigate table seats/history
- Escape closes modals

**3. Screen Reader Support:** Game state narrated clearly
- ARIA live regions announce turn changes
- Cards described textually: "Your hole cards: Ace of Spades, King of Hearts"
- Proof ready announced: "Success: Your hand is fair. Proof ready for download."
- Game phase communicated: "Current phase: Flop. Betting round in progress."

**4. Touch Target Sizes:** Minimum 44x44px, preferably 48x48px
- Fold/Call/Raise buttons: 48px height on mobile
- Card tap areas: 48px minimum
- Join Game buttons: 48px height
- Meets WCAG AAA standards for touch targets

**5. Focus Indicators:** Clear visible focus for keyboard users
- 2px Deep Blue outline around focused elements
- Outline offset 2px to avoid covering content
- Remains visible on all interactive elements
- Keyboard tab order matches logical visual flow

**6. Motion & Animation:** Respect user preferences
- Provide prefers-reduced-motion support
- Animations are decorative, not essential
- Can disable animations for users with vestibular disorders
- Proof confirmation animation respects reduced-motion

**7. Form Accessibility:** Inputs fully accessible
- Player name input: Label clearly associated
- Bet amount: Label associated, validation announced
- Errors appear inline with aria-describedby
- Field-level error messages in red + text
- Required fields marked with aria-required

### Testing Strategy

**Responsive Testing Plan:**

**Device Testing (Real Hardware):**
- iPhone SE/11/14 (320-430px widths)
- iPad (768px landscape)
- Desktop monitor (1440px+)
- Chrome DevTools device emulation (fallback)

**Browser Testing:**
- Chrome 120+ (modern features)
- Firefox 121+ (compatibility)
- Safari 17+ (iOS compatibility)
- Edge 121+ (Windows compatibility)

**Network Performance Testing:**
- 4G (typical mobile): Proof generation <1s
- 3G (slow): Game loads with progress indicator
- Offline: Graceful error, reconnect prompt

**Accessibility Testing (Automated + Manual):**

Automated Tools:
- Axe DevTools (Chrome extension)
- WebAIM WAVE (accessibility checker)
- Lighthouse (Chrome DevTools)

Manual Testing:
- Keyboard-only navigation (no mouse)
- Screen reader testing:
  - NVDA (Windows, free)
  - JAWS (Windows, premium)
  - VoiceOver (Mac/iOS native)
- Color blindness simulation (Coblis app)
- Zoom testing (200% text zoom, page zoom)
- Focus visible testing (all interactive elements)

**User Testing with Real Disabilities:**
- Include users with color blindness
- Include keyboard-only users
- Include screen reader users
- Include users with fine motor difficulties
- Real-world usage patterns matter more than spec compliance

### Implementation Guidelines

**Responsive Development Best Practices:**

**1. Mobile-First CSS:**

Start with mobile styles, enhance for larger screens:
```css
/* Base mobile styles */
.button { width: 100%; padding: 12px; }

/* Tablet enhancement */
@media (min-width: 768px) {
  .button { width: auto; }
}

/* Desktop enhancement */
@media (min-width: 1024px) {
  .button-group { display: flex; gap: 8px; }
}
```

**2. Flexible Units:**
- Use rem for font sizes (relative to 16px base)
- Use % for widths (responsive to container)
- Use em for padding/margins (scales with text)
- Avoid hard-coded px except for very small elements
- Use max-width for readable line length (600-800px for text)

**3. Touch-Friendly Design:**
- 48px minimum tap targets
- 8px spacing between adjacent buttons
- No hover-required interactions (mobile has no hover)
- Gesture support (swipe, pinch) enhance but don't require
- Long-press shows tooltip/help

**4. Image Optimization:**
- Serve scaled images for device size
- Use WebP with JPEG fallback
- SVG for icons (scales perfectly)
- Lazy load images below fold
- Optimize for 4G network speed

**Accessibility Implementation Best Practices:**

**1. Semantic HTML:**

Use proper elements, not divs:
```html
<!-- Good -->
<button>Fold</button>
<label for="bet-amount">Bet Amount</label>
<input id="bet-amount" type="number">

<!-- Avoid -->
<div onclick="fold()">Fold</div>
<div>Bet Amount</div>
<div contenteditable>amount</div>
```

**2. ARIA Labels (When HTML Not Enough):**

Add context for screen readers:
```html
<!-- Icon button needs label -->
<button aria-label="Download proof">
  <svg><!-- download icon --></svg>
</button>

<!-- Complex game state -->
<div aria-live="polite" role="status">
  Waiting for opponent...
</div>
```

**3. Focus Management:**

Help users navigate with keyboard:
```html
<!-- Skip to main content link (first focusable) -->
<a href="#main" class="sr-only">Skip to game</a>

<!-- Modal traps focus -->
<dialog role="dialog" aria-labelledby="modal-title">
  <h2 id="modal-title">Your hand is fair</h2>
</dialog>
```

**4. Color Contrast Verification:**
- Text on background: 4.5:1 minimum (AA)
- Large text (18px+): 3:1 minimum
- UI components (borders, icons): 3:1 minimum
- Test with WebAIM Contrast Checker

**5. Keyboard Support Checklist:**
- Can Tab through all interactive elements? ✓
- Logical Tab order (left-to-right, top-to-bottom)? ✓
- All button actions work with Enter/Space? ✓
- Modal closeable with Escape? ✓
- Form submittable with Enter? ✓

### Responsive Layout Specifications

**Mobile (320px - 767px):**
- Single column layout
- Full-width buttons (100% minus padding)
- Bottom navigation or hamburger menu
- Game table simplified (just hole cards visible)
- Card display: 2 columns (hole cards side by side)
- Action buttons: Full width, stacked vertically

**Tablet (768px - 1023px):**
- Two-column layout (landscape)
- Single column (portrait)
- Table visible with 4-5 seats
- Side panel for player info or history
- Buttons can arrange horizontally
- Landscape mode optimized for game play

**Desktop (1024px+):**
- Three-column layout (table + info + proof)
- Table shows all 6 seats comfortably
- Sidebar navigation on left
- Right panel for stats/history
- Proof modal centered on screen
- Generous spacing and readable text

### Accessibility Compliance Checklist

Before launch, verify:
- ✓ WCAG 2.1 Level AA automated testing passes
- ✓ Manual keyboard navigation works
- ✓ Screen reader testing with NVDA/VoiceOver/JAWS
- ✓ Color contrast meets 4.5:1 standard
- ✓ Touch targets minimum 44x44px
- ✓ Focus indicators visible on all interactive elements
- ✓ Form labels properly associated
- ✓ Error messages clear and recovery path available
- ✓ Motion respects prefers-reduced-motion
- ✓ Proof success state not color-only indicator
- ✓ No auto-playing sounds or videos
- ✓ Time-based content has pause/resume controls

---


