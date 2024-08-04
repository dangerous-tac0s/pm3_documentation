---
NTAG Implant Options
---

```mermaid
  flowchart TD;
      A[Form Factor]--> B[X-Series] & C[Flex];
      B --> B1[NTAG Only] & B2[NTAG + Blink] & B3[NTAG + t5577];
      B1 --> B1.1{xNT};
      click B1.1 "https://dngr.us/xnt" _self
      B1.1 -- type --> B1.1a[216];
      B2 --> B2.1{xSIID};
      click B2.1 "https://dngr.us/xsiid" _self
      B2.1 -- type --> B2.1a[I2C];
      B3 --> B3.1{NExT};
      click B3.1 "https://dngr.us/next" _self
      B3.1 -- type --> B3.1a[216];

      C -- format --> C1[Wide] & C2[Narrow];
      C1 --> C1.1[NTAG Only];
      C1.1 --> C1.1a{flexNT};
      click C1.1a "https://dngr.us/flexnt" _self
      C1.1a -- type --> C1.1a_1[216];
      C2 --> C2.1[Magic*];
      C2.1 --> C2.1a{flexUG4};
      click C2.1a "https://dngr.us/flexug4" _self
      C2.1a -- type --> C2.1a_1[gen4];

      subgraph " "
      C2.1a_1 .-> UG4a[NTAG2XX] & UG4b[MIFARE Classic 1k/4k] & UG4c[MIFARE Mini] & UG4d[MIFARE Ultralight]
      end
```

\* So called "magic" chips can change their UIDs. Some, like in this case, can also emulate other chips such as the NTAG varieties.

### Further Reading
- [Flex Formats](FLEX_FORMATS.md)
- [NTAG Information](NTAG.md)

### Product Links
- [xNT](https://dngr.us/xnt)
- [xSIID](https://dngr.us/xsiid)
- [flexNT](https://dngr.us/flexnt)
- [flexUG4](https://dngr.us/flexug4)
  
---
### [Back to High Frequency Chips](HIGH_FREQUENCY_CHIPS.md)
