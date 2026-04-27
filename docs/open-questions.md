# Open Questions

- **OCR / receipt parsing engine** — VisionKit + Vision (free, on-device, Apple-native) is the obvious default, but line-item extraction quality is unproven for our use case. Paid alternatives (Veryfi, AWS Textract, Google Document AI) parse line items more reliably out-of-the-box. Decide after testing Vision on real receipts.

- **Diners — durable or ephemeral?** Ephemeral = type names per bill, no friend list, no contact-permissions, simpler. Durable = a `Person` entity persists across bills, enabling history-by-person ("Sarah owes you R47 across 3 receipts") at the cost of a friends-list UI.

- **Splitting granularity.** Whole items only (each line item belongs to one diner or "shared by all") vs. fractional via shares (a line item can be divided — e.g. 3 shares of nachos, you own 2; ½ pizza you, ½ pizza Sarah). Shares cleanly handle the realistic "we shared this" case.

- **Tax / tip / service charge distribution.** Proportional to each diner's subtotal share, equal across heads, or configurable per bill. Real receipts mix all three behaviours.

- **Currency support.** Single currency (ZAR) is simpler but locks us in. Per-bill currency field is nearly free to add now and avoids a migration later. No FX conversion either way.
