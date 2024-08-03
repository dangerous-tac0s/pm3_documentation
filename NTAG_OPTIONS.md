---
NTAG Implant Options
---

```mermaid
  flowchart TD;
      A[Form Factor]--> B[X-Series] & C[Flex];
      B --> B1[NTAG Only] & B2[NTAG + Blink] & B3[NTAG + t5577];
      B1 --> B1.1[xNT];
      B1.1 -- type --> B1.1a[216];
      B2 --> B2.1[xSIID];
      B2.1 -- type --> B2.1a[I2C];
      B3 --> B3.1[NExT];
      B3.1 -- type --> B3.1a[216];

      C -- format --> C1[Wide];
      C1 --> C1a[flexNT];
      C1a -- type --> C1a_1[216];
```

### Further Reading
- [Flex Formats](FLEX_FORMATS.md)
- [NTAG Inforation](NTAG_INFORMATION.md)

### Product Links
- [xNT](https://dngr.us/xnt)
- [xSIID](https://dngr.us/xsiid)
- [flexNT](https://dngr.us/flexnt)
  
---
### [Back to High Frequency Chips](HIGH_FREQUENCY_CHIPS.md)
