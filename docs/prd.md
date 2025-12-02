---
stepsCompleted: [1, 2, 3, 4, 6, 7, 8, 9, 10, 11]
inputDocuments: []
workflowType: 'prd'
lastStep: 11
project_name: 'mental'
user_name: 'Riddler'
date: '2025-12-01'
---

# Product Requirements Document - mental

**Author:** Riddler
**Date:** 2025-12-01

## Executive Summary

### Vision

Mental is a heads-up poker server that delivers cryptographically-verified fair play for online poker players. Using mental poker algorithms, the system guarantees fair shuffles and real-time verification of game integrity—eliminating the possibility of server-side collusion or card manipulation. Players can mathematically prove they weren't cheated, with zero trust required in the server operator.

### What Makes This Special

**Trustless Verification:** Unlike traditional poker platforms where players must trust the operator, Mental enables players to independently verify that:
- The shuffle is mathematically fair and verifiable in real-time
- No cards can be exposed until showdown
- The server cannot manipulate outcomes or collude with players

**Open-Source Client:** The client is fully open-source, allowing players to audit the code, verify correctness, or build their own implementation. This eliminates hidden vulnerabilities or backdoors.

**Heads-Up Only, By Design:** The 2-player constraint is intentional—it's the only way to mathematically guarantee no collusion. This is a feature, not a limitation.

**Cryptographic Guarantee:** Mental poker algorithms provide mathematical proof of fair play, not reliance on audits or reputation.

## Project Classification

**Technical Type:** API Backend with Open-Source Client

The core is a poker server exposing cryptographic game protocol endpoints. The open-source reference client is a developer tool that enables players to participate with confidence.

**Domain:** Scientific / Cryptography

This is cryptographic protocol implementation with game theory foundations. The domain complexity is **high** due to:
- Mental poker algorithm implementation and verification
- Real-time cryptographic proof generation
- Game state management under cryptographic constraints
- Security analysis requirements

**Complexity Level:** High

**Implications:**
- Requires deep cryptographic expertise for implementation
- Needs formal verification of protocol correctness
- Security audit critical before production
- Performance optimization needed for real-time verification

## Success Criteria

### User Success

Players successfully use Mental when they:
- Complete a full heads-up poker game with normal poker gameplay experience
- Have mathematical proof that the shuffle was fair and verifiable in real-time
- Know with certainty that no cards were exposed before showdown
- Can independently verify the game integrity after play concludes

A player's success moment is when they finish a game and can confirm: *"I played poker and I have mathematical proof I wasn't cheated. It was impossible to rig this game."*

### Business Success

Mental succeeds when:
- The system reliably serves fair, secure poker games to players who demand integrity
- Players trust the system because it's mathematically impossible to cheat
- The platform remains available and performs to the limits of ZKP technology
- Open-source client enables players to audit the code and verify correctness themselves

Success is measured by the existence and reliability of the system, not by scale or revenue. The mission is integrity.

### Technical Success

The system succeeds technically when:
- Mental poker algorithm is correctly implemented and cryptographically sound
- Zero-knowledge proofs generate and verify reliably during gameplay
- Game state remains cryptographically secure throughout the entire play session
- Performance is optimized within ZKP constraints (not compromising on fairness for speed)
- Security audit validates the system is immune to cheating vectors

### Measurable Outcomes

- ✅ Games can be played and completed without players noticing the cryptography
- ✅ Shuffle fairness is verifiable in real-time or post-game
- ✅ 100% of players can independently verify they weren't cheated
- ✅ Zero successful attacks or cheating exploits detected
- ✅ Open-source client passes player audits for correctness

## Product Scope

### MVP - Minimum Viable Product

**Core Requirements:**
- Heads-up (2-player) poker game with mental poker algorithm
- Fair shuffle with real-time ZKP proof generation
- Card dealing, betting, and showdown workflow
- Cryptographic guarantee that cards are hidden until appropriate game phase
- Server-side game logic with open-source reference client
- Post-game verification: players can prove the game was fair

