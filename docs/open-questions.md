# Open Questions

- **OCR / receipt parsing engine** — VisionKit + Vision (free, on-device, Apple-native) is the obvious default, but line-item extraction quality is unproven for our use case. Paid alternatives (Veryfi, AWS Textract, Google Document AI) parse line items more reliably out-of-the-box. Decide after testing Vision on real receipts.

- **Person merge-conflict UX.** Decision `002-diner-durability` dedupes typed names by normalised match. Open: how does the user resolve "Sarah" and "Sarah K" being the same human (or, conversely, two different Sarahs)? Punted until allocation UX exists to inform the answer.

- **Tax / tip / service charge distribution.** Proportional to each diner's subtotal share, equal across heads, or configurable per bill. Real receipts mix all three behaviours.

- **Currency support.** Single currency (ZAR) is simpler but locks us in. Per-bill currency field is nearly free to add now and avoids a migration later. No FX conversion either way.
