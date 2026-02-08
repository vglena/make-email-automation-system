# ⚙️ Technical Decisions and Learnings

## Use of Routers

A Router is used to separate processing paths based on email classification, which allows:

- Clear separation of logic
- Easier maintenance
- Future scalability with new categories

---

## Use of Aggregators

Although attachments are processed individually, an Aggregator is used to:

- Rebuild a unified view at the email level
- Prepare data for external systems like Airtable
- Separate internal Make logic from the end-user experience

---

## End-User-Oriented Design

A key design decision is that the end user **never interacts with Make**.  
As a result:

- Airtable receives only readable, meaningful data
- Complex arrays and internal structures are hidden
- Clarity and usability are prioritized over raw technical detail

---

## Considered Alternatives

- Explicit use of an Iterator: rejected as redundant
- One Airtable record per attachment: rejected due to poor user experience
- Single-path automation without Router: rejected due to low scalability

---

## Possible Future Improvements

- Semantic classification using AI modules
- Automatic response generation
- Metrics dashboard in Airtable
- Integration with additional publishing or reporting systems

---

## Key Learnings

- Deep understanding of bundle-based execution in Make
- Correct and justified use of Aggregators
- Designing automations with a user-first mindset