**Player Experience:**
- Join a game and play with normal poker interaction patterns
- Experience responsive gameplay within ZKP performance limits
- View real-time verification that shuffle is fair
- Complete showdown and independently verify game integrity

**Technical Deliverables:**
- Mental poker algorithm implementation
- ZKP proof system for shuffle and card state
- Server API endpoints for game protocol
- Open-source client implementation
- Documentation for players/developers to audit or build clients

### Growth Features (Post-MVP)

- Performance optimization to reduce ZKP verification latency
- Enhanced UI for visualizing cryptographic verification
- Game replay and audit tools for players
- Extended poker variants (cash games, tournaments) if feasible
- Community contributions to client implementations

### Vision (Future)

- Mental becomes the recognized standard for mathematically fair poker
- Academic validation and security audits establish it as gold standard
- Ecosystem of independently-built clients proves trustlessness
- Foundation for fair-play gaming in other domains beyond poker

## User Journeys

### Journey 1: Alex Chen - Playing Fair Poker for the First Time

Alex is a serious online poker player who's been burned by rigged games before. He's heard rumors about Mental—a poker game where the shuffle is mathematically guaranteed to be fair. Skeptical but curious, he searches for Mental online and finds the website with clear documentation explaining the mental poker algorithm.

He downloads the browser-based Mental client (written in WebAssembly for speed) and creates a simple session. Within seconds, he's connected to the Mental server and can see a list of available games. He joins a heads-up game with another player, Sarah.

As the game begins, Alex experiences normal poker—he sees his hole cards clearly, can make betting decisions naturally. What's different is subtle but powerful: behind the scenes, cryptographic proofs are being generated to prove the shuffle was fair and his cards remain private until showdown. Alex doesn't need to understand the math; he just knows it's happening.

During play, Alex bets aggressively with K-Q and wins the hand. At showdown, the system reveals both players' cards. The moment of truth arrives: Alex downloads the hand history for this game. He opens it and sees the cryptographic proof embedded in the history—mathematical evidence that:
- The shuffle was fair and verifiable
- His cards were genuinely private until showdown
- Nothing was manipulated

Alex shares the hand history with a cryptographer friend who validates the proofs independently. His friend confirms: the game is mathematically sound. For the first time in years, Alex played poker knowing with absolute certainty he wasn't being cheated.

**Requirements This Journey Reveals:**
- Browser-based client with WebAssembly for responsive gameplay
- Clear mental poker algorithm documentation for players
- Real-time game state management (dealing, betting, showdown)
- Hand history download with embedded cryptographic proofs
- Proof format that matches mental poker literature standards
- Server connection and game session management

### Journey 2: Jordan Lee - Verifying Multiple Games Over Time

Jordan is a professional player who wants to use Mental for serious poker. After his first successful game with Alex, he plays another game, then another. Over a week, he accumulates 20 hand histories from Mental games.

Jordan decides to do a deeper audit. He downloads all 20 hand histories and writes a simple script (using the open-source specifications) to verify every single proof independently. He spot-checks random games, looking for any anomalies in the shuffle patterns or card distributions. Everything checks out perfectly—mathematically sound on every hand.

Jordan now recommends Mental to his poker circle. They start playing regularly. Each player can download their own hand histories and verify the proofs themselves. No trust in Jordan, no trust in the server operator—just mathematical verification.

**Requirements This Journey Reveals:**
- Hand history storage and retrieval for all games played
- Cryptographic proof format that's parseable and verifiable by external tools
- Clear documentation of proof verification methodology
- Game state preservation for historical analysis
- Support for multiple games/sessions per player

### Journey 3: Sam Rodriguez - Operating the Mental Poker Server

Sam decides to run their own Mental poker server. They pull the open-source repository, follow the deployment documentation, and run the web server on a simple Linux machine. The server starts successfully and begins accepting game requests.

