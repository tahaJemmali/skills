# Worked example: "One umbrella for partners"

Source: a design discussion plus a five-sweep code audit about how a chat platform lets
outside partners send WhatsApp templates and hear back what the customer did. Audience: a junior
joining the meeting. Metaphor: a patch panel (boxes are sockets, arrows are cables that plug,
unplug and straighten into one hub). Nine beats, ninety seconds, dark ground, teal for the good
path, amber for broken, a mono face for identifiers.

Named things (seven): Partner, the platform, Customer, the relay, the event bus, "inbound actions",
"subscription row". Everything else appears once as a tag or not at all.

| # | Beat (s) | On screen | Words that appear |
|---|----------|-----------|-------------------|
| 1 | A partner knocks (8) | Three sockets rise: New partner, Platform, Customer. Cables draw: send → template → tap. A dashed amber cable back: the missing part. | "One umbrella for partners" · "send this template" · "tap" · "and the tap back, with my ids?" |
| 2 | Three loops today (12) | Three rows, one per existing partner. Each row: partner → platform → customer, with a tag under the platform saying what it remembers, and a return cable. The third row's return is amber and dashed. | "remembers an order, by phone" · "remembers a request, by phone" · "remembers nothing" · "Same job. Three wirings." |
| 3 | First idea (9) | One loop again. A glowing "subscription row" pops under the platform. A dot (the id) rides the cable into the customer's buttons and comes back. | "Add one row at send time" · "a tiny id in each button" · "Neat. One row. Done?" · "We looked deeper before building it." |
| 4 | We looked deeper (8) | A light band sweeps left to right; seventeen small boxes pop up as it passes; a counter climbs to 17. | the seventeen names, one each · "Seventeen ways to say: something happened, now react." |
| 5 | Three exits (10) | One "chat fact" socket on the left, the relay on the right, three different middle boxes draw one after another. | "the event bus" · "a direct queue add" · "walker-side ports" · "same moment, two names" |
| 6 | Three doors in (9) | Mirror of beat 5: partner on the left, "WhatsApp send" on the right, three entrances. | "relay inbound action" · "event-dispatcher registry" · "public endpoint + trigger flag" |
| 7 | Dead and doubled (8) | Three vignettes: a node with two cables out; three list rows whose cable ends in an ×; two labels wired to an empty dashed box. | "HTTP call + relay event: twice" · "never fires" · "labels only, no branch" |
| 8 | One umbrella (16) | Nine tangled thin cables draw, then fade. Five partners, one "door in", one "spine" box that fills with seven facts, one "door out", the customer. Cables straighten through them. | "move one: raise every fact once" · "move two: partners ask one way" · "move three: partners hear one way" |
| 9 | Why this one (10) | Three cards rise, then an ordered strip (new partner first → property app → order system last), then everything shrinks and the end card lands with a growing dot. | "Built on parts we already have" · "Nothing changes for partners" · "One umbrella. Three moves. Order still to agree." |

What the story skipped on purpose (said in the reply, not on screen): the security holes found in
the same audit (their own ticket), the exact row shape of the subscription, the fallback order for
reactions without an id, and every partner that is a domain client rather than a chat signal.

Three doors given in the reply: the issue that holds the proposal and its three open decisions;
the file where the tap handler already runs actions without a model; the relay's vendor spec that
delivers events with retries.

## Why these choices

- Beat 3 exists although the source never said "first idea": the viewer will think "just store a
  row" too, and seeing it drawn, then questioned, is what makes beats 5–7 feel earned.
- Beat 4 shows a number (17) instead of a list. The list exists for one second as boxes; nobody
  reads it, everybody feels it.
- Beats 5, 6 and 7 are the same layout three times. Repetition is a feature: the viewer learns the
  grammar on beat 5 and reads beats 6 and 7 instantly.
- Beat 8 starts with the mess and straightens it. "Transform, don't cut": the viewer watches the
  tangle become the answer instead of being shown a clean diagram out of nowhere.
- The end card states the takeaway and names what is still open ("Order still to agree"). An
  earlier cut ended on "Questions, ideas, holes?" and read as a slide asking for applause; the
  people in the room ask anyway, and a card that begs for it only closes the film weaker.
- In hindsight beat 9 does too much: three cards, an order strip and the end card in ten seconds.
  The template now splits it into a "why" beat and a "door" beat. When you copy this example,
  copy the split, not the stack.
