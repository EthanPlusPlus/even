# Open Questions

- **OCR / receipt parsing engine** — VisionKit + Vision (free, on-device, Apple-native) is the obvious default, but line-item extraction quality is unproven for our use case. Paid alternatives (Veryfi, AWS Textract, Google Document AI) parse line items more reliably out-of-the-box. Decide after testing Vision on real receipts.