During the first week of operation, Sam periodically checks the server logs to monitor game activity. They see entries like:
- Game sessions created
- Players connecting and disconnecting
- Hands completed
- No errors or anomalies

A player emails Sam asking for help retrieving an old hand history. Sam checks the server logs, confirms the game occurred, and provides the player with the hand history file. The player verifies the proofs independently and confirms everything is correct.

Months later, a security researcher audits the Mental codebase and publishes a report confirming the cryptographic implementation is sound. Sam updates to the latest version (a minor performance optimization) following the standard deployment process.

**Requirements This Journey Reveals:**
- Simple web server deployment (Docker or standard process)
- Log-based monitoring for game activity and errors
- Hand history persistence and retrieval
- Support for basic server administration tasks
- Simple update/deployment process
- No complex user management (players use the client directly)

### Journey 4: Maya Patel - The Skeptical Researcher

Maya is a cryptography researcher who wants to validate that Mental actually delivers on its fairness promise. She reads the open-source code, reviews the mental poker algorithm implementation, and downloads several hand histories to analyze the proofs.

After deep review, Maya publishes a technical validation report confirming:
- The mental poker algorithm is correctly implemented
- The cryptographic proofs are mathematically sound
- The shuffle is genuinely unpredictable
- Cards are genuinely private until showdown

This report becomes the authoritative reference that new players trust. When players ask "Is this actually fair?", the answer is: "See Maya's technical validation—it's been independently verified."

**Requirements This Journey Reveals:**
- Clean, auditable source code with clear cryptographic implementation
- Comprehensive technical documentation of the algorithm
- Hand history format that supports detailed cryptographic analysis
- Clear specification of the mental poker protocol
- Performance characteristics and security properties documented

## Journey Requirements Summary

The four journeys reveal these core capability areas:

**For Players:**
- Browser-based client with WebAssembly rendering
- Seamless game joining and session management
- Normal poker gameplay experience (dealing, betting, showdown)
- Real-time cryptographic proof generation (transparent to player)
- Hand history download with embedded proofs
- Proof format matching mental poker literature standards

**For Server Operation:**
- Simple web server deployment
- Game state management and persistence
- Hand history storage and retrieval
- Log-based monitoring
- No complex administration interface needed

**For Code Auditors/Validators:**
- Open-source cryptographic implementation
- Clear mental poker algorithm documentation
- Hand history format that supports proof verification
- Specification document for the protocol
- Performance benchmarks and security analysis

