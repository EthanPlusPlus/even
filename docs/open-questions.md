# Open Questions

- **OCR / receipt parsing engine** — VisionKit + Vision (free, on-device, Apple-native) is the obvious default, but line-item extraction quality is unproven for our use case. Paid alternatives (Veryfi, AWS Textract, Google Document AI) parse line items more reliably out-of-the-box. Decide after testing Vision on real receipts.

- **Person merge-conflict UX.** Decision `002-diner-durability` dedupes typed names by normalised match. Open: how does the user resolve "Sarah" and "Sarah K" being the same human (or, conversely, two different Sarahs)? Punted until allocation UX exists to inform the answer.

- **Auto-service-charge detection.** Some restaurants auto-add a 10–20% service charge as a line item. For MVP the user manually allocates it to "everyone" (Decision `004`). Open: when does detection become a real need, and what does it look like — keyword match on the OCR output vs. structured field from a cloud parser?