**Cross-Cutting:**
- Zero trust architecture (mathematical proof, not reliance on operator)
- Stateless game sessions (players don't need accounts)
- Simple, focused scope (heads-up only, no collusion scenarios)

## Innovation & Novel Patterns

### Detected Innovation

Mental's innovation is not in cryptographic breakthrough, but in practical application of proven peer-reviewed mathematics to solve a real market problem that no online poker platform currently addresses:

**The Problem No One Has Solved:**
Every online poker platform relies on players trusting the operator. Regulatory licensing, third-party audits, and company reputation are the only assurances players have. Despite this, players regularly encounter:
- Suspected collusion between players and operators
- Skepticism about "rigged" shuffles
- No way to mathematically verify fairness

**Mental's Novel Approach:**
Rather than asking players to trust the operator, Mental makes trust irrelevant. By publishing complete hand histories with full cryptographic details, players can:
- Independently verify every shuffle was mathematically fair
- Audit games weeks, months, or years later
- Share proofs with cryptographers or researchers
- Build alternative clients using the same proven algorithms

The innovation is in **radical transparency through mathematical proof**, not in cryptographic novelty.

### Competitive Landscape

**Existing Online Poker Platforms:**
- PokerStars, 888poker, GGPoker: Regulated platforms relying on audits and licensing
- No platform currently publishes verifiable cryptographic proofs of shuffle fairness
- Players must trust the operator's integrity

**Mental's Unique Position:**
- Only platform where mathematical certainty replaces operational trust
- Only platform where all games are permanently auditable
- Only platform with open-source client enabling independent verification
- Eliminates the "trust the house" problem entirely

### Validation Approach

The innovation is validated through:

1. **Peer-Reviewed Algorithm Foundation**
   - Mental poker algorithm sourced from published, peer-reviewed academic papers
   - No novel cryptography (reduces security risk)
   - Established mathematical foundation

2. **Hand History Auditability**
   - Every hand published with complete cryptographic details
   - Cryptographers can independently verify shuffle fairness
   - Long-term validation (games verifiable years later)

3. **Open-Source Client**
   - Players can audit implementation
   - Researchers can validate the system end-to-end
   - Community-driven validation replaces corporate claims

4. **Proof of Concept Validation**
   - Early adopters can verify small games
   - Researchers can publish validation reports
   - Network effects build as more people verify and trust the system

### Risk Mitigation

**Risk: Performance Issues Make Gameplay Unacceptable**
- Mitigation: Build WebAssembly client optimized for real-time ZKP
- Fallback: If ZKP proofs too slow, publish proofs post-game instead of real-time
- Validation: Beta test with actual poker players for UX acceptance

**Risk: Cryptographic Implementation Contains Flaw**
- Mitigation: Use established, peer-reviewed algorithms (not novel crypto)
- Mitigation: Open-source code for community review
- Fallback: Security audit by recognized cryptography firm before production
- Validation: Researchers publish formal verification reports

**Risk: Market Demand Is Unclear**
- Mitigation: Start with proof-of-concept among poker enthusiasts and cryptography community
- Validation: Measure player adoption and engagement metrics
- Fallback: Pivot to licensing the technology to existing platforms

**Risk: Alternative Clients May Introduce Vulnerabilities**
- Mitigation: Publish clear specification and reference implementation
- Mitigation: Documentation explaining cryptographic guarantees
- Fallback: Community maintains list of "verified client implementations"

## API Backend Specific Requirements

### Project-Type Overview

Mental is an API Backend system that exposes cryptographic game protocol endpoints. The architecture prioritizes simplicity and correctness of the protocol over feature richness. The server manages game sessions, enforces game rules, generates cryptographic proofs, and maintains no persistent player data.

### Core API Endpoints

**Game Session Management:**
- `POST /table` - Create a new poker table (returns table_id)
- `GET /table/{table_id}` - Get table status (seats available, players, game state)
- `POST /table/{table_id}/join` - Join a table with player name (returns player_id, session_token)
- `POST /table/{table_id}/leave` - Leave a table

**Game Play Endpoints:**
- `GET /table/{table_id}/game` - Get current game state (hole cards for authenticated player, community cards, betting round)
- `POST /table/{table_id}/game/action` - Submit player action (fold, check, call, bet, raise)
- `POST /table/{table_id}/game/showdown` - Reveal cards and complete hand
- `GET /table/{table_id}/history` - Retrieve complete hand history with cryptographic proofs (downloadable)

**Server Status:**
- `GET /health` - Server status and game protocol version

### Authentication & Session Model

**No Persistent Authentication:**
- Players join by table_id and can use any name
- Each session generates a unique session_token for the duration of the table
- No login, no accounts, no password
- No player data persists after session ends

**Session Constraints:**
- Session token valid only for the current table
- Player identity verified only within session scope
- No cross-session player tracking

### Data Formats

**Request/Response Format:** JSON for all endpoints

**Game State Representation:**
```json
{
  "table_id": "abc123",
  "players": [
    {"player_id": "p1", "name": "Alex", "stack": 1000, "position": "button"},
    {"player_id": "p2", "name": "Jordan", "stack": 1000, "position": "small_blind"}
  ],
  "game_state": {
    "round": "pre_flop",
    "community_cards": [],
    "pot": 150,
    "to_act": "p1",
    "hole_cards": { "p1": ["AH", "KD"] }
  }
}
```

**Hand History Format:**
- Complete game log with all actions and card reveals
- Embedded ZKP proofs for shuffle verification (format matching mental poker literature)
- Downloadable as JSON for external verification

### Rate Limiting & Access Control

**No Rate Limiting:**
- API is open to anyone
- Constraint is table availability, not API rate limits
- Any player can join any available seat

**DoS Protection:**
- Table creation may require minimal rate limiting (prevent table spam)
- Action submissions rate-limited to prevent network abuse during gameplay
- Simple per-connection rate limits sufficient

### Error Handling

**Error Response Format:**
```json
{
  "error": "error_code",
  "message": "Human readable message",
  "status": 400
}
```

**Common Error Codes:**
- `table_not_found` - Table doesn't exist
- `table_full` - No seats available
- `invalid_action` - Action not legal in current game state
- `not_your_turn` - Submitted action when not active player
- `session_expired` - Session token invalid or expired

### Versioning Strategy

**Automatic Updates via Browser:**
- Web-based client automatically loads latest version on refresh
- No versioning headers or content negotiation needed
- Server handles protocol evolution through backward compatibility when possible

**Protocol Evolution:**
- Major changes documented in API specification
- Reference client always supports current protocol version
- Future: versioning strategy if alternative clients diverge

### Implementation Priorities

**MVP Phase (Phase 1):**
- Focus on correct mental poker algorithm implementation
- Ensure cryptographic proofs generate and verify correctly
- Implement core game endpoints for 2-player heads-up
- Prioritize correctness over optimization

**Post-MVP Performance Optimization (Phase 2):**
- Optimize ZKP proof generation for faster gameplay
- Cache frequently-used cryptographic computations
- WebAssembly client performance tuning

**Features for Future Versions (Phase 3+):**
- Extended game variants
- Performance monitoring dashboard
- Player reputation system (optional, doesn't persist between sessions)

### Security Considerations

**Cryptographic Integrity:**
- All game state cryptographically secured (mental poker algorithm constraints)
- Proofs generated server-side, verified client-side and by auditors
- No shortcuts or trust-based security

**No Player Data Persistence:**
- Eliminates data breach risk
- No user database to protect
- Privacy by architecture (no data to steal)

**Open-Source Audit:**
- All cryptographic code open-source for community review
- Security audit recommended before production deployment

## Project Scoping & Phased Development

### MVP Strategy & Philosophy

**MVP Approach:** Problem-Solving MVP

Mental's MVP focuses on solving the core problem: delivering cryptographically-verified fair poker with mathematical proof that players weren't cheated. Rather than building comprehensive features, the MVP delivers the essential experience that validates the core innovation.

**MVP Rationale:**
- The core innovation (trustless verification through published proofs) must work flawlessly
- Additional features (accounts, stats, multiple variants) don't add to core value
- Lean scope de-risks the most critical assumption: ZKP performance in real-time play
- Market validation comes from proof-of-concept, not feature breadth

**Resource Requirements:**
- Core team: 2-3 engineers (cryptography, backend, frontend)
- Estimated timeline: 8-12 weeks
- Key expertise: Cryptographic protocol implementation, game state management, WebAssembly optimization

### MVP Feature Set (Phase 1)

**Core User Journeys Supported:**
1. **Player's First Game** - Player discovers Mental, plays fair poker, verifies proof
2. **Multi-Game Auditor** - Player verifies multiple games independently
3. **Server Operation** - System runs reliably with log-based monitoring
4. **Cryptographer Validation** - Researcher audits code and proofs

**Must-Have Capabilities:**

*Player Experience:*
- Browse available tables and join with any name (no account)
- Play complete heads-up No Limit Hold'em game
- See game state naturally (hole cards, community cards, betting)
- Download hand history after game ends
- Verify cryptographic proofs in hand history

*Server/Protocol:*
- Mental poker algorithm correctly implemented
- Real-time ZKP proof generation for shuffle verification
- JSON API endpoints for game management
- Hand history persistence and retrieval
- Stateless session management (no persistent player data)

*Client:*
- Browser-based interface (responsive design)
- WebAssembly for responsive proof verification display
- Open-source reference implementation
- Clear documentation for alternative client builders

*Deployment:*
- Simple web server deployment
- Log-based monitoring
- No complex infrastructure

### Post-MVP Features

**Phase 2 (Post-MVP Growth - Weeks 13-24):**

*Performance & UX:*
- ZKP proof generation optimization
- Faster proof verification in client
- Enhanced UI showing real-time verification
- Performance monitoring and metrics dashboard

*Scalability:*
- Multiple concurrent tables
- Session persistence (optional account system)
- Better logging and error tracking

*Community:*
- Clear specification document for alternative client builders
- SDK or library for cryptographic proof verification
- Community contributions to client implementations

**Phase 3 (Expansion - Beyond 6 months):**

*Game Variants:*
- Cash game support (variable buy-in, variable stakes)
- Tournament structures (if demand exists)

*Ecosystem:*
- Multiple independently-developed clients
- Integration with poker training platforms
- Academic research partnerships

*Advanced Features:*
- Player statistics and hand review tools
- Replay and analysis capabilities
- Multi-language client support

### Risk Mitigation Strategy

**Technical Risk: ZKP Performance**

*Risk:* Cryptographic proofs too slow, making gameplay unplayable
*Mitigation:* 
- Prioritize performance optimization in Phase 1
- Use established mental poker algorithms (proven efficient)
- Build WebAssembly client for fast proof verification
*Validation:*
- Beta test with actual poker players during MVP
- Measure action-to-confirmation latency
- Acceptance threshold: <2 second game rhythm acceptable
*Fallback:*
- Post-game proof generation instead of real-time if latency unacceptable
- Alternative mental poker algorithm if current choice too slow

**Technical Risk: Cryptographic Implementation Flaw**

*Risk:* Implementation error undermines fairness guarantee
*Mitigation:*
- Use peer-reviewed algorithms (no novel crypto)
- Open-source code from day one for community review
- Formal code review by cryptography expert before launch
*Validation:*
- Security audit by recognized cryptography firm
- Researchers publish formal validation reports
*Fallback:*
- Maintain vulnerability disclosure process
- Community can audit and publish findings

**Market Risk: Unclear Demand**

*Risk:* Players don't care about mathematical fairness
*Mitigation:*
- Target early adopters (cryptography enthusiasts, skeptical poker players)
- Start with small community before scaling
- Measure engagement: games played, repeat players, player feedback
*Validation:*
- Track player retention and satisfaction
- Gather qualitative feedback from auditors and validators
- Monitor adoption in cryptography and poker communities
*Fallback:*
- Pivot to licensing algorithm to existing platforms
- Focus on academic/research use cases

**Resource Risk: Team Availability**

*Risk:* Key team members unavailable, project delayed
*Mitigation:*
- Document all cryptographic decisions clearly
- Keep codebase clean and well-commented
- Build modular architecture (can parallelize work)
*Validation:*
- Regular milestone reviews and progress tracking
*Fallback:*
- Can scope reduce to async-only gameplay (eliminate real-time latency requirement)
- Extend timeline rather than cut quality

### Development Milestones

**MVP Delivery Timeline:**

- **Week 1-2:** Mental poker algorithm implementation & testing
- **Week 3-4:** ZKP proof system (shuffle verification)
- **Week 5-7:** Server API endpoints & game logic
- **Week 8-9:** WebAssembly client development
- **Week 10-11:** Integration & performance optimization
- **Week 12:** Security review & beta testing

**Go-Live Criteria:**
- ✅ Mental poker algorithm verified correct
- ✅ ZKP proofs generate and verify reliably
- ✅ End-to-end game playable with acceptable latency
- ✅ Hand histories downloadable with verifiable proofs
- ✅ Code reviewed by cryptography expert
- ✅ Beta tested by target users (cryptography enthusiasts, poker players)
- ✅ Documentation complete for auditors and alternative client builders

## Functional Requirements

### Game Session Management

- FR1: Players can create a new table and receive a unique table_id
- FR2: Players can view a list of available tables with seat availability
- FR3: Players can join an available table using any player name
- FR4: Players receive a unique session_token upon joining a table
- FR5: Players can view current table status (active players, stacks, game state)
- FR6: Players can leave a table at any time
- FR7: Existing players are notified when a new player joins their table
- FR8: Existing players are notified when a player leaves their table
- FR9: Tables automatically close when all players leave

### Game Play & State Management

- FR10: Players can view their own hole cards at the start of each hand
- FR11: Players cannot view opponent hole cards until showdown
- FR12: Players can view community cards during each betting round
- FR13: Players can view current pot size and their stack size at all times
- FR14: Players can view whose turn it is to act
- FR15: Players can perform valid actions (fold, check, call, bet, raise) based on game state
- FR16: The system prevents invalid actions (e.g., folding when it's not their turn, bet amounts exceeding their stack)
- FR17: The system processes all player actions in the correct order
- FR18: The system automatically moves through betting rounds (pre-flop, flop, turn, river)
- FR19: The system correctly determines which hand wins at showdown
- FR20: Players cannot see opponent cards until showdown or hand conclusion

### Cryptographic Fairness

- FR21: The system generates a cryptographically-verified fair shuffle using mental poker algorithm
- FR22: The system generates zero-knowledge proofs for shuffle verification
- FR23: The system maintains cryptographic proof that cards are private until showdown
- FR24: The system ensures opponent cannot collude with server to cheat (heads-up only constraint)
- FR25: ZKP proofs are generated in real-time during gameplay (within playable latency)

### Hand History & Verification

- FR26: Players can download complete hand history for any game they participated in
- FR27: Hand history includes all actions taken during the game
- FR28: Hand history includes final hand outcomes and card reveals
- FR29: Hand history includes embedded cryptographic proofs in format matching mental poker literature
- FR30: Hand history is downloadable in JSON format for external analysis
- FR31: Hand histories are persistent (retrievable days/weeks/months after play)
- FR32: Hand history proofs can be independently verified by external tools

### Authentication & Player Identification

- FR33: Players join games using only a player name (no account required)
- FR34: Each player session is identified by a unique session_token
- FR35: Session tokens are valid only for the duration of the table
- FR36: No player data persists after a player leaves or session ends
- FR37: Players are not tracked across multiple sessions

### Server & API

- FR38: Server exposes /table POST endpoint to create new tables
- FR39: Server exposes /table/{table_id} GET endpoint to retrieve table status
- FR40: Server exposes /table/{table_id}/join POST endpoint for player joining
- FR41: Server exposes /table/{table_id}/leave POST endpoint for player leaving
- FR42: Server exposes /table/{table_id}/game GET endpoint to retrieve game state
- FR43: Server exposes /table/{table_id}/game/action POST endpoint to submit player actions
- FR44: Server exposes /table/{table_id}/game/showdown POST endpoint to reveal cards
- FR45: Server exposes /table/{table_id}/history GET endpoint to retrieve hand history
- FR46: Server exposes /health GET endpoint for status checking
- FR47: All API responses are in JSON format
- FR48: API returns appropriate error codes for invalid requests

### Client Experience

- FR49: Browser-based client displays game state in real-time
- FR50: Client displays hole cards clearly and safely (opponent cannot see)
- FR51: Client displays community cards and betting round information
- FR52: Client provides buttons/interface for player actions
- FR53: Client displays current pot and player stacks
- FR54: Client displays whose turn it is to act
- FR55: Client can download and save hand history
- FR56: Client can display or reference cryptographic proofs from hand history
- FR57: Client is built with WebAssembly for responsive user experience
- FR58: Client works in all major web browsers

### Auditability & Code Access

- FR59: All cryptographic implementation is open-source and publicly available
- FR60: Cryptographic algorithms are sourced from peer-reviewed academic papers
- FR61: Source code is clearly documented and auditable
- FR62: Hand history format is documented for external verification
- FR63: Mental poker algorithm specification is published for auditors
- FR64: Reference client implementation is available as open-source

### Deployment & Operations

- FR65: Server can be deployed on standard web server infrastructure
- FR66: Server can be deployed from open-source repository
- FR67: Server deployment does not require complex configuration or dependencies
- FR68: Server generates logs of all game activity
- FR69: Server logs contain sufficient detail for monitoring and troubleshooting
- FR70: Server can be restarted without losing hand history data

### Error Handling & Reliability

- FR71: System gracefully handles player disconnection mid-game
- FR72: System returns appropriate error messages for invalid table access
- FR73: System returns appropriate error messages for invalid game actions
- FR74: System ensures game state consistency even after errors
- FR75: System prevents double-betting or action duplication from network retries

## Non-Functional Requirements

### Performance

**ZKP Proof Generation:**
- Shuffle verification proofs must generate within 2 seconds per hand
- Target: <1 second for optimal user experience
- Acceptable: <2 seconds (maintains poker game rhythm)
- Fallback: Post-game proof generation if real-time latency unacceptable

**Player Action Response:**
- Player actions must be acknowledged by server within 500ms
- Game state updates must be visible to players within 1 second
- Acceptable latency includes network round-trip and server processing

**Concurrent Game Support:**
- MVP must support minimum 5 concurrent heads-up games
- Target: Scale to 10+ concurrent games with single-server deployment
- Growth phase: Horizontal scaling as needed

**Client Responsiveness:**
- WebAssembly client must render game state updates within 200ms of receiving data
- Proof verification display must not block player interaction

### Security

**Cryptographic Algorithm Integrity:**
- Mental poker algorithm must be sourced from peer-reviewed academic papers
- No novel cryptography (proven algorithms reduce security risk)
- Algorithm selection and rationale must be documented

**Code Auditability:**
- All cryptographic code must be open-source from day one
- Code must be clearly documented and understandable to cryptography experts
- No obfuscation or intentionally obscure implementations

**Cryptographic Proof Verification:**
- ZKP proofs must be independently verifiable by external tools
- Proof format must match published mental poker literature standards
- Proof verification must not require trust in server implementation

**Security Review:**
- Code must undergo formal security review by recognized cryptography expert before production deployment
- All identified security issues must be resolved before launch
- Security audit report should be published

**Implementation Correctness:**
- Mental poker shuffle must be mathematically proven fair (not just claimed)
- Card privacy must be cryptographically guaranteed (not through access control)
- Opponent collusion must be mathematically impossible (enforced by heads-up constraint)

### Reliability

**Hand History Persistence:**
- Hand histories must persist indefinitely (or for minimum 1 year)
- Hand history data must survive server restarts
- Lost hand histories represent data loss failure

**Game State Consistency:**
- Game state must remain consistent even in case of errors
- Player balances and pot calculations must always be correct
- No possibility of double-betting or action duplication from network retries

**Error Handling:**
- System must gracefully handle player disconnections mid-game
- Cryptographic proof generation failures must be reported to players
- API errors must return appropriate error codes and messages

**Data Recovery:**
- In-progress game state should be recoverable after unexpected shutdown (best effort)
- Hand histories already published cannot be lost or modified

**Deployment Reliability:**
- Server must be deployable on standard web server infrastructure
- Deployment must not require complex configuration or external dependencies
- Server can be restarted without data loss

### Availability

**MVP Availability Target:**
- Best effort for MVP (no strict uptime requirement)
- Scheduled maintenance windows acceptable
- Players should be notified of planned downtime

**Future Growth Target (Phase 2+):**
- Target 99% uptime for production deployment
- Automatic failover mechanisms if deployed at scale

